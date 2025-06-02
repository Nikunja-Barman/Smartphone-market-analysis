# Unlocking Smartphone Market Trends: A Data-Driven Analysis👨🏼‍💻📈

## MS SQL Server was specifically employed for this project for initial data cleaning and insights drawing. Below are the detailed SQL queries that were utilized for performing the analysis.🛢

### 1.-- using database
use smartphone;

![image](https://github.com/user-attachments/assets/c4601456-44ce-43b1-9e3a-62bbf4137933)

### 2. -- stored procedure query for describing the table
EXEC sp_help 'phone_data';

![image](https://github.com/user-attachments/assets/90a1a658-a754-4674-9410-f46244e580e8)

### 3. -- Query for checking the null values in the columns
select avg_rating, processor_brand, num_cores, processor_speed, battery_capacity, fast_charging, os, primary_camera_front from phone_data;

![image](https://github.com/user-attachments/assets/792b4822-52bf-4c68-9a0d-03e08cb071db)

### 4. -- Filling the null values of avg_rating column with 0
UPDATE phone_data
SET avg_rating = 0
WHERE avg_rating IS NULL;

![image](https://github.com/user-attachments/assets/8bdf5d87-993a-40a8-a3c8-6f8abe9d7f6b)

### 5. -- Querying to check the null values in avg_rating column
SELECT
    CASE
        WHEN EXISTS (SELECT 1 FROM phone_data WHERE avg_rating IS NULL)
        THEN 'Null values found in avg_rating'
        ELSE 'No null values found in avg_rating'
    END AS NullCheckResult;

![image](https://github.com/user-attachments/assets/7ce7ac53-1077-4f85-b734-7de1443cc3ce)

### 6. -- Query to fill the null values of num_cores, processor_speed, battery_capacity, fast_charging, primary_camera_front columns with 0

UPDATE phone_data
SET
    num_cores = ISNULL(num_cores, 0),
    processor_speed = ISNULL(processor_speed, 0),
    battery_capacity = ISNULL(battery_capacity, 0),
    fast_charging = ISNULL(fast_charging, 0),
    primary_camera_front = ISNULL(primary_camera_front, 0)
WHERE
    num_cores IS NULL
    OR processor_speed IS NULL
    OR battery_capacity IS NULL
    OR fast_charging IS NULL
    OR primary_camera_front IS NULL;

![image](https://github.com/user-attachments/assets/f9d570b6-9f02-4da1-818c-f80369c745d3)

### 7. -- Query for checking the null values in the columns
select avg_rating, processor_brand, num_cores, processor_speed, battery_capacity, fast_charging, os, primary_camera_front from phone_data;

![image](https://github.com/user-attachments/assets/6a6b0c0d-2a2a-42e0-b2cf-d4df0f4befd8)

### 8. -- What is the average price of smartphones for each brand, and how does the price distribution vary across brands
select brand_name, AVG(price) as Avg_price from phone_data
group by brand_name
order by Avg_price desc;

![image](https://github.com/user-attachments/assets/8c5989f8-71f0-4cfe-b4da-dce3e017c3f2)

### 9. -- What percentage of smartphones in the dataset support 5G, and how does 5G adoption correlate with price

--    Percentage of Smartphones Supporting 5G
select (sum(case when [_5G_or_not]=1 then 1 else 0 end)*100)/count(*) as Percent_5G
from phone_data

![image](https://github.com/user-attachments/assets/25c9894b-0d05-4936-a02e-6f4530091f3a)

--    Correlation Between 5G Adoption and Price
SELECT [_5G_or_not], AVG(price) AS average_price
FROM phone_data 
GROUP BY [_5G_or_not];

![image](https://github.com/user-attachments/assets/583174c1-3af0-49c9-add4-67d8eb115cc9)

### 10. -- Which processor brand and number of cores are most common, and how do they relate to processor speed and average rating?

-- Most Common Processor Brand
SELECT TOP 1
    processor_brand,
    COUNT(*) AS frequency
FROM 
    phone_data 
GROUP BY 
    processor_brand
ORDER BY 
    frequency DESC;

![image](https://github.com/user-attachments/assets/913e9f75-a175-40c9-bda1-73abdfc0d3d4)

-- Most Common Number of Cores
SELECT TOP 1
    num_cores,
    COUNT(*) AS frequency
FROM 
    phone_data 
GROUP BY 
    num_cores
ORDER BY 
    frequency DESC;

![image](https://github.com/user-attachments/assets/e3f7699b-0d33-4073-82ba-57d638ceda70)

-- Relationship Between Processor Brand, Number of Cores, Processor Speed, and Average Rating

select processor_brand, num_cores, AVG(processor_speed) as Avg_speed, AVG(avg_rating) as Avg_rating
from phone_data
group by processor_brand, num_cores
order by processor_brand, num_cores

![image](https://github.com/user-attachments/assets/41a4a36a-e75e-4fbd-b220-93b3471decd5)

### 11. -- What is the relationship between battery capacity, fast charging speed, and average rating? 
      Are phones with higher battery capacity and faster charging more highly rated? */

--  Average Rating by Battery Capacity Ranges

SELECT 
    CASE 
        WHEN battery_capacity < 4000 THEN 'Less than 4000 mAh'
        WHEN battery_capacity >= 4000 AND battery_capacity < 5000 THEN '4000-4999 mAh'
        WHEN battery_capacity >= 5000 THEN '5000+ mAh'
        ELSE 'Unknown'
    END AS battery_range,
    AVG(avg_rating) AS average_rating
FROM 
    phone_data 
GROUP BY 
    CASE 
        WHEN battery_capacity < 4000 THEN 'Less than 4000 mAh'
        WHEN battery_capacity >= 4000 AND battery_capacity < 5000 THEN '4000-4999 mAh'
        WHEN battery_capacity >= 5000 THEN '5000+ mAh'
        ELSE 'Unknown'
    END;

![image](https://github.com/user-attachments/assets/facdcfc4-6090-4e96-871d-d9ae6b8a2dc8)

--  Average Rating by Fast Charging Speed Ranges

SELECT 
    CASE 
        WHEN fast_charging < 30 THEN 'Less than 30W'
        WHEN fast_charging >= 30 AND fast_charging < 60 THEN '30-59W'
        WHEN fast_charging >= 60 THEN '60+W'
        ELSE 'Unknown'
    END AS charging_range,
    AVG(avg_rating) AS average_rating
FROM 
    phone_data
GROUP BY 
    CASE 
        WHEN fast_charging < 30 THEN 'Less than 30W'
        WHEN fast_charging >= 30 AND fast_charging < 60 THEN '30-59W'
        WHEN fast_charging >= 60 THEN '60+W'
        ELSE 'Unknown'
    END;

![image](https://github.com/user-attachments/assets/f3a758d6-c159-4278-8690-201050f83a88)

-- Correlation Between Battery Capacity, Fast Charging, and Average Rating

SELECT 
    AVG(battery_capacity) AS avg_battery_capacity,
    AVG(fast_charging) AS avg_fast_charging,
    AVG(avg_rating) AS avg_rating
FROM 
    phone_data

![image](https://github.com/user-attachments/assets/c43df710-19fe-44ed-b82b-8d33eca25dc8)

-- More Granular Correlation for every unique combination of Battery Capacity & Fast Charging against Average Rating

SELECT 
    battery_capacity,
    fast_charging,
    AVG(avg_rating) AS average_rating
FROM 
    phone_data
GROUP BY 
    battery_capacity,
    fast_charging
ORDER BY
    battery_capacity,
    fast_charging;

![image](https://github.com/user-attachments/assets/ea52dd79-cdac-450b-9650-a731c70b188b)

### 12. -- How does the primary camera resolution (rear and front) correlate with the average rating and price of smartphones?

-- Correlation Between Rear Camera Resolution, Average Rating, and Price

SELECT 
    AVG(primary_camera_rear) AS avg_rear_camera_res,
    AVG(avg_rating) AS avg_rating,
    AVG(price) AS avg_price
FROM 
    phone_data

![image](https://github.com/user-attachments/assets/690b8dbe-5125-4231-83ad-48a27796ba99)

-- Correlation Between Front Camera Resolution, Average Rating, and Price

SELECT 
    AVG(primary_camera_front) AS avg_front_camera_res,
    AVG(avg_rating) AS avg_rating,
    AVG(price) AS avg_price
FROM 
    phone_data

![image](https://github.com/user-attachments/assets/4b5819bd-a7f4-4f26-acfd-d505ec62c065)

-- More Granular Correlation for every unique combination of front_camera & rear_camera against Average Rating and Price

SELECT 
    primary_camera_rear,
    primary_camera_front,
    AVG(avg_rating) AS avg_rating,
    AVG(price) AS avg_price
FROM 
    phone_data
GROUP BY 
    primary_camera_rear,
    primary_camera_front
ORDER BY
    primary_camera_rear desc,
    primary_camera_front;

![image](https://github.com/user-attachments/assets/98727e2b-7798-41ef-b58e-827dbfa04548)
