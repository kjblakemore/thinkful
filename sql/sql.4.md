#### JOINS AND CTE's (Project 4)

1. What are the three longest trips on rainy days?

  ```SQL
  WITH rainy_days
  AS (
    SELECT Date
    FROM weather
    WHERE events = 'Rain' 
    GROUP BY 1
  ) 

  SELECT 
    trip_id,
    DATE(start_date) trip_date,
    duration
  FROM trips
  JOIN rainy_days ON rainy_days.Date = trip_date

  ORDER BY trips.duration DESC
  LIMIT 3 
  ```

2. Which station is empty most often?

  ```SQL
  SELECT
    status.station_id,
    stations.name,
    COUNT(*) as no_bike_count
  FROM status
  JOIN stations ON status.station_id=stations.station_id
  WHERE bikes_available=0
  
  GROUP BY status.station_id

  ORDER BY no_bike_count DESC
  LIMIT 1
  ```

3. Return a list of stations with a count of number of trips starting at that station but ordered by dock count.
  ```SQL
  SELECT
    trips.start_station,
    COUNT(*) trip_count,
    stations.dockcount
  FROM trips
  JOIN stations ON trips.start_station=stations.name

  GROUP BY trips.start_station

  ORDER BY stations.dockcount DESC
  ```

 4. What's the length of the longest trip for each day it rains anywhere?
 ```SQL
  WITH rainy_days
  AS (
    SELECT Date
    FROM weather
    WHERE Events='Rain'
  )

  SELECT
    DATE(start_date) trip_date,
    MAX(duration) as longest_trip
  FROM trips
  JOIN rainy_days ON rainy_days.Date = trip_date

  GROUP BY trip_date
 ```    