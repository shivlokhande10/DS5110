Financial Analysis of SVB, HSBC, and Morgan Stanley
This project provides an in-depth financial analysis of Silicon Valley Bank (SVB), HSBC, and Morgan Stanley. The analysis includes examining key financial metrics such as net income, provisions for credit losses, interest income, and efficiency ratios over the years. The primary goal is to understand the financial stability and risk management practices of these banks, particularly focusing on the factors contributing to the decline of SVB.

Project Structure
Data Files:

HSBC.csv: Financial data for HSBC.
Morgan.csv: Financial data for Morgan Stanley.
SVB.csv: Financial data for Silicon Valley Bank.
Scripts:

analysis_script.py: The main script that performs data cleaning, analysis, and visualization.
Installation
To run the analysis, you will need to have the following dependencies installed:

bash
Copy code
pip install pandas matplotlib sqlite3
Usage
Load the datasets: The script starts by loading the financial datasets for HSBC, Morgan Stanley, and SVB.

python
Copy code
hsbc_df = pd.read_csv('HSBC.csv')
morgan_df = pd.read_csv('Morgan.csv')
svb_df = pd.read_csv('SVB.csv')
Data Cleaning: Basic data cleaning is performed by filling missing values with the median of each column.

python
Copy code
for bank_df in [hsbc_df, morgan_df, svb_df]:
    bank_df.fillna(bank_df.median(), inplace=True)
Database Creation: The cleaned data is loaded into an in-memory SQLite database for querying and analysis.

python
Copy code
db_connection = sqlite3.connect(':memory:')
hsbc_df.to_sql('HSBC', db_connection, if_exists='replace', index=False)
morgan_df.to_sql('Morgan', db_connection, if_exists='replace', index=False)
svb_df.to_sql('SVB', db_connection, if_exists='replace', index=False)
SQL Queries: The script performs various SQL queries to analyze financial metrics over time.

python
Copy code
financial_metrics_df = pd.read_sql_query(financial_query, db_connection)
Visualization: Several plots are generated to visualize trends in net income, provisions for credit losses, efficiency ratios, and other key metrics.

python
Copy code
plot_financial_trend(financial_metrics_df, 'Net Income', 'Net Income Trends Over Years', 'Net Income')
Results
The analysis results are presented in the form of graphs that illustrate the trends in key financial metrics over time, comparing the performance of SVB, HSBC, and Morgan Stanley. These results provide insights into the financial health and risk management practices of these institutions.

Conclusion
The project highlights significant differences in the financial stability of the three banks, with SVB showing considerable volatility in its financial metrics. In contrast, Morgan Stanley demonstrates stable growth and strong risk management, while HSBC maintains a conservative approach with steady performance.
