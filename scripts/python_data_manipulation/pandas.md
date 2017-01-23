[← back to *Main Page*](https://github.com/dawkiny/Python3/blob/master/PythonDataManipulation.md)


# Pandas

## Data Structure

* [Series](#numpy)
* [DataFrame](#pandas)  
* [Index](#pandas)  
* [groupby](#pandas)  
##

* ```ndarray```  


Installation
```sh
pip install numpy
conda install numpy
```

```python
import numpy as np
```

### words

### Operation
 
```python
mydf = pd.DataFrame({'col1': [1, 2, 4,],
                     'col2': 'abc'})


mydf = pd.DataFrame({'col1': [1, 2, 4,],
                     'col2': list('abc')})

a['col1']    # pd.Series
a[['col1']]  # pd.DataFrame
a.col1       # pd.Series

a.col3 = ['d', 'e', 'f']
a.col3
a['col3'] = ['aa', 'bb', 'cc']
a
a[['col3']]
a.col3
```

```python
codes
```



[↑ Up to the Top](#python-data-manipulation)

---
## Pandas

* ```Series```  
* ```DataFrame```  

Installation
```sh
pip install pandas
conda install pandas
```

```python
import pandas as pd
from pandas import Series as sr
from pandas import DataFrame as df
```

words

### words

### Operation
 
```python
codes
```



[↑ Up to the Top](#python-data-manipulation)

---
## datetime
words

### words

### Operation
 
```python
codes
```



[↑ Up to the Top](#python-data-manipulation)

---
## PyTables
words

### words

### Operation
 
```python
codes
```



[↑ Up to the Top](#python-data-manipulation)





---
[← back to *Main Page*](https://github.com/dawkiny/Python3/blob/master/PythonProgramming.md)