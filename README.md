# Connect to Binance download crypto prices and calculate volatility

#Connect to API

pip install binance-connector
from binance.spot import Spot
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import math
client = Spot()
import plotly.graph_objects as go
import time

