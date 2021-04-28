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
  * metrics : not sure metrics are attached to return-dataframe 'perf'
    ```
    metrics_set : iterable[Metric] or str, optional
        The set of metrics to compute in the simulation. If a string is passed,
        resolve the set with :func:`zipline.finance.metrics.load`.
    
    ```
    
## register new bundle
Most explanations in web sites uses old-style registration,  
putting register function in extension.py and run ingest in command terminal.  
But zipline-trader, new version of zipline, recommends using notebooks methods.  
Below are function call from jupyter notebook
```
from zipline.data.bundles import ingest, load, register
# I copied csvdir.py to custom_bundle and renamed csvdir_equities
from zipline.data.bundles.custom_bundle import csvdir_equities2

# using start_session and end_session makes using data complicated. not sure.
# Just using default(NOne) is easy

###########  register  ############
register(
    'custom-bundle2',
    csvdir_equities2(
        ['daily'],
        '/home/adminuser/shared/portfolios/OLMAR/csv'
    ),
    calendar_name='NYSE', # US equities
    #start_session=start_session,
    #end_session=end_session,
    create_writers=True
)

###########  ingest  ############
bundle_name = 'custom-bundle2' # choose what you want
ingest(bundle_name, os.environ, 
       show_progress=True)
      
###########  load  ############
bundle_data = bundles.load(bundle_name)      
```
