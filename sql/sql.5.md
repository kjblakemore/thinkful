#### Airbnb cities (Project 5)

1. What's the most expensive listing? What else can you tell me about the listing?
  ```SQL
  SELECT *
  FROM listings    
  ORDER BY price DESC 
  LIMIT 1
  ```  

2. What neighborhoods seem to be the most popular?    
  ```SQL
  SELECT 
    neighbourhood,
    Count(id) as listing_count
  FROM listings

  GROUP BY 1
  ORDER BY listing_count DESC
  ```

3. What time of year is the cheapest time to go to your city? 
  ```SQL
  SELECT 
    date,
    AVG(LTRIM(price, '$')) avg_price
  FROM
    calendar
  WHERE available = 't'  
  GROUP BY 1
  ORDER BY avg_price
  ```
4. What is the busiest time to go to your city?
  ```SQL
  SELECT 
    date,
    COUNT(*) no_availabilities
  FROM
    calendar
  WHERE available = 'f'  
  GROUP BY 1
  ORDER BY no_availabilities DESC
  ```  