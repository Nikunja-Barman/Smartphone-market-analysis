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


