# Robo-Advisor

Authors: Piero Camposeo (Lead), Sathun Suthakaran, Ishaan Bansal

Python program whose goal is to generate a portfolio, based on a random set of tickers, whose projected value over an arbitrary number of days is as close to its starting value as possible.

<b>Achievements:</b>

1. Increased performance times for io bound tasks by up to 800% by implementing multithreading to speed up API requests.
    - This project had the fastest data cleaning pipeline of anyone who completed the same project (Those in the class).

2. Developed efficient systems to select tickers and allocation of capital to achieve the goal and outperform a benchmark in achieving the goal.
    - Includes a one million iteration Monte Carlo simulation that runs in ~1m 30s

3. Successfully implemented a modified Capital Asset Pricing Model to accurately predict portfolio expected returns.

4. Accurately completed data analysis on portfolio and stock volatility using visual aids and important numbers.
    - Was able to show that the selected portfolio was accurate in terms of meeting the goal.

5. Scored extremely well when submitted for evaluation to established finance professor James Thompson and Teaching Assistants.

<b>Problems we Were Able to Fix / Improvements we Were Able to Make:</b>

1. Selecting a model which would be conducive to the goal of the program.
    - Collaborated to discuss important statistical measures, found a trusted pricing model that accurately implements all of them, modified it to fit our needs.
        - Issues with our model: Trying to use just one equation as the centerpiece of our program made it sometimes difficult to troubleshoot, as we had to work around certain aspects of it to fix others. In hindsight, de-coupling influencing factors and building separate models may have proven useful.

2. General issues with CPU-bound and IO-bound tasks slowing down the program.
    - Removed redundancies and number of API requests, implemented recursive threading, simplified code. (Especially exemplified in Monte Carlo simulation and data cleaning).

3. Issues with Pandas not being inclusive of the end date.
    - Implemented relativedelta to strategically change certain dates within functions to produce the desired information.

4. Quality Assurance and ETL was extremely slow due to API request time.
    - Implemented a unique, multithreaded and recursive function to Extract, Transform, and Load data, implemented Queues and efficient retrieval mechanisms to retrieve clean data.

5. YFinance outputting too much information to the console when a ticker was invalid.
    - Implemented a valid check function that strategically attempts to call on information from YFinance in such a way that only one error message is outputted if the ticker is invalid, then removing invalid tickers.

6. No objectively correct way to select the tickers that would be used in the final portfolio.
    - We decided that volatility and correlation were the most important factors to consider, and created the points system for selecting tickers.

7. Inaccurate calculation of market expected return.
    - The issue: initially, the group was simply taking a one-day market return, and multiplying it by the number of days desired by the user. We soon realized that this was causing inaccuracies in our predictions, as a one-day expected return, scaled up linearly, is different than the average of returns over periods of a given group of days. Also, this approach disregards the compounding of returns.
        - The solution: Developed function "expectedReturnXDays", which takes a list of daily returns, groups them by a number of days, finds the return for each group, and takes the average. This is an accurate calculation of expected return.

8. Inaccuracies with regards to returns data for the portfolio and market.
    - Retrieved price data with existing "get_closing_df", along with a new function, "get_harmonized_df", which is able to perform the same task as "get_closing_df", but with a selection of stocks to be merged. Developed function get_pct_change to gather the return over a given period.

<b>Problems / Improvements that Still Exist:</b>

1. Risk-free rate (rf)
    - We do not account for the fact that the rf changes over time. This could cause issues with accuracy of expected returns predictions (but not with the performance of the program in terms of our goal).
    - We do not automatically update the rf. This could be annoying for the user, and could cause issues with accuracy of expected returns predictions (but not with the performance of the program in terms of our goal).
    - The rf was causing inaccuracies and issues with regards to the Monte-Carlo simulation (for reasons beyond our comprehension). For this reason, we had to remove it from the simulation. This did not affect the performance of the program in terms of our goal, nor the accuracy of predictions, as is explained in the program.

2. Due to the nature of statistical distribution, for a portfolio of many stocks, the number of generated portfolios with one or more stocks at 
a high weight is disproportionately low compared to the number of generated portfolios whose weights all sit around 100% divided by the number of stocks (the mean). A different system of weight generation could be implemented to offset this.

3. The Monte Carlo simulation is a CPU-heavy task. Since the best_weighting function needs to generate 1 million portfolios, the computer spends most of the runtime crunching numbers. With this being said, multiprocessing may have been preferred for our simulation. Unfortunately, after many efforts, we could not get a multiprocessing system to work.

4. The program can be inconsistent, even when provided with the same information many times. This is especially prevalent with the Monte Carlo simulation. Periodically, it will output a portfolio that is noticeably different than the optimal portfolio / what it would normally output. This was happening very frequently before we removed the risk-free rate, but still happens sometimes. This may be a local issue, as we used an old surface pro to test-run the program.

Dependencies:
Pandas
Numpy
numpy_financial
MatPlotLib
datetime
dateutil.relativedelta
threading
YFinance
Queue
random
uniform