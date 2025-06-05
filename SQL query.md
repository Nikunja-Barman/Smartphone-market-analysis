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

### 13. -- What is the distribution of RAM and internal memory across different price ranges and brands?

-- RAM Distribution Across Price Ranges and Brands

SELECT 
    brand_name,
    CASE 
        WHEN price < 10000 THEN 'Budget Phone'
        WHEN price >= 10000 AND price < 30000 THEN 'Mid-Range Phone'
		WHEN price >= 30000 AND price < 50000 THEN 'Upper Mid-Range Phone'
		WHEN price >= 50000 THEN 'Flagship Phone'
        ELSE 'Ultra-Luxury Phone'
    END AS price_range,
    AVG(ram_capacity) AS avg_ram,
    MIN(ram_capacity) AS min_ram,
    MAX(ram_capacity) AS max_ram
FROM 
    phone_data
GROUP BY 
    brand_name,
    CASE 
        WHEN price < 10000 THEN 'Budget Phone'
        WHEN price >= 10000 AND price < 30000 THEN 'Mid-Range Phone'
		WHEN price >= 30000 AND price < 50000 THEN 'Upper Mid-Range Phone'
		WHEN price >= 50000 THEN 'Flagship Phone'
        ELSE 'Ultra-Luxury Phone'
    END;

![image](https://github.com/user-attachments/assets/6d3d09fb-12ec-4615-b1d7-4a5b4fe33445)

-- Internal Memory Distribution Across Price Ranges and Brands

SELECT 
    brand_name,
    CASE 
        WHEN price < 10000 THEN 'Budget Phone'
        WHEN price >= 10000 AND price < 30000 THEN 'Mid-Range Phone'
		WHEN price >= 30000 AND price < 50000 THEN 'Upper Mid-Range Phone'
		WHEN price >= 50000 THEN 'Flagship Phone'
        ELSE 'Ultra-Luxury Phone'
    END AS price_range,
    AVG(internal_memory) AS avg_internal_memory,
    MIN(internal_memory) AS min_internal_memory,
    MAX(internal_memory) AS max_internal_memory
FROM 
    phone_data
GROUP BY 
    brand_name,
    CASE 
        WHEN price < 10000 THEN 'Budget Phone'
        WHEN price >= 10000 AND price < 30000 THEN 'Mid-Range Phone'
		WHEN price >= 30000 AND price < 50000 THEN 'Upper Mid-Range Phone'
		WHEN price >= 50000 THEN 'Flagship Phone'
        ELSE 'Ultra-Luxury Phone'
    END;

![image](https://github.com/user-attachments/assets/987b63e2-bd5d-417e-95dc-665d6c0aed87)

### 14. -- How does screen size and refresh rate affect the price and average rating of smartphones?

-- Average Price and Average Rating by Screen Size Ranges

SELECT 
    CASE 
        WHEN screen_size < 6.0 THEN 'Compact Phones'
        WHEN screen_size >= 6.0 AND screen_size < 6.5 THEN 'Medium-Sized Phones'
        WHEN screen_size >= 6.5 AND screen_size < 7.0 THEN 'Large Phone'
        ELSE 'Foldable Phone'
    END AS screen_size_range,
    AVG(price) AS average_price,
    AVG(avg_rating) AS average_rating
FROM 
    phone_data
GROUP BY 
    CASE 
        WHEN screen_size < 6.0 THEN 'Compact Phones'
        WHEN screen_size >= 6.0 AND screen_size < 6.5 THEN 'Medium-Sized Phones'
        WHEN screen_size >= 6.5 AND screen_size < 7.0 THEN 'Large Phone'
        ELSE 'Foldable Phone'
    END;

![image](https://github.com/user-attachments/assets/272560d3-5ad1-4ff2-b37c-5cdd5de429fe)

-- Average Price and Average Rating by Refresh Rate Ranges

SELECT 
    CASE 
        WHEN refresh_rate <= 60 THEN '60Hz'
        WHEN refresh_rate > 60 AND refresh_rate <= 90 THEN '90Hz'
        WHEN refresh_rate > 90 AND refresh_rate <= 120 THEN '120Hz'
        ELSE '120+Hz'
    END AS refresh_rate_range,
    AVG(price) AS average_price,
    AVG(avg_rating) AS average_rating
FROM 
    phone_data
GROUP BY 
    CASE 
        WHEN refresh_rate <= 60 THEN '60Hz'
        WHEN refresh_rate > 60 AND refresh_rate <= 90 THEN '90Hz'
        WHEN refresh_rate > 90 AND refresh_rate <= 120 THEN '120Hz'
        ELSE '120+Hz'
    END;

![image](https://github.com/user-attachments/assets/8f262934-6417-4231-8484-4890a3ba139d)

-- Correlation Between Screen Size, Refresh Rate, Price, and Average Rating (Granular)

SELECT 
    screen_size,
    refresh_rate,
    AVG(price) AS average_price,
    AVG(avg_rating) AS average_rating
FROM 
    phone_data
GROUP BY 
    screen_size,
    refresh_rate
ORDER BY
    screen_size,
    refresh_rate;

![image](https://github.com/user-attachments/assets/644884fe-ed1d-4a28-abe1-174c09426180)

### 15. -- What is the distribution of operating systems (OS) across different brands and price ranges, and how does OS relate to average rating?

-- OS Distribution Across Brands and Price Ranges

SELECT 
    brand_name,
    CASE 
        WHEN price < 10000 THEN 'Budget Phone'
        WHEN price >= 10000 AND price < 30000 THEN 'Mid-Range Phone'
		WHEN price >= 30000 AND price < 50000 THEN 'Upper Mid-Range Phone'
		WHEN price >= 50000 THEN 'Flagship Phone'
        ELSE 'Ultra-Luxury Phone'
    END AS price_range,
    os,
    COUNT(*) AS os_count
FROM 
    phone_data
GROUP BY 
    brand_name,
    CASE 
        WHEN price < 10000 THEN 'Budget Phone'
        WHEN price >= 10000 AND price < 30000 THEN 'Mid-Range Phone'
		WHEN price >= 30000 AND price < 50000 THEN 'Upper Mid-Range Phone'
		WHEN price >= 50000 THEN 'Flagship Phone'
        ELSE 'Ultra-Luxury Phone'
    END,
    os
ORDER BY
    brand_name,
    price_range,
    os;

![image](https://github.com/user-attachments/assets/a9cbfb1f-fc0d-4baa-a1cc-32c677054e73)

-- Average Rating by OS

SELECT 
    os,
    AVG(avg_rating) AS average_rating
FROM 
    phone_data
GROUP BY 
    os;

![image](https://github.com/user-attachments/assets/4d8f08db-1011-4c11-8a0f-1e500ddfbfab)

-- Average Rating by OS and Price Range

SELECT 
    CASE 
        WHEN price < 10000 THEN 'Budget Phone'
        WHEN price >= 10000 AND price < 30000 THEN 'Mid-Range Phone'
		WHEN price >= 30000 AND price < 50000 THEN 'Upper Mid-Range Phone'
		WHEN price >= 50000 THEN 'Flagship Phone'
        ELSE 'Ultra-Luxury Phone'
    END AS price_range,
    os,
    AVG(avg_rating) AS average_rating
FROM 
    phone_data
GROUP BY 
    CASE 
        WHEN price < 10000 THEN 'Budget Phone'
        WHEN price >= 10000 AND price < 30000 THEN 'Mid-Range Phone'
		WHEN price >= 30000 AND price < 50000 THEN 'Upper Mid-Range Phone'
		WHEN price >= 50000 THEN 'Flagship Phone'
        ELSE 'Ultra-Luxury Phone'
    END,
    os
ORDER BY
    price_range,
    os;

![image](https://github.com/user-attachments/assets/b31a24c5-51cb-4fa2-8826-551294dd75cc)

### 16. -- How does the number of rear cameras relate to the price and average rating of smartphones

-- Average Price and Average Rating by Number of Rear Cameras

SELECT 
    num_rear_cameras,
    AVG(price) AS average_price,
    AVG(avg_rating) AS average_rating
FROM 
    phone_data
GROUP BY 
    num_rear_cameras
ORDER BY 
    num_rear_cameras;

![image](https://github.com/user-attachments/assets/f2eb1342-0fa3-4bac-92ec-267ef0307e9c)

-- General Correlation between Number of Rear Cameras, Price, and Average Rating

SELECT 
    AVG(num_rear_cameras) AS avg_num_rear_cameras,
    AVG(price) AS average_price,
    AVG(avg_rating) AS average_rating
FROM 
    phone_data

![image](https://github.com/user-attachments/assets/6d076521-8c48-4b79-a29f-c95de2d1155c)

### 17. -- What is the relationship between resolution height, resolution width, and screen size. Also, how does screen resolution relate to price?

-- Relationship Between Resolution Height, Resolution Width, and Screen Size

SELECT 
    AVG(resolution_height) AS avg_resolution_height,
    AVG(resolution_width) AS avg_resolution_width,
    AVG(screen_size) AS avg_screen_size
FROM 
    phone_data

![image](https://github.com/user-attachments/assets/e49fc0d5-64f9-4315-b89e-85e5ee3db82d)

-- Average Price by Screen Size Ranges (To see how screen size relates to price)

SELECT 
    CASE 
        WHEN screen_size < 6.0 THEN 'Compact Phones'
        WHEN screen_size >= 6.0 AND screen_size < 6.5 THEN 'Medium-Sized Phones'
        WHEN screen_size >= 6.5 AND screen_size < 7.0 THEN 'Large Phone'
        ELSE 'Foldable Phone'
    END AS screen_size_range,
    AVG(price) AS average_price
FROM 
    phone_data
GROUP BY 
    CASE 
        WHEN screen_size < 6.0 THEN 'Compact Phones'
        WHEN screen_size >= 6.0 AND screen_size < 6.5 THEN 'Medium-Sized Phones'
        WHEN screen_size >= 6.5 AND screen_size < 7.0 THEN 'Large Phone'
        ELSE 'Foldable Phone'
    END;

![image](https://github.com/user-attachments/assets/7ff2639b-e366-4ad5-b5ef-d10ee15fa6f5)

--	Average Price by Resolution Height and Width (Showing the Avg price for every distinct pair of Resolution_height and Resolution_width

SELECT 
    resolution_height,
    resolution_width,
    AVG(price) AS average_price
FROM 
    phone_data
GROUP BY 
    resolution_height,
    resolution_width
ORDER BY
    resolution_height,
    resolution_width;

![image](https://github.com/user-attachments/assets/6e4308d4-9920-499a-b3b4-5139b946ec48)
