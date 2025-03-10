
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
* speed over 80mph
* trip_duration < 1min, so the trip_distance < 0.5mile
* trip duration > 720 min


fare_amount	$2.50 - $500	低于 $2.50 不合理（起步价），高于 $500 可能是异常值。
extra	$0 - $5	高峰时段附加费：$1.00；夜间附加费：$0.50；高于 $5 可能异常。
mta_tax	固定 $0.50	NYC 规定的 MTA 附加税，异常值可能是数据问题。
tip_amount	$0 - $100	一般不超过 30% 总费用，大额小费（>$100）可能是异常值。
tolls_amount	$0 - $30	过桥隧道费一般不超过 $30（例如 Verrazzano-Narrows Bridge）。
improvement_surcharge	固定 $0.30	2015 年后 NYC 出租车强制收取。
total_amount	$2.50 - $1000	应该是所有费用的总和，远低于 $2.50 或超过 $1000 可能是异常数据。
congestion_surcharge	$0 或 $2.50	适用于曼哈顿核心区域行程，不应该有其他值。
payment_type	1, 2, 3, 4, 5	超过 5 或者负值都是异常值。
