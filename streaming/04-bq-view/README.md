# Day 5. Streaming ETL with PubSub and Dataflow
## Step 4. Prepare user views

### Stream processing
* In BigQuery, run this query and save this as a view:
	```
		#standardSQL
		SELECT
		  airport,
		  last[safe_OFFSET(0)].*,
		  CONCAT(CAST(last[safe_OFFSET(0)].latitude AS STRING), ",", CAST(last[safe_OFFSET(0)].longitude AS STRING)) AS location
		FROM (
		  SELECT
		    airport,
		    ARRAY_AGG(STRUCT(arr_delay,
		        dep_delay,
		        timestamp,
		        latitude,
		        longitude,
		        num_flights)
		    ORDER BY
		      timestamp DESC
		    LIMIT
		      1) last
		  FROM
		    `flights.streaming_delays`
		  GROUP BY
		    airport )
	```   
