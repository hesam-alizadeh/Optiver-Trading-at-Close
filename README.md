# Optiver Trading at Close Competition Repository
data at : https://www.kaggle.com/competitions/optiver-trading-at-the-close/data
## Description

Stock exchanges are fast-paced, high-stakes environments where every second counts. The intensity escalates as the trading day approaches its end, peaking in the critical final ten minutes. These moments, often characterised by heightened volatility and rapid price fluctuations, play a pivotal role in shaping the global economic narrative for the day.

Each trading day on the Nasdaq Stock Exchange concludes with the Nasdaq Closing Cross auction. This process establishes the official closing prices for securities listed on the exchange. These closing prices serve as key indicators for investors, analysts and other market participants in evaluating the performance of individual securities and the market as a whole.

Within this complex financial landscape operates Optiver, a leading global electronic market maker. Fueled by technological innovation, Optiver trades a vast array of financial instruments, such as derivatives, cash equities, ETFs, bonds, and foreign currencies, offering competitive, two-sided prices for thousands of these instruments on major exchanges worldwide.

In the last ten minutes of the Nasdaq exchange trading session, market makers like Optiver merge traditional order book data with auction book data. This ability to consolidate information from both sources is critical for providing the best prices to all market participants.

## Dataset Description

This repository contains historic data for the daily ten-minute closing auction on the NASDAQ stock exchange. The challenge is to predict future price movements of stocks relative to the synthetic index composed of NASDAQ-listed stocks.

### Files

- **[train/test].csv**: The auction data. Test data will be delivered by the API.
  - `stock_id`: Unique identifier for the stock.
  - `date_id`: Unique identifier for the date.
  - `imbalance_size`: Unmatched amount at the current reference price (USD).
  - `imbalance_buy_sell_flag`: Direction of auction imbalance (1 for buy-side, -1 for sell-side, 0 for no imbalance).
  - `reference_price`: Price at which paired shares are maximized.
  - `matched_size`: Amount that can be matched at the current reference price (USD).
  - `far_price`: Crossing price maximizing matched shares based on auction interest.
  - `near_price`: Crossing price maximizing matched shares based on auction and continuous market orders.
  - `[bid/ask]_price`: Price of the most competitive buy/sell level in the non-auction book.
  - `[bid/ask]_size`: Dollar notional amount on the most competitive buy/sell level in the non-auction book.
  - `wap`: Weighted average price in the non-auction book.
  - `seconds_in_bucket`: Seconds elapsed since the beginning of the day's closing auction.
  - `target`: 60-second future move in the wap of the stock, less the 60-second future move of the synthetic index (provided for the train set).

- **sample_submission**: A valid sample submission, delivered by the API.

- **revealed_targets**: API-served dataframe providing true target values for the entire previous date when `seconds_in_bucket` equals zero.

- **public_timeseries_testing_util.py**: An optional file to facilitate running custom offline API tests.

- **example_test_files/**: Data illustrating how the API functions, including files and columns delivered by the API.

- **optiver2023/**: Files enabling the API. Expect the API to deliver all rows in under five minutes and reserve less than 0.5 GB of memory.

- **optiver-trading-at-the-close.ipynb**: Jupyter notebook containing the code.


## Timeline

This is a forecasting competition with an active training phase and a second period where models will be run against real market data.

Training Timeline:

- **September 20, 2023** - Start Date.

- **December 13, 2023** - Entry Deadline. You must accept the competition rules before this date in order to compete.

- **December 13, 2023** - Team Merger Deadline. This is the last day participants may join or merge teams.

- **December 20, 2023** - Final Submission Deadline.


All deadlines are at 11:59 PM UTC on the corresponding day unless otherwise noted. The competition organizers reserve the right to update the contest timeline if they deem it necessary.

Forecasting Timeline:
Starting after the final submission deadline there will be periodic updates to the leaderboard to reflect market data updates that will be run against selected notebooks. Updates will take place roughly every two weeks.


- **March 20, 2024** - Competition End Date

## Note
- The unit of the target is basis points (0.01% price move).
- Size-related columns are in USD terms.
- Price-related columns are relative to the stock wap at the beginning of the auction period.

## Competition Details
This repository is created for the 'Trading at Close' competition hosted by Optiver. The challenge involves forecasting future price movements using time series data from the NASDAQ stock exchange's daily ten-minute closing auction.

## API Usage
Refer to the provided files in the `optiver2023/` directory for handling the API. Ensure predictions are made for the first three date IDs delivered by the API to advance but note that these predictions are not scored.

## Disclaimer
The private leaderboard will be determined using real market data gathered after the submission period closes.
