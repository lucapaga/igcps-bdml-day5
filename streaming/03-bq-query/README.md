# Day 5. Streaming ETL with PubSub and Dataflow
## Step 3. Monitor on BigQuery

### Stream processing
* Once you see events being written into BigQuery, you can query them from the BigQuery console:
			```
			#standardsql
			SELECT
			  *
			FROM
			  `flights.streaming_delays`
			WHERE
			  airport = 'DEN'
			ORDER BY
			  timestamp DESC
			```
	
