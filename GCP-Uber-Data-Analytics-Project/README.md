
use the bigquery to do the data cleansing, get ride of outliers(long distance), wrong record(rate_id), wrong shape code
fare_amount, trip_distance, tip_amount, tolls_amount, total_amount
According to the data description, 
  1.trip_distance extreme value 3.265055e+05
  2. fate_amount has negative value & extrame large value
  3.extra, mta_tax, tip_amount, tolls_amount, improvement negative value
  4.mta_tax negative value
  
## Data Cleansing
* locationid should be within the range of 1-263
* distance should greater than 0 but less than 100
* passenger should less than 6
* fare amount
