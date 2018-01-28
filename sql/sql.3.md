#### Aggregates and Groups (Project 3)
1. What was the hottest day in our data set? Where was that?
  ```SQL
  SELECT 
    MAX(MaxTemperatureF),
    ZIP,
    Date
  FROM weather
  ```
2. How many trips started at each station?
  ```SQL
  SELECT 
    COUNT(*) as trip_count,
    start_station
  FROM trips

  GROUP BY start_station
  ```  
3. What's the shortest trip that happened?
  ```SQL
  SELECT 
    trip_id,
    MIN(duration) as minimum_duration
  FROM trips
  ```  

4. What is the average trip duration, by end station?
  ```SQL
  SELECT 
    AVG(duration) as average_duration,
    end_station
  FROM trips
  
  GROUP BY end_station
  ```