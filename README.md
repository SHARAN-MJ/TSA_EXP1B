# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
## Date: 
## AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
## ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
## PROGRAM:
```
Name : SHARAN MJ
Reg no : 212222240097
```
### REGULAR DIFFERENCING
```
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
data=pd.read_csv("/content/airline-passengers.csv",parse_dates=['Month'],index_col='Month')
data.head()
passengers = pd.DataFrame(data)
passengers['shifted_value']=passengers['Passengers'].shift(1)
passengers['difference_value']=passengers['Passengers']-passengers['shifted_value']
passengers.dropna(inplace=True)
print(passengers)
passengers.plot(kind='line')
```
### SEASONAL ADJUSTMENT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data=pd.read_csv("/content/airline-passengers.csv",parse_dates=['Month'],index_col='Month')
passengers=pd.DataFrame(data)
result=seasonal_decompose(passengers['Passengers'],model='additive',period=1)
seasonal=result.seasonal
passengers['Seasonal_value']=passengers['Passengers']-seasonal
passengers.dropna(inplace=True)
print(passengers)
passengers.plot(kind='line')
```
### LOG TRANSFORMATIONS
```
import numpy as np
import pandas as pd
data= pd.read_csv('/content/airline-passengers.csv')
data.head()
data.dropna(inplace=True)
x=data['Month']
y=data['Passengers']
data_log=np.log(data['Passengers'])
X=data['Month']
Y=data_log
import matplotlib.pyplot as plt
plt.plot(x,y)
plt.xlabel('Original Data')
plt.plot(X,Y)
plt.xlabel('Log- Transformed data')
```

## OUTPUT:
![Screenshot 2024-09-23 112214](https://github.com/user-attachments/assets/14f33c99-ee59-4de4-ac2b-393050c89ab8)


### REGULAR DIFFERENCING:
![Screenshot 2024-09-23 112226](https://github.com/user-attachments/assets/60b1c106-c3b3-4190-92e0-726df0f63d48)


### SEASONAL ADJUSTMENT:
![Screenshot 2024-09-23 112620](https://github.com/user-attachments/assets/e5b27e9e-5798-4d1e-bb63-2b4cc10c7e7a)

### LOG TRANSFORMATION:
![Screenshot 2024-09-23 112237](https://github.com/user-attachments/assets/be2b37e3-40e6-4a75-ad3c-5f765f690164)

## RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
