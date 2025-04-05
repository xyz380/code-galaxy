# Building Resilient Infrastructure, Promoting Inclusive and Sustainable Industrialization, and Fostering Innovation  
*A Decision Intelligence Analysis of UN Sustainable Development Goal 9 (SDG 9)*  

By: Siddharth Koyada

  
  ## Table of Contents
1. [Introduction](#introduction)
2. [Research Objective](#research-objective)
3. [Milestone 2: Exploratory Data Analysis](#milestone-2-exploratory-data-analysis)
   - [3.1 Total Energy Consumption by Industry](#31-total-energy-consumption-by-industry)
   - [3.2 Employee Earnings Growth Across Industries](#32-employee-earnings-growth-across-industries)
   - [3.3 Capital Expenditure on Infrastructure and Transportation Infrastructure](#33-capital-expenditure-on-infrastructure-and-transportation-infrastructure)
   - [3.4 Greenhouse Gas Emission by Province](#34-greenhouse-gas-emission-by-province)
   - [3.5 Plastic Usage by Province and Industry Over Time](#35-plastic-usage-by-province-and-industry-over-time)
4. [Milestone 3: Correlation & Causal Inference Analysis](#milestone-3-correlation--causal-inference-analysis)
   - [4.1 Correlation Matrix and Heatmap](#41-correlation-matrix-and-heatmap)
   - [4.2 Causal Inference with DoWhy](#42-causal-inference-with-dowhy)
   - [4.3 Comparison of Milestone 2 and Milestone 3](#43-comparison-of-milestone-2-and-milestone-3)
5. [Discussion](#discussion)
6. [References](#references)

## Introduction 

Infrastructure is the backbone of economic growth, social development, and technological progress. However, many regions still lack reliable infrastructure, leading to inefficiencies in transportation, energy, and industrial development. Sustainable industrialization and innovation are critical for economic resilience, environmental sustainability, and reducing inequalities.  

This project aims to analyze global infrastructure development, industrialization trends, and innovation metrics. Using open datasets, it explores the relationship between infrastructure investments, economic growth, and sustainable industrial policies. The goal is to identify key factors that drive resilient and inclusive industrialization while fostering technological advancements.  

For a deeper understanding of the problem, datasets, and methodology, refer to the [Background.md](Background.md) file.

## Research Objective
This project aims to analyze global infrastructure development, industrialization trends, and innovation metrics. Using open datasets, it explores the relationship between infrastructure investments, economic growth, and sustainable industrial policies. The goal is to identify key factors that drive resilient and inclusive industrialization while fostering technological advancements.
## Milestone 2: Exploratory Data Analysis

In Milestone 2, we focused on **data cleansing** (using Tableau Prep) and **data visualization** (using Tableau). We identified five key performance indicators (KPIs) to explore how infrastructure, industrialization, and innovation interrelate.

## Key Performance Indicators (KPIs)

1. ### Total Energy Consumption by Industry

This KPI highlights the industries with the highest energy consumption (in GJ), helping identify key sectors for energy optimization. It provides insights into which industries should be prioritized for energy efficiency initiatives.

![Energy Consumption Visualization](https://github.com/xyz380/code-galaxy/blob/main/images/Energy%20consumption.png?raw=true)


#### Insights:
- Based on the visualization, the **top 3 industries with the highest energy consumption** are:
  - **Manufacturing**
  - **Paper Manufacturing**
  - **Primary Metal Manufacturing**
- These industries should be prioritized for energy efficiency improvements.
- **Manufacturing** stands out as a significant energy consumer, and improvements here could lead to substantial energy savings.
- **Paper Manufacturing** and **Primary Metal Manufacturing** also contribute heavily to energy consumption, suggesting that optimization measures in these sectors would yield environmental and cost benefits.
  
2. ### Employee Earnings Growth Across Industries

This KPI visualizes the growth of employee earnings across different industries from 2001 to 2023. It highlights industries that have shown consistent increases in earnings over time.

![Employee Earnings Growth Across Industries]( https://github.com/xyz380/code-galaxy/blob/main/images/Earnings%20in%20different%20industries%20over%20the%20time.png?raw=true)

#### Insights:
- **Highway street bridge construction**, **mining and quarrying**, and **gas extraction and utility system construction** have experienced the highest growth in employee earnings over the years.
- This increase suggests rising demand or higher compensation levels in these industries.
- Monitoring these trends is crucial for assessing the labor market's health and identifying sectors with rising job opportunities.

3. ### Capital Expenditure on Infrastructure and Transportation Infrastructure

This KPI tracks the capital expenditure on infrastructure and transportation infrastructure from 2013 to 2023. It highlights the top-growing sectors in terms of investment.

![Capital Expenditure on Infrastructure and Transportation Infrastructure]( https://github.com/xyz380/code-galaxy/blob/main/images/Capital%20Expenditure%20on%20%20Different%20Infrastructure.png?raw=true)

#### Insights:
- **Infrastructure** and **transportation infrastructure** are the top two sectors with the highest capital expenditure over the years.
- Capital expenditure on these sectors has increased year over year, indicating a focus on strengthening transportation and essential infrastructure.
- Tracking this growth helps guide strategic investment decisions and ensures that resources are directed toward key areas for long-term development.

4. ### Greenhouse Gas Emission by Province

This KPI visualizes the greenhouse gas emissions across Canadian provinces using a geographic map. It identifies which provinces have the highest emissions, supporting targeted efforts to reduce environmental impact.

![Greenhouse Gas Emission by Province](https://github.com/xyz380/code-galaxy/blob/main/images/High-Emission%20Provinces%20.png?raw=true)

#### Insights:
- **Ontario** and **Alberta** have the highest greenhouse gas emissions in Canada, as shown by the darker colors on the map.
- These provinces contribute significantly to Canada's overall emissions, and efforts to reduce emissions here could have a major impact.
- Monitoring emissions by province is crucial for tracking Canada's progress in meeting environmental sustainability goals.

5. ### Plastic Usage by Province and Industry Over Time

This KPI highlights the trend of plastic usage across Canadian provinces and industries from 2012 to 2021. It shows where plastic consumption is increasing, focusing on the most significant provinces and industries.

![Plastic Usage by Province and Industry Over Time]( https://github.com/xyz380/code-galaxy/blob/main/images/Dashboard%201%20province%20with%20high%20plastic%20usage.png?raw=true)

#### Insights:
- **Ontario** and **Quebec** have the highest plastic usage among Canadian provinces and have shown an increasing trend over the years.
- Plastic usage in these provinces has grown from 2012 to 2021.
- The **Packaging** and **Vehicle** industries are the top consumers of plastic and have seen significant increases in usage over the years.
- The rising trend in plastic usage in these provinces and industries suggests that targeted efforts for reduction are crucial.
  
## Milestone 3: Correlation & Causal Inference Analysis

To build on the insights from Tableau, we introduced more advanced statistical methods in Milestone 3.
### 4.1 Correlation Matrix and Heatmap
Using Pearson’s correlation coefficients for our five KPIs:
- **Strong positive cluster**: Earnings_Value, CapitalExpenditure, GHG_Value, and Plastic_Value (0.84–0.97).
- **Negative correlation**: Energy_Value with the other four KPIs (around -0.88 to -0.91).

> **Key Takeaway**: When Earnings, Capital Expenditure, GHG, and Plastic Usage rise, Energy Consumption tends to decrease, or vice versa. However, correlation alone doesn’t imply causation.

### 4.2 Causal Inference with DoWhy
We treated **CapitalExpenditure** as the treatment and **Energy_Value** as the outcome, with Earnings_Value, GHG_Value, and Plastic_Value as confounders.

- **Identified Estimand**: A backdoor path requiring us to condition on the confounders.
- **Estimation Method**: Simple linear regression (`method_name="backdoor.linear_regression"`).
- **Result**: Suggests a **negative causal relationship** between CapitalExpenditure and Energy_Value, meaning higher capital spending might coincide with lower energy consumption, assuming our confounders capture the main sources of bias.

> **Caveat**: This result is subject to data limitations and the assumption that no unobserved confounders exist. A placebo treatment refutation was also performed to check for spurious results.

### 4.3 Comparison of Milestone 2 and Milestone 3
- **Milestone 2 (Tableau)**:
  - Strengths: Easy data cleansing (Tableau Prep), intuitive data visualization, quick identification of patterns.
  - Limitations: Tableau does not natively support advanced statistical modeling or causal inference methods.
- **Milestone 3 (Advanced Analysis)**:
  - Strengths: Python libraries like DoWhy allow for correlation matrices and causal inference, giving deeper insights into *why* relationships may exist, not just *how* they correlate.
  - Limitations: Requires careful handling of missing data, understanding of causal assumptions, and more advanced coding skills.

By comparing these two milestones, it’s clear that **Tableau** excels at fast, interactive dashboards and basic trend analysis, whereas **Python-based** tools (e.g., DoWhy) enable **more rigorous statistical and causal analysis**. Together, they provide a comprehensive understanding of the data and underlying relationships.

---

## Discussion
Based on the insights from Milestone 2 (Tableau-based EDA) and Milestone 3 (Causal Analysis):
- Infrastructure and transportation investments are growing, potentially reducing energy consumption while fostering industrial growth.
- Certain industries (e.g., manufacturing, paper, and primary metal) remain major energy consumers and could benefit most from targeted efficiency measures.
- Provinces like Ontario and Alberta (for GHG emissions) and Ontario and Quebec (for plastic usage) are prime targets for environmental policies.

Moving forward, additional data—such as sector-level breakdowns, technology adoption rates, or policy interventions—could refine our causal analysis and strengthen the validity of these findings.

---

## References
- [Background.md] – Provides detailed information about the project scope, datasets, and methodologies.
- [DoWhy Documentation](https://github.com/py-why/dowhy) – Used for causal inference.
- Additional references as needed (e.g., data sources, relevant literature, official reports).
