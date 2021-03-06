To load the CSV files created in Chapter 3 into BigQuery:
* Open CloudShell and navigate to 05_bqdatalab
* Run the script to load data into BigQuery:
	```
	bash load_into_bq.sh <BUCKET-NAME>
	```
* Visit the BigQuery console to query the new table:
	```
	SELECT
	  *
	FROM (
	  SELECT
	    ORIGIN,
	    AVG(DEP_DELAY) AS dep_delay,
	    AVG(ARR_DELAY) AS arr_delay,
	    COUNT(ARR_DELAY) AS num_flights
	  FROM
	    flights.tzcorr
	  GROUP BY
	    ORIGIN )
	WHERE
	  num_flights > 3650
	ORDER BY
	  dep_delay DESC
	
	``` 
* In BigQuery, run this query and save the results as a table named trainday
	```
	  #standardsql
	SELECT
	  FL_DATE,
	  IF(MOD(ABS(FARM_FINGERPRINT(CAST(FL_DATE AS STRING))), 100) < 70, 'True', 'False') AS is_train_day
	FROM (
	  SELECT
	    DISTINCT(FL_DATE) AS FL_DATE
	  FROM
	    `flights.tzcorr`)
	ORDER BY
	  FL_DATE
	```
  This table will be used throughout the rest of the book.

* In CloudShell, create a Datalab instance (change the zone to match where your bucket is located):
	```
	datalab create --zone us-central1-a dsongcp
	```
* Once you get the message that the instance is reachable on localhost:8081, navigate to the web page using the Web Preview button on the top-right of Cloud Shell.

* Within Datalab, start a new notebook. Then, copy and paste cells from <a href="exploration.ipynb">exploration.ipynb</a> and click Run to execute the code.


