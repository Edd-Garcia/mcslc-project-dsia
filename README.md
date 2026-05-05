# MSCLC Respond Time Efficiency for Cities Based on Category

This project intends to analyze the efficiency of the new Oregon mobile response team MCSLC over its two operational years by comparing the average response time for each category of dispatch reason for three particular cities, Eugene, Springfield and Other.




## Environment Variables

To run this project, you will need to add the following environment variables to your .env file

`DATA_DIR` : Points to the folder where all your CSV/Excel files live




## Documentation

MCSLC is an excel sheet with 18 columns. You will load the data using `pd.read_exel()`


These columns are:


`ID`, `End Point of Dispatch`, `City`, `Dispatch Request Date & Time`, `Dispatch Date & Time`, `Arrival on Scene Date & Time`, `Engagement with Client Date & Time`. `MCIT Departure Date & Time`, `Reason for Dispatch #1`, `Reason for Dispatch #2`, `Reason for Dispatch #3`, `Reason for Dispatch #4`, `Reason for Dispatch #5`, `Disposition`, `Minutes: Request → Dispatch`, `Minutes: Dispatch → Arrival`, `Minutes: Arrival → Engagement`, `Minutes: Arrival → Departure`


Key columns are:

`End Point of Dispatch`, `City`, `Dispatch Request Date & Time`, `Dispatch Date & Time`, `Arrival on Scene Date & Time`, `Engagement with Client Date & Time`. `MCIT Departure Date & Time`, `Reason for Dispatch #1`, and `Disposition`

Preprocessing required:

Make sure the values for `End Point of Dispatch`, `Disposition`, and `Reason for Dispatch #1` are unique and not the similar values with different spelling. 

Remove any NA values from the columns for `Dispatch Request Date & Time`, `Dispatch Date & Time`, `Arrival on Scene Date & Time`, `Engagement with Client Date & Time`. `MCIT Departure Date & Time`. You will then use these columns to calculate five new columns using arithmetic. 

These columns are:

`Min: Request to Dispatch`, `Min: Dispatch to Arrival`, `Min: Arrival to Engagement`, `Min: Arrival to Departure`, and `Total Response Time` which subtracts `Dispatch Request Date & Time` from `MCIT Departure Date & Time`. Finally, extract the minutes and set the minutes as the values for these new columns. 



## Installation

Required libraries and packages for this project
```bash
import numpy as np
import pandas as pd
import scipy,sklearn
import matplotlib.pyplot as plt
import seaborn as sns
```
    
## Analytical Steps

•	Identify city trends. Plot average total response time by month for each city `Eugene`, `Springfield`, `Other`. Line plot where X: Months, Y: Mean(Total Response Time)
•	Using clean separate dataframes for each city, group the means of the different minute columns and the total response time column by year and month.
•	Melt the grouped table into three columns, Year_Month, Time Metric, and Minutes
•	Using Seaborn, use the melted table to graph a line plot for each time metric with Year_Month as the x variable.
•	Repeat these steps for Springfield and for Other.
•	Now group the minute columns based on the reason for dispatch. 
•	Using seaborn, create horizontal bar plots that show minutes as the x variable and the reasons for dispatch as the y variable for both operational years. Make a bar plot for each time difference column.
•	Repeat the previous steps for Springfield and Other

•	Potential models: Event Study, Dynamic DiD, Mixed Effects Durations.
