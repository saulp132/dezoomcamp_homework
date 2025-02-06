# dezoomcamp_homework
# Homework 1
homerworks solutions to the data engineer course from the zoomcamp
Code solutions homework 1

__Question 1__

docker run -it --entrypoint=bash python:3.12.8
root@de48da5ee367:/# pip --version


__Question 3__

SELECT COUNT(*) 
FROM green_taxi
WHERE trip_distance <= 1;

SELECT COUNT(*) 
FROM green_taxi
WHERE trip_distance > 1 AND trip_distance <=3;

SELECT COUNT(*) 
FROM green_taxi
WHERE trip_distance > 3 AND trip_distance <=7;

SELECT COUNT(*) 
FROM green_taxi
WHERE trip_distance > 7 AND trip_distance <=10;

SELECT COUNT(*) 
FROM green_taxi
WHERE trip_distance > 10;

__QUestion 4__
SELECT  lpep_pickup_datetime::timestamp::date, trip_distance
FROM green_taxi
where trip_distance = (SELECT MAX(trip_distance) FROM green_taxi);

__QUestion 6__
SELECT g.lpep_pickup_datetime, zpu."Zone" as pick_zone, zdo."Zone" dropoff_zone, g.tip_amount
from green_taxi g
join zones zpu
on g."PULocationID" = zpu."LocationID"
join zones zdo
on g."DOLocationID" = zdo."LocationID"
where CAST(g.lpep_pickup_datetime AS DATE) > '2019-09-30' and CAST(g.lpep_pickup_datetime AS DATE) < '2019-11-01' and zpu."Zone" = 'East Harlem North'
order by  g.tip_amount DESC;

# Homework 2

6.	How would you configure the timezone to New York in a Schedule trigger?
•	Add a timezone property set to EST in the Schedule trigger configuration
•	Add a timezone property set to America/New_York in the Schedule trigger configuration
•	Add a timezone property set to UTC-5 in the Schedule trigger configuration
•	Add a location property set to New_York in the Schedule trigger configuration
•	  - id: EST
•	    type: io.kestra.plugin.core.trigger.Schedule
•	    cron: "0 10 1 * *"
•	    timezone: EST
•	
•	  - id: America_New_York
•	    type: io.kestra.plugin.core.trigger.Schedule
•	    cron: "0 10 1 * *"
•	    timezone:  America/New_York
•	
•	  - id: UTC_5 
•	    type: io.kestra.plugin.core.trigger.Schedule
•	    cron: "0 10 1 * *"
•	    timezone: UTC-5 



