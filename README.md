# Connect to Binance download crypto prices and calculate volatility

# Connect to API

    pip install binance-connector

    from binance.spot import Spot

    client = Spot()

    import time
# Libraries

    import pandas as pd

    import matplotlib.pyplot as plt

    import numpy as np

    import math

    import plotly.graph_objects as go

# Create DataFrame with data
    df = pd.DataFrame(klines, columns=['timestamp', 'open', 'high', 'low', 'close', 'volume', 'close_time', 'quote_asset_volume', 'number_of_trades',                     
    'taker_buy_base_asset_volume', 'taker_buy_quote_asset_volume', 'ignore'])

    df['timestamp'] = pd.to_datetime(df['timestamp'], unit='ms')

# Setting graph
    fig = go.Figure(data=[go.Candlestick(x=df['timestamp'],

                                     open=df['open'],
                                     
                                     high=df['high'],
                                     
                                     low=df['low'],
                                     
                                     close=df['close'])])

#Titles and labels

    fig.update_layout(title=f'Precio de {symbol} en intervalos de {interval}',
                  xaxis_title='Tiempo',
                  yaxis_title='Precio (USD)')

#Show graphic

    fig.show()
# Calculate daily returns as percentage price changes
df['Close'] = df['close'].astype(float)
df['Return'] = 100 * (df['Close'].pct_change()).dropna()
# View the data
#print(df.tail(10))
# Plot the price returns
plt.plot(df['timestamp'],df['Return'], color = 'orange', label = 'Daily Returns')
plt.legend(loc='upper right')
plt.show()

# Calculate daily std of returns
std_daily = df['Return'].std()
print('Daily volatility: ', '{:.2f}%'.format(std_daily))

# Convert daily volatility to monthly volatility
std_monthly = math.sqrt(21) * std_daily
print ('Monthly volatility: ', '{:.2f}%'.format(std_monthly))

# Convert daily volatility to annaul volatility
std_annual = math.sqrt(252) * std_daily
print ('Annual volatility: ', '{:.2f}%'.format(std_annual))


