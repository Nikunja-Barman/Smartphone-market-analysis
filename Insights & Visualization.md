# Unlocking Smartphone Market Trends: A Data-Driven Analysis 🕵👨‍💻

## 🎯Project Overview:
This Power BI project analyzes smartphone sales data to uncover key market trends and consumer insights. The goal was to create an interactive dashboard that visualizes crucial metrics like brand pricing, 5G adoption, and feature-to-customer satisfaction correlations (e.g., charging speed, cameras). This analysis provides actionable intelligence to guide strategic decisions in smartphone product development, marketing, and competitive strategy.

## ❓Problem Statement:
This project aimed to conduct a comprehensive analysis of smartphone sales data to identify critical market trends, understand consumer preferences, and derive actionable insights. The primary goal was to develop an interactive Power BI dashboard that empowers stakeholders to quickly grasp key performance metrics, pricing dynamics, feature prevalence, and competitive positioning within the smartphone market, ultimately informing strategic decisions for product development, pricing, and marketing.

## 🔑What I did;
●  Data Cleaning & Transformation: Utilized SQL for initial data querying and cleaning, followed by Power Query in Power BI for robust data transformation and preparation. 

●  Data Visualization: Created intuitive and impactful visual representations to effectively communicate complex smartphone market trends and relationships. 

●  Dashboard Design Principles: Applied best practices in dashboard design to ensure clarity, interactivity, and a user-friendly experience for data exploration. 

●  Statistical Analysis (basic level): Performed basic statistical analysis, such as identifying averages, correlations, and distributions to derive meaningful insights from the sales data. 

●  Business Acumen: Translated raw data points into actionable business recommendations, demonstrating an understanding of market dynamics and strategic implications. 

●  Communication of Insights: Clearly articulated key findings, trends, and recommendations derived from the data analysis, making complex information accessible to stakeholders.

## 🔎Key Visualizations & Insights:
### 1. Top Bar: Key Performance Indicators (KPIs)

➤	What it Shows: 
A summary of key metrics: Common Core (8-Octa core), Common Battery (5000mAh), Avg. Fast Charging (36W), Percent 5G (56%), 5G Status (Avg Price: $43,200.49), Not 5G (Avg Price: $18,916.53), Most Common Processor (Snapdragon 413).

➤	Key Insights: 
o	The market shows a strong preference for octa-core processors and 5000mAh batteries.
o	5G phones command a significantly higher average price than non-5G phones (more than double).
o	Over half of the current market (56%) is 5G enabled, indicating a strong adoption rate.
o	Snapdragon 413 is the most prevalent processor.

➤	Business Implication/Actionable Insight: 
o	Product Development: Manufacturers should prioritize octa-core processors and 5000mAh batteries for new models.
o	Pricing Strategy: 5G capability is a major value driver, justifying premium pricing. Businesses can leverage this for higher margins.
o	Market Trend: The rapid adoption of 5G suggests an increasingly tech-savvy customer base willing to pay for advanced features.
o	Inventory Management: Focus on stocking phones with the Snapdragon 413 or similar popular processors.

![image](https://github.com/user-attachments/assets/f9411ded-59fb-4b8a-81f3-f576c8384aa5)

### 2. Average Price by Brand (Bar Chart)

➤	What it Shows: A bar chart displaying the average price of smartphones for various brands, sorted in descending order.

➤	Key Insights: 
o	Vertu and Royole command exceptionally high average prices, indicating a luxury or niche market.
o	Mainstream brands like Apple, Huawei, and Asus have significantly lower average prices, suggesting a broader market appeal.
o	LG, and Tesla have the lowest average prices.

➤	Business Implication/Actionable Insight: 
o	Market Positioning: Brands like Vertu and Royole should continue targeting premium segments with unique value propositions.
o	Competitive Analysis: For mainstream brands, this chart provides a benchmark for pricing strategies relative to competitors.
o	Target Market Identification: Different brands appeal to different price segments. Businesses can use this to refine their marketing and sales efforts.
o	Product Portfolio Optimization: Lower-priced brands might need to re-evaluate their value proposition or explore premium segments if profitability is a concern.

![image](https://github.com/user-attachments/assets/00cf2d83-f323-4d9b-a2e3-3bb943d92fd6)

### 3. Processor & 5G Status (Pie Chart)

➤	What it Shows: A donut chart showing the distribution of processors, with a clear distinction between 5G and non-5G devices. Snapdragon (with 35.63% 5G status phone), Bionic (51.72% 5G status phone), Kirin (with 8.05% 5G status phone), etc.

➤	Key Insights: 
o	Bionic processors dominate the 5G market share (51.72%), followed closely by Snapdragon (35.63%).
o	Kirin has a relatively small 5G market share.

➤	Business Implication/Actionable Insight: 
o	Supply Chain & Sourcing: Understanding processor market share helps in negotiating with chip manufacturers and ensuring a stable supply.
o	Product Development: Companies can align their product development with popular processor choices or identify gaps for niche processors.
o	Competitive Intelligence: Knowing competitor processor usage helps in strategic planning.

![image](https://github.com/user-attachments/assets/7a6f19dc-7e2e-48ee-9ff0-3cdf97fdc660)

### 4. Charging Range & Rating (Column Chart)

➤	What it Shows: A column chart showing the average customer rating for different charging ranges (Less than 30W, 30-59W, 60+W).

➤	Key Insights: 
o	Phones with ‘Less than 30W’ charging have the highest average rating (7.37).
o	Phones with ‘60+W’ charging also have a strong average rating (7.06).
o	"30-59W" charging has a noticeably lower average rating (4.96).

➤ Business Implication/Actionable Insight: 
o	Product Feature Prioritization: ‘Less than 30W’ charging is a highly valued feature by customers and directly impacting customer satisfaction. Higher charging range are gaining less popularity among customer which seems a peculiar case and need further in-depth analysis..
o	Research & Development: Urgent need of invest in improving charging technology is necessary to enhance customer experience and ratings.
o	Competitive Advantage: Offering superior charging speeds can give a competitive edge.

![image](https://github.com/user-attachments/assets/3050ad42-944d-4cc9-bd83-2609ef9d06c5)

### 5. Resolution & Price (Scatter Plot)

➤	What it Shows: A scatter plot displaying smartphone resolution (width vs. height) against price, with each point representing a phone model.

➤	Key Insights: 
o	There appears to be a general positive correlation: higher resolution tends to correlate with higher prices, especially at the higher end of the resolution spectrum.
o	Some very high-resolution phones are also very expensive, indicating a premium for top-tier displays.

➤	Business Implication/Actionable Insight: 
o	Product Strategy: Companies can decide on target resolution ranges based on their desired price segment. High-end phones can justify premium displays.
o	Value Proposition: For mid-range phones, finding an optimal resolution that balances cost and customer satisfaction is key.
o	Market Segmentation: Different resolution requirements cater to different user needs (e.g., professional users, gamers, casual users).

![image](https://github.com/user-attachments/assets/3216c9f5-6a5a-4f7f-8583-fe03a898bc07)

### 6. Processor & Cores Comparison (Bubble Chart)

➤	What it Shows: A bubble chart comparing different processors based on the "Average Rating" along Y-axis and perhaps another metrics viz. “Num_cores” in Legend and “Average speed of processor” in Bubble size .

➤	Key Insights: 
o	"Dimensity” processors appear to have the highest average ratings with Octa-core processor.
o	"Snapdragon", "unisoc", “tiger”, “helio” have a wide range of ratings.
o	"Dimensity" and “kirin” appears to be best processor with best “Avg-rating”, “octa-core” and best “Average speed of the processor” in the whole range.

➤	Business Implication/Actionable Insight: 
o	Component Sourcing: When selecting processors, consider not just performance but also their impact on overall customer satisfaction (as reflected in ratings).
o	Product Quality: High-rated processors contribute to better overall product perception.
o	Market Intelligence: Understanding which processors resonate well with users helps in making informed decisions about future product lines.

![image](https://github.com/user-attachments/assets/daed5150-e178-4397-bf06-90b21777994a)

### 7. Battery Capacity & Rating (Matrix/Table)

➤	What it Shows: A matrix displaying average ratings for different battery capacities (e.g., 1821mAh, 2050mAh, 2230mAh to 4600mAh, 5000mAh, 6000mAh) across various brands. 

➤	Key Insights: 
o	‘Leitz’ with 5000 mAh of battery has the highest ‘Avg rating of  9’ followed by ‘Sharp’ with 3730 mAh of battery with ‘Avg rating of  9’ and then ‘Lenovo’ with 5000-5600 mAh battery with ‘Avg rating of 9’.
o	Some brands consistently receive lower ratings across all displayed battery capacities (e.g., 'sony', 'asus').

➤	Business Implication/Actionable Insight: 
o	Product Development: Identify optimal battery capacities that lead to higher customer satisfaction for specific brands or product lines.
o	Brand Performance: Analyze how battery performance impacts brand perception and ratings.

![image](https://github.com/user-attachments/assets/1f53199f-1b1b-43e6-ab66-e0009dfddbee)

### 8. Camera vs Price vs Rating (Line Chart)

➤	What it Shows: A line graph displaying the average price and average rating of smartphones based on the number of rear cameras.

➤	Key Insights: 
o	Both average price and average rating generally increase with the number of rear cameras, peaking at 3 rear cameras.
o	Phones with 3 rear cameras have the highest average rating (around 7.5) and are among the highest in average price (over 35K).
o	While the average price continues to rise slightly for 4 rear cameras, the average rating starts to decline, suggesting diminishing returns on customer satisfaction beyond 3 cameras.
o	Phones with 1 or 2 rear cameras have significantly lower average prices and average ratings compared to those with 3 or 4.

➤	Business Implication/Actionable Insight: 
o	Product Development: Consider focusing on 3 rear cameras for a strong balance of price and customer satisfaction. Adding a fourth camera might increase cost without a proportional increase in user rating.
o	Pricing Strategy: A higher number of rear cameras (up to 3) allows for premium pricing.

![image](https://github.com/user-attachments/assets/ef8ba85a-667a-4fcc-86f0-c975b9ebe9be)

### 9. RAM vs Price vs Rating (Line & Column Chart)

➤	What it Shows: A column chart showing the average price and a line graph showing the average rating of smartphones based on their RAM capacity.

➤	Key Insights: 
o	There isn't a direct linear relationship between RAM capacity and average price or average rating.
o	Smartphones with 18GB of RAM command the highest average price (close to 90K) along with highest average rating of around 9.
o	RAM capacities of 8GB and 6GB show relatively high average ratings (around 8-8.5) despite having moderate average prices.
o	Lower RAM capacities (e.g., 1GB, 2GB, 3GB, 4GB) generally correspond to much lower average prices and significantly lower average ratings.
o	There's a noticeable drop in both average price and average rating for RAM capacities of 2GB and 1GB.

➤	Business Implication/Actionable Insight: 
o	Product Development: Consider offering smartphones with 8GB or 6GB RAM for a good balance of performance, customer satisfaction, and competitive pricing.
o	Pricing Strategy: While very high RAM (12GB) can justify a premium price, it may not necessarily translate to the highest customer satisfaction.
o	Target Market Identification: Phones with lower RAM capacities (1GB-4GB) likely cater to a budget-conscious segment, but businesses should be aware of the lower customer satisfaction associated with these models.
o	Marketing & Sales: Highlight RAM capacities like 8GB and 6GB as they appear to be highly valued by users.

![image](https://github.com/user-attachments/assets/3c586ffb-4f83-4607-9d33-f7ce9109db19)

## 🛠 Tools & Technologies used:
● Excel: For initial data understanding

● SQL: For Data cleaning and initial insights drawing 

● Power BI Desktop: For data import (Power Query), for DAX measures, visualization and dashboard design.

● Power BI Service: For publishing and sharing the interactive report.
.
## 💡𝗞𝗲𝘆 𝗧𝗮𝗸𝗲𝗮𝘄𝗮𝘆𝘀:
📍Developed end-to-end Power BI dashboards, providing actionable insights into smartphone market trends, pricing strategies, and customer preferences. 

📍Leveraged Excel for initial data understanding, SQL for robust data cleaning and initial insights drawing, and Power BI for advanced data import (Power Query), comprehensive data modeling (including Star Schema design), and complex DAX measures. 

📍Translated raw smartphone data into clear business implications and actionable recommendations, such as prioritizing specific core processors and battery capacities, optimizing 5G pricing, and identifying optimal camera and RAM configurations for enhanced customer satisfaction. 

📍Analyzed diverse smartphone market metrics, including key performance indicators (KPIs), average price by brand, processor and 5G status distribution, charging range ratings, resolution-price correlation, and the impact of camera count and RAM capacity on price and user ratings.



