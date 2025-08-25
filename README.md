## Tasks

1. Load the dataset into a Pandas DataFrame and display the first few rows to get an overview of the data.
2. Perform data cleaning by handling missing values, if any, and removing any redundant or unnecessary columns.
3. Explore the basic statistics of the dataset, including measures of central tendency and dispersion.
4. Perform data visualization to gain insights into the dataset. Generate appropriate plots, such as histograms, scatter plots, or bar plots, to visualize different aspects of the data.
5. Analyze the sales trends over time. Identify the busiest months and days of the week in terms of sales.
6. Explore the top-selling products and countries based on the quantity sold.
7. Identify any outliers or anomalies in the dataset and discuss their potential impact on the analysis.
8. Draw conclusions and summarize your findings from the exploratory data analysis.


## EDA Summary: Conclusions and summarize of my findings

### Dataset overview
- Original dataset: 541,909 rows, 8 columns (InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country).
- Working (cleaned) dataset: 333,201 rows, 7 columns (InvoiceNo, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country).

### Cleaning steps performed
- Dropped rows with missing values (removed many rows with missing CustomerID).
- Removed an accidental row (if present) and converted CustomerID to object as data-type.
- Dropped `StockCode` column and can be renamed `Quantity` → `QTY`, `UnitPrice` → `UPrice` (but were not necessary- code added as alternative)
- Removed duplicate rows (5,261 duplicates found and dropped).
- Removed negative-quantity rows (returns/cancellations): 8,871 rows identified and dropped.
- Removed rows with UPrice ≤ 0 (40 entries with zero/negative price removed).
- Outliers removed using IQR filtering on `UnitPrice` and `Quant`:
    - Q1: UPrice=1.25, QTY=2.0
    - Q3: UPrice=3.75, QTY=12.0
    - IQR: UPrice=2.5, QTY=10.0

### Key numeric relationships & stats
- Top product by total quantity: "PACK OF 72 RETROSPOT CAKE CASES" (14,986 units).
- Top 10 products include popular retrospot items, cake cases, bags and tea/cake related products.
- Top country by volume: United Kingdom (2,155,791 units) — dominant market by a large margin; next are Germany (approx 83,869) and France (approx 75,353).

### Notable anomalies / data quality issues
- Many zero-price entries
- Removing returns (negative QTY) simplifies sales view but loses return behavior insight; need to consider analyzing returns separately if necessary.
- Dropping rows with missing CustomerID may bias customer-level analyses toward known customers. However, no consideration here. Can be checkd separately for customer base analysis

### Visualizations used
- Boxplots for QTY and UPrice (before & after outlier removal).
- Bar charts for top products and top countries.
