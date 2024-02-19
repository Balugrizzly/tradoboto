Broker:

https://www.mexc.com/mexc-api
https://www.mexc.com

MEXC - will allow for deposits / investors to use crypto
Initially was thinking of MT4/ MT5 supporting trad brokers but there is a lack of APIs
and this would limit investors to tradfi. 

Technical Requirements:

API key from MEXC with read / trade capabilities => to be created
Server with high availability. Does not need to be anything fancy 

Indicators:

TWO indicators are used.
BBWP (Public indicator),
There are specific settings with this indicator that the strategy utilizes:

Extreme Low BBWP: 15%tile or lower.
Extreme high BBWP: 85th%tile or higher.

CT RSI (Closed source indicator), no source code available:
There are specific settings with this indicator that the strategy utilizes:

Source: Close
RSI period: 14
Type: Cutlers
Signal period: 12
Type: SMA
Divergence Lookback bars: 22

Execution:

1. Wait for extreme low BBWP - Produce an alert when this happens
2. Once low BBWP occurs, wait for a divergence signal from the RSI, produce alert when this happens
3. Trade in the direction of the RSI signal IE if bearish short if bullish long

Trade Params:

1. 5% of portfolio
2. 4h timeframe
3. Stop loss is below the last two days of price action
4. Entries are market orders upon divergence confirmation (candle closure)
5. If volatility expands (no longer in 15th or lower %tile and then recontracts, and an opposite signal is produced, the initial trade is closed and a new one is open
5. Operating hours are 10AM AEST => 6PM AEST 7 days a week
6. 1:1.5 RR (we can also look at using dynamic TP based off extreme BBWP but I would run this as a separate strategy)