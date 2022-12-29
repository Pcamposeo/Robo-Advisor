# Robo-Advisor

Python program whose goal is to generate a portfolio, based on a random set of tickers, whose projected value over an arbitrary number of days is as close to its starting value as possible.

<b>Achievements:</b>

1. Increased performance times for io bound tasks by up to 800% by implementing multithreading to speed up API requests.
    - This project had the fastest data cleaning pipeline of anyone who completed the same project (Those in the class).

2. Developed efficient systems to select tickers and allocation of capital to achieve the goal and outperform a benchmark in achieving the goal.
    - Includes <b>1 million iteration</b> Monte Carlo simulation which runs in ~1m 30s

3. Successfully implemented a modified Capital Asset Pricing Model to accurately predict portfolio expected returns.

4. Accurately completed data analysis on portfolio and stock volatility using visual aids and important numbers.

5. Scored extremely well when submitted for evaluation to established finance professor James Thompson and Teaching Assistants.


\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\

Problems we Ran Into:
The K-MST algorithm solution we came up with was already extremely difficult to implement, hence, we optimized the dataset for the graph and directly ran the Maximum Spanning Tree algorithm on multiple combinations of stock tickers.
The graph was being initialized very slowly due to multiple dataframes being created. To solve this issue, we implemented multithreading and utilized hashtables instead of dataframes to achieve faster read and write times.
There wasn't enough options data available for some stocks, so we implemented a data filtering solution for stocks that lacked sufficient options data.
Set-up

Problems / Improvements that Still Exist:

\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\ REHANS (FIXXXXXXXXXXXXXXXXXXX)

Dependencies:
pandas
numpy
numpy_financial
matplotlib
datetime
dateutil.relativedelta
threading
yfinance
Queue
random

Authors: Piero Camposeo (Lead), Sathun Suthakaran, Ishaan Bansal

** Further, Delete above **

Problems and improvements:
- The correlation and volatility shit
- Correlation have full matrix and make into directed graph and the path which has the correlation closest to 0 is the best fff(im so tired)

Optimizations:

Auto-updated RF rate if included