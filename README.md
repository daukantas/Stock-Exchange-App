# Stock-Exchange-App

This program is developed in C++ using object oriented concepts to analyse stock trades and give a setailed report on the trades using various parameters.


Input:
The input file represents a very simplified stream of trades on an exchange.  
Each row represents a trade.  If you don't know what that means don't worry.  
The data can be thought of as a time series of values in columns: 

<TimeStamp>,<Symbol>,<Quantity>,<Price>

Although the provided input file is small, the solution should be able to handle 
a source dataset well beyond the amount memory and hard disk space on your machine.
Thus any solution that reads the entire file contents into memory at once is unacceptable.

Definitions
- TimeStamp is value indicating the microseconds since midnight.
- Symbol is the 3 character unique identifier for a financial 
  instrument (Stock, future etc.)
- Quantity is the amount traded
- Price is the price of the trade for that financial instrument.

Safe Assumptions:
- TimeStamp is always for the same day and won't roll over midnight.
- TimeStamp is increasing or same as previous tick (time gap will never be < 0).
- Price - our currency is an integer based currency.  No decimal points.
- Price - Price is always > 0.

Example: here is a row for a trade of 10 shares of aaa stock at a price of 12 
1234567890,aaa,10,12

Problem:
Find the following on a per symbol basis:
- Maximum time gap
  (time gap = Amount of time that passes between consecutive trades of a symbol)
  if only 1 trade is in the file then the gap is 0.
- Total Volume traded (Sum of the quantity for all trades in a symbol).
- Max Trade Price.
- Weighted Average Price.  Average price per unit traded not per trade.
  Result should be truncated to whole numbers.

  Example: the following trades
	20 shares of aaa @ 18
	5 shares of aaa @ 7
	Weighted Average Price = ((20 * 18) + (5 * 7)) / (20 + 5) = 15

Output:
The output file should be a comma separate file with this format:
symbol, MaxTimeGap, Volume, WeightedAveragePrice, MaxPrice

The output should be sorted by symbol ascending ('aaa' should be first).

Sample Input:<br>
52924702314,aaa,13,1136<br>
52924702549,aac,20,477<br>
52925641407,aab,31,907<br>
52927350412,aab,29,724<br>
52927783980,aac,21,638<br>
52930489178,aaa,18,1222<br>
52931654404,aaa,9,1077<br>
52933453444,aab,9,756<br>

Sample Output:<br>
aaa,5786864,40,1161,1222<br>
aab,6103032,69,810,907<br>
aac,3081431,41,559,638<br>
