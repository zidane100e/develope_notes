## arguments
There are some arguments in pre-defined functions.
* context : TradingAlgorithm
* data : BarData

## functions
* analyze : automatically called after the backtest is done.
  * do not run by calling run_algorithm
* record : record values each day
  * given to analyze as perf 
