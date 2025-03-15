# Building Resilient Infrastructure, Promoting Inclusive and Sustainable Industrialization, and Fostering Innovation  
*A Decision Intelligence Analysis of UN Sustainable Development Goal 9 (SDG 9)*  

By: Siddharth Koyada

## Executive Summary  

Infrastructure is the backbone of economic growth, social development, and technological progress. However, many regions still lack reliable infrastructure, leading to inefficiencies in transportation, energy, and industrial development. Sustainable industrialization and innovation are critical for economic resilience, environmental sustainability, and reducing inequalities.  

This project aims to analyze global infrastructure development, industrialization trends, and innovation metrics. Using open datasets, it explores the relationship between infrastructure investments, economic growth, and sustainable industrial policies. The goal is to identify key factors that drive resilient and inclusive industrialization while fostering technological advancements.  

For a deeper understanding of the problem, datasets, and methodology, refer to the [Background.md](Background.md) file.  

## Key Performance Indicators (KPIs)

### Total Energy Consumption by Industry

This KPI highlights the industries with the highest energy consumption (in GJ), helping identify key sectors for energy optimization. It provides insights into which industries should be prioritized for energy efficiency initiatives.

![Energy Consumption by Industry](./visualizations/energy_consumption_by_industry.png)

#### Insights:
- Based on the visualization, the **top 3 industries with the highest energy consumption** are:
  - **Manufacturing**
  - **Paper Manufacturing**
  - **Primary Metal Manufacturing**
- These industries should be prioritized for energy efficiency improvements.
- **Manufacturing** stands out as a significant energy consumer, and improvements here could lead to substantial energy savings.
- **Paper Manufacturing** and **Primary Metal Manufacturing** also contribute heavily to energy consumption, suggesting that optimization measures in these sectors would yield environmental and cost benefits.



The success of resilient infrastructure, sustainable industrialization, and innovation can be measured using the following KPIs:

import pandas as pd

# Load your energy consumption dataset (replace with your file path)
data = pd.read_csv('industrial_energy_consumption.csv')

# Display the first few rows of the dataset to check the structure
print(data.head())

# Clean and preprocess data (if necessary)
# For example, removing any NaN values or handling missing data
data = data.dropna()

# 1. Total energy consumption by industry
total_energy_consumption = data.groupby('Industry')['Energy_Consumption_GJ'].sum().reset_index()

# 2. Top 5 energy-consuming industries
top_5_industries = total_energy_consumption.nlargest(5, 'Energy_Consumption_GJ')

# 3. Energy consumption growth rate (YoY)
# Assuming the data has columns 'Year' and 'Energy_Consumption_GJ'
data['Growth_Rate'] = data.groupby('Industry')['Energy_Consumption_GJ'].pct_change() * 100
growth_rate = data.groupby('Industry')['Growth_Rate'].mean().reset_index()

# 4. Energy intensity (GJ per $1M industrial output)
# Assuming you have a column 'Industrial_Output' in your dataset
data['Energy_Intensity'] = data['Energy_Consumption_GJ'] / (data['Industrial_Output'] / 1000000)
energy_intensity = data.groupby('Industry')['Energy_Intensity'].mean().reset_index()

# 5. Merging top 5 industries, growth rate, and energy intensity
analysis = top_5_industries.merge(growth_rate, on='Industry').merge(energy_intensity, on='Industry')

# Display the final analysis
print(analysis)

# Save the results to a CSV file for later use or upload to GitHub
analysis.to_csv('industrial_energy_analysis.csv', index=False)

# You can also plot the data if necessary using matplotlib or seaborn
import matplotlib.pyplot as plt
import seaborn as sns

# Plot the total energy consumption for top 5 industries
plt.figure(figsize=(10, 6))
sns.barplot(x='Industry', y='Energy_Consumption_GJ', data=top_5_industries)
plt.title('Top 5 Energy Consuming Industries')
plt.xlabel('Industry')
plt.ylabel('Total Energy Consumption (GJ)')
plt.xticks(rotation=45)
plt.show()

# Plot energy intensity for top 5 industries
plt.figure(figsize=(10, 6))
sns.barplot(x='Industry', y='Energy_Intensity', data=analysis)
plt.title('Energy Intensity for Top 5 Industries')
plt.xlabel('Industry')
plt.ylabel('Energy Intensity (GJ per $1M Output)')
plt.xticks(rotation=45)
plt.show()

# Optionally, you can push this code and the results to GitHub from here.


2. **Industrialization Growth Rate**  
   - *Definition:* The rate of growth in the manufacturing and industrial sector as a percentage of GDP.  
   - *Measurement:* National and global industrial production data.  

3. **Innovation Index**  
   - *Definition:* A measure of a country’s ability to innovate based on research output, patents, and technology adoption.  
   - *Measurement:* Data from the Global Innovation Index.  

4. **CO₂ Emissions per Unit of Industrial Output**  
   - *Definition:* Tracks the environmental impact of industrialization by measuring carbon emissions per unit of GDP.  
   - *Measurement:* Emissions data from international environmental organizations.  

5. **Investment in Sustainable Infrastructure Projects**  
   - *Definition:* Tracks financial commitments toward eco-friendly infrastructure and industrial projects.  
   - *Measurement:* Global and national investment reports.  

---

This repository contains the complete analysis, including data collection, visualization, and modeling using Git, Tableau, and Python/R. Explore the full study for insights into the future of sustainable industrialization and resilient infrastructure.  
