# Back_test_API_Binance

Read this in other languages: [Portuguese](https://github.com/Kalienel/back_test_API_Binance/blob/main/README.md)

This tool was developed to calculate possible returns in any coin pain on Binance utilizing technical analysis indicators in [TA](https://technical-analysis-library-in-python.readthedocs.io/en/latest/) Python module

### Requirements
- Pandas
- Numpy
- Matplotlib
- Seaborn
- binance-connector
- ta

### Set-up functions


Market_data function is responsible for making requests from Binance API and returning a dataframe with candlestick's info
Load_market gets the market_data dataframe and adds TA indicators, with EMA 9, EMA 26 and RSI 7 as default
Plot_market uses load_market info and plots the data, it can also receive a list of buy and sell dates, output from back_test function

### Back_test Function

The back_test function receives load_market and the dataframe with prices, indicators and another argument with initial investment money. It's np.where section is where the main logic is located, with the moment of BUY and SELL well defined. Already with a simple EMA cross + RSI under 80 as default. This returns a dataframe with profit, profit percentage and gross

It works based on iteration of the trading logic, applying the np.where strategy to every data point and recording the returns if the investment was made in each moment of coins lifespan on Binance.

In the end it also returns a csv that can be analyzed any way the user desired

![Final dataframe](https://github.com/Kalienel/back_test_API_Binance/blob/main/back_test.PNG)

## Orders

This notebook returns 3 dataframes
- All buy and sell orders
- Only bids
- Only asks

The purpose of this function is to be used to automate order creation based on previous backtest and market making
It also returns a csv with all order book information

![Order book](https://github.com/Kalienel/back_test_API_Binance/blob/main/orders.PNG)
