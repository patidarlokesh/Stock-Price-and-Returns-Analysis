# Stock-Price-and-Returns-Analysis
A Python script that downloads historical stock data for several major tech companies, calculates daily returns, and visualizes the stock prices and cumulative returns over a 10-year period.


# The main libraries
Python: The core programming language.
pandas: Used for data manipulation and analysis, handling the DataFrames.
yfinance: A library for downloading historical market data from Yahoo Finance.
Matplotlib (via pandas.plot): Used for generating the plots and visualizations.

# mport Libraries
Explain the purpose of each library imported at the beginning of the script.
                
                import datetime as dt # For handling dates and time
                import yfinance as yf # For downloading stock data
                import pandas as pd # For data manipulation

# Tickers and Date Range
                tickers = ["AMZN", "AAPL", "MSFT", "GOOG"]
                start = dt.datetime.today() - dt.timedelta(3650) # 10 years ago
                end = dt.datetime.today() # Today's date
# Download and Clean Data

                cl_price = pd.DataFrame()
                for stock in tickers:
                    cl_price[stock] = yf.download(stock, start, end)["Close"]
                cl_price.dropna(axis=0, how="any", inplace=True) # Remove rows with any missing data

# Calculate Daily and Cumulative Returns
                daily_returns = cl_price.pct_change()
                (1 + daily_returns).cumprod() # Calculates the growth of a $1 investment over time


  #  Cumulative Returns

     
