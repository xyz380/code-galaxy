Handling Missing Values

Identified missing values in the dataset.

Applied imputation techniques such as mean/median for numerical values and mode for categorical values.

Removed rows with excessive missing values (>50%) to maintain data quality.

Removed years with empty data.

Removing Duplicates

Checked for duplicate rows and removed exact duplicates.

Used domain knowledge to identify and remove near-duplicate records.

Standardizing Formats

Converted date columns to a uniform YYYY-MM-DD format.

Standardized categorical values by ensuring consistent naming conventions (e.g., "Male" vs. "M").

Normalized numerical values where necessary (e.g., converting currency to a common unit).

Renamed column headers for consistency and clarity.

Filtering Unnecessary Columns or Rows

Dropped columns with low variance or irrelevant information.

Filtered out rows that did not meet specific criteria (e.g., removing outliers based on business logic).

Removed unnecessary columns.

Joining Multiple Datasets

Merged datasets using common keys (e.g., INNER JOIN for relevant records, LEFT JOIN for retaining important data).

Ensured consistency in key formats before merging.

Aggregations

Summarized data using GROUP BY operations (e.g., total sales per region, average customer rating per category).

Computed new metrics such as moving averages or cumulative sums.

Pivoting

Transformed data using pivot tables to reshape the dataset for analysis.

Converted long format data into wide format for easier readability and interpretation.

Pivoted years in different columns into a single row and named the new column Year.

Pivoted different KPI variables in one row into separate rows.

Organizing Tableau Fields

Arranged Tableau fields in order to improve usability and visualization efficiency.
