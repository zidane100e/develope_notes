## arguments
There are some arguments in pre-defined functions.
* context : TradingAlgorithm
* data : BarData

## functions
* analyze : automatically called after the backtest is done.
  * do not run by calling run_algorithm
  ```
  analyze : callable[(context, pd.DataFrame) -> None], optional
        The analyze function to use for the algorithm. This function is called
        once at the end of the backtest and is passed the context and the
        performance data.
  
  ```
* record : record values each day
  * given to analyze as perf 
* run_algorithm:
  * return : perf : pd.DataFrame  
             The daily performance of the algorithm. 
