#### JOINS AND CTE's (Project 4)

1. What are the three longest trips on rainy days?

  ```SQL
  WITH
    rainy_days
  AS (
    SELECT 
      Date
    FROM 
      weather
    WHERE events = 'Rain' 
    GROUP BY 1
  ) 

  SELECT 
    trip_id,
    DATE(start_date) trip_date,
    duration
  FROM 
     trips
  JOIN 
       rainy_days
  ON   
     rainy_days.Date = trip_date
  ORDER BY trips.duration DESC
  LIMIT 3 
  ```

2. Which station is empty most often?

  ```SQL
  WITH 
    empty_stations
  AS (
    SELECT 
      status.station_id,
      COUNT(*) no_bike_count
    FROM 
      status
    WHERE 
      bikes_available = 0 
    GROUP BY 1  
  )

  SELECT 
    stations.station_id,
    stations.name
  FROM 
    stations
  JOIN 
    empty_stations
  ON 
    empty_stations.station_id = stations.station_id
  ORDER BY no_bike_count DESC 
  LIMIT 1 
  ```

3. Return a list of stations with a count of number of trips starting at that station but ordered by dock count.
  ```SQL
  WITH 
    station_trips
  AS (
    SELECT 
      trips.start_station,
      COUNT(*) count
    FROM 
      trips
    GROUP BY 1  
  )

  SELECT 
    stations.station_id,
    
    stations.name,
    stations.dockcount
  FROM 
    stations
  JOIN 
    station_trips
  ON 
    station_trips.start_station = stations.name
  ORDER BY stations.dockcount DESC  
```      