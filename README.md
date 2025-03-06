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
df = pd.DataFrame(klines, columns=['timestamp', 'open', 'high', 'low', 'close', 'volume', 'close_time', 'quote_asset_volume', 'number_of_trades', 'taker_buy_base_asset_volume', 'taker_buy_quote_asset_volume', 'ignore'])

df['timestamp'] = pd.to_datetime(df['timestamp'], unit='ms')

# Setting graph
fig = go.Figure(data=[go.Candlestick(x=df['timestamp'],

                                     open=df['open'],
                                     
                                     high=df['high'],
                                     
                                     low=df['low'],
                                     
                                     close=df['close'])])


