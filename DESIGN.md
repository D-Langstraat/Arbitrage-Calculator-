The problem I was trying to solve was the difficulty in finding aribtrage opportunities given the amount of quickly changing data that needs to be considered. 

Arbitrage is when an asset is purchased in one exchange and then sold at a higher price on another exchange. A key to a succesful arbitrage strategy is trading quickly when opportunities arise. This program detects those opportunites across a large data set from CoinGecko on two exchanges Coinbase, and Kucoin.

Please know that there are risks associated with arbitrage that this program does not factor, such as the slippage of price that can happen between trade execution. This is a tool to be considered along with other factors. I am not licesned to provide financial advice and the programs outputs are not to be considered financial advice.


Under the hood:

Import requests as needed to get results of Coingecko API

Establish list of top 10 cryptos that will be referenced when option 1 is selected

-------------
The 1st function getPrice gets crypto name and market from Coingecko API.
url saves url for API
results creates a dict of the crypto info and then gets results of ticker info
We iterate through the results dict for 3 pieces of info from the API base(ticker) Target(trading pair) and Price(most recent spot price). We want to filter out trading pairs that
are not in USD or USD stable coins.

-------------
The 2nd function getChange does the arithmatic and displays the results
it gets the price from both exchanges
it checks and rejects request that come back empty and prints "not found" if empty
it divides the assets prices determines if they meet the .5% threshold for price difference to weed out insignificant differences - if one wanted to increase this threshold they could by chang the .005 to .01 or .001 depending on their desired threshold.
it then determines which exchange has the arbitrage opportunity on it - or none
and prints the results as price on both exchanges and price difference if
opportunity is found.

-------------
The main function starts the program off
Welcome screen loads and asks the user to make a choice 1 or 2 for top 10 crypto
there is a loop so after a user inputs a ticker the options will restart
choice is established as an input for option 1 or 2
option 1 will get info for tickers in top 10 list
option 2 will get further prompt for custom ticker and get info for it
if user inputs anything besides 1 or 2 the program will end


