# Weekly_Momentum_Breakout_Screener_-WMB_5-
✅ Screener Criteria (WMB-5) MACD% > 52-week average ADX > 22 BB Width % expanding vs previous week ROC > 2% Stochastic %D > 55
**nse500_sector_mapping.csv has to be the colab enviorment**
  download the file to local system
  In the Colab environment, click the "Files" icon on the left sidebar.
  Click the "Upload" button (up arrow icon) and select the desired file(s) from your local computer.
  The file will be uploaded to the Colab runtime's temporary storage.

🔍 How Does It Work?
For each stock, it checks the following 5 technical signals, all based on weekly data:

Signal	What It Checks	Why It Matters
1. MACD > 52-week average	The momentum line is rising above its long-term norm	Indicates increasing bullish momentum
2. ADX > 22	The trend strength is high	Tells us a trend is forming or getting stronger
3. Bollinger Band Width expanding	Price volatility is increasing	Breakouts often happen after periods of low volatility
4. ROC (Rate of Change) > 2%	The price has moved significantly upward	Shows recent bullish acceleration
5. Stochastic %D > 55	Price is near recent highs	Reflects buying pressure and possible continuation

A stock must meet all 5 criteria to pass. This tight filter helps avoid noise and only focus on high-quality setups.

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

This code performs a backtest on NSE 500 stocks using several technical indicators. Here's a breakdown of the steps:

Install Dependencies: Installs the necessary libraries (yfinance, ta, and tqdm).
Imports: Imports the installed libraries and pandas.
Load NSE 500 Sector Mapping: Reads a CSV file containing the sector mapping for NSE 500 stocks and creates a dictionary to map symbols to sectors.
Define Ticker List: Creates a list of unique stock symbols from the sector mapping data.
Indicator Calculation Function: Defines a function calculate_indicators that takes a DataFrame as input and calculates several technical indicators (Bollinger Bands Width %, MACD, Normalized MACD, ADX, ROC, and Stochastic %D) and adds them as new columns to the DataFrame.
Backtest: This is the main part of the code that iterates through each ticker:
Downloads historical weekly data for each stock using yfinance.
Skips stocks with insufficient data.
Cleans up column names and resets the index.
Calls calculate_indicators to add the technical indicators.
Removes rows with missing values.
Iterates through the data to check for specific trading signals based on the calculated indicators.
If a signal is found, it calculates the returns for the next 8 weeks and stores the results (symbol, entry date, close price, indicator values, and future returns) in a list.
Includes error handling to skip stocks that fail to download or process.
Save Output: Converts the list of results into a pandas DataFrame and saves it to a CSV file named nse500_backtest_results.csv.
The code also uses tqdm to display a progress bar during the backtesting process.
