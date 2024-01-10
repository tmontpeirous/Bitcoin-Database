<h1>Bitcoin Database</h1>

 <h2>Description</h2>
This is the first step in building a market pricing database.
This can be used for logging, backtesting, and spotting anomolies in price.
This code scrapes historical market data from from Binance Echange by connecting directly to the Binance API
(Must be outside of USA to connect to Binance API)

<h2>Languages and Utilities Used</h2>
- <b>Python</b> 
- <b>Binance API </b>
 
 <h2>Binance Scraper </h2>
 
csvfile = open("6Hour2017", "w", newline='')
candlestick_writer= csv.writer(csvfile, delimiter=',')
candlestick_writer.writerow(candlestick)
candlesticks = client.get_historical_klines("BTCUSDT",
Client.KLINE_INTERVAL_6HOUR, "1 Jan, 2016", "16 May, 2023")
for candlestick in candlesticks: candlestick_writer.writerow(candlestick)
csvfile.close()
df= pd.read_csv("6Hour2017",index_col = 0, parse_dates = [0])

 <h2>Organize The Data By Renaming the Columns</h2>

df = df.reset_index()
df.columns = [
    "Open time",
    "Open",
    "High",
    "Low",
    "Close",
    "Volume",
    "Close time",
    "Quote asset volume",
    "Number of trades",
    "Taker buy base asset volume",
    "Taker buy quote asset volume",
    "Ignore"
]

https://ibb.co/W6sC5Jw

<h2>Set The Index</h2>

df = df.set_index('Datetime')
