#### SELECT, FROM, WHERE (Project 2)
1. The ID's and durations for all trips of duration greater than 500, ordered by duration.
  ```SQL
  SELECT
    trip_id,
    duration
  FROM trips
  WHERE duration > 500
  
  ORDER BY duration
  ```
2. Every column of the stations table for station id 84.
  ```SQL
  SELECT *
  FROM stations
  WHERE station_id == 84 
  ```
3. The min temperatures of all the occurrences of rain in zip 94301.
  ```SQL
  SELECT MinTemperatureF
  FROM weather
  WHERE ZIP == 94301 AND Events = 'Rain'
  ```