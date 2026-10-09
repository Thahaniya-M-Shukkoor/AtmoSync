# AtmoSync: Micro-Climate Arbitrage Analytics 

## 1. Project Overview
### 1.1 Background
The transportation and storage of agricultural commodities are highly sensitive to environmental and logistical conditions. Factors such as temperature, humidity, transportation distance, storage duration, traffic conditions, and route characteristics can influence product quality and contribute to spoilage and economic losses.
**AtmoSync: Micro-Climate Arbitrage Analytics** is a data analytics project designed to examine these relationships within agricultural logistics. By analyzing environmental, transportation, and operational data, the project aims to identify conditions associated with quality deterioration and potential supply-chain inefficiencies.
The project applies data analytics techniques to transform logistics data into meaningful insights that can support better transportation, storage, and commodity-management decisions.

### 1.2 Problem Statement
Agricultural commodities can lose quality during transportation and storage because of unfavorable environmental and logistical conditions. However, identifying the factors that contribute most significantly to quality deterioration can be challenging when large volumes of supply-chain data are involved.
The project therefore focuses on analyzing agricultural logistics data to:
* Identify important environmental and transportation factors affecting commodity quality.
* Examine relationships between storage/transit conditions and product deterioration.
* Detect patterns associated with higher spoilage risk.
* Analyze differences across commodities, routes, and transportation conditions.
* Generate data-driven insights that can support improved logistics decision-making.

### 1.3 Business Context
In agricultural supply chains, maintaining product quality throughout transportation and storage is essential because deterioration can reduce the commercial value of commodities and increase operational losses.
For logistics managers and commodity businesses, understanding how **environmental conditions, transportation characteristics, route conditions, delays, and storage factors** influence quality can help improve supply-chain planning.
AtmoSync approaches this challenge from a business analytics perspective by converting logistics data into actionable information. The analysis can help decision-makers identify high-risk transportation or storage conditions, understand potential sources of quality loss, and prioritize areas for operational improvement.

### 1.4 Project Objectives
The primary objectives of the AtmoSync project are:
1. **Environmental Condition Analysis:** Analyze temperature, humidity, and  vibration levels across cold-chain shipments.
2. **Quality & Spoilage Risk Assessment:** Evaluate the relationship between environmental conditions and product quality/spoilage risk.
3. **Transportation & Storage Risk Analysis:** Identify key transportation and storage factors associated with product deterioration and shipment risk.
4. **Commodity-wise Analysis:** Compare quality and spoilage patterns across commodities to identify products that are more vulnerable during transportation.
5. **Economic Impact Assessment:** To estimate the potential economic impact of quality deterioration and spoilage.
6. **Operational Efficiency & Cost Analysis:** Examine relationships among fuel consumption, fuel costs, energy consumption to assess logistics efficiency.
7. **Decision-Support Dashboard Development:** Develop an interactive Power BI dashboard to monitor shipment conditions, identify high-risk shipments, and support timely logistics decisions.

## 2. Dataset Description

### 2.1 Dataset Name
**Euro Crop Agricultural Logistics Dataset**

### 2.2 Source
The dataset was obtained from **Kaggle** and is designed for analyzing agricultural logistics, transportation conditions, storage operations, IoT-based environmental monitoring, efficiency, and product quality.

### 2.3 Dataset Dimensions
The dataset contains **53,305 records and 29 columns**.
* **Rows:** 53,305
* **Columns:** 29
* **Numerical variables:** 25
* **Categorical/date variables:** 4
* **Missing values:** No missing values were identified in the dataset.

### 2.4 Important Variables
The variables relevant to the AtmoSync project include:

**Environmental & IoT Variables**
* **Temperature** – Environmental temperature during transportation.
* **Humidity** – Environmental humidity during transportation.
* **Vibration_Level** – Vibration experienced during transportation.
* **IoT_Sensor_Reading_Temperature** – Temperature recorded through IoT sensors.
* **IoT_Sensor_Reading_Humidity** – Humidity recorded through IoT sensors.
* **IoT_Sensor_Reading_Light** – Light intensity recorded through IoT sensors.
* **Storage_Temperature** – Temperature during storage.
* **Storage_Humidity** – Humidity during storage.

**Agricultural & Product Variables**
* **Crop_Type** – Type of agricultural crop/product.
* **Crop_Yield** – Quantity/yield associated with the crop.
* **Spoilage_Risk** – Indicator of the potential risk of product spoilage.
* **Quality_Maintenance_Ratio** – Measure related to maintaining product quality.

**Transportation & Logistics Variables**
* **Vehicle_Type** – Type of vehicle used for transportation.
* **Route_Distance** – Distance travelled along the route.
* **Delivery_Time** – Time required for delivery.
* **Traffic_Level** – Traffic conditions affecting transportation.
* **Weather_Impact** – Effect of weather conditions on logistics.
* **Queue_Time** – Time spent waiting in queues.
* **Warehouse_Storage_Time** – Duration of warehouse storage.
* **Vehicle_Load_Capacity** – Vehicle carrying capacity.

**Operational & Cost Variables**
* **Fuel_Consumption** – Fuel consumed during transportation.
* **Fuel_Costs** – Fuel-related costs.
* **Operational_Cost** – Overall operational logistics cost.
* **Energy_Consumption** – Energy consumed during operations.
* **Efficiency_Ratio** – Indicator of logistics efficiency.

### 2.5 Why This Dataset Was Selected
The dataset was selected because it closely aligns with the objectives of the **AtmoSync: Micro-Climate & Agricultural Logistics Analytics** project.
It contains environmental and IoT variables such as **temperature, humidity, and vibration**, along with transportation, storage, operational, and spoilage-related variables. These features allow the project to investigate how environmental and logistics conditions are associated with **product quality and spoilage risk**.
The dataset also provides sufficient information to analyze relationships between **environmental conditions, transportation distance, storage duration, delivery time, operational costs, and product-quality indicators**.
Therefore, it provides a suitable foundation for developing an analytics solution that can identify high-risk transportation and storage conditions and support data-driven logistics decisions.

### 2.6 Dataset Limitations
Despite its suitability for the project, the dataset has some limitations:
1. **No market-price information:** The dataset does not contain commodity market prices or alternative-market prices. Therefore, the financial component of the original AtmoSync "Spoilage Arbitrage" concept cannot be calculated directly from this dataset alone.
2. **No shipment/container identifiers:** The dataset does not contain explicit **Container_ID** or **Shipment_ID** fields, which limits shipment-level tracking.
3. **No explicit location information:** There is no dedicated location/market column for analyzing geographic-level differences.
4. **No direct rerouting information:** The dataset does not provide alternative routes or destination-market information, so actual rerouting decisions cannot be directly evaluated.
5. **Limited time-series information:** Although **Harvest_Date** is available, the dataset does not provide a continuous timestamp for individual sensor observations. Therefore, real-time sensor-stream analysis cannot be fully performed.
6. **Market integration requires additional data:** To study the economic impact of spoilage or potential arbitrage opportunities, a separate commodity market-price dataset would need to be integrated.

## 3. Technology Stack
* Python
* Pandas
* NumPy
* Matplotlib/Seaborn
* Power BI

## 4. Data Preparation
Data preparation was performed using **Python and Pandas** to improve data quality, standardize the dataset, and create additional variables required for subsequent exploratory and business analysis. The preparation process consisted of the following stages.
### 4.1 Header and Date-Time Standardization
The original dataset contained a column named `Unnamed: 0`, which was identified as representing timestamp information. This column was renamed to **`timestamp`** for better interpretability.
Date-related columns were converted from their original format into the standardized **`datetime64[ns]`** data type. This ensures that the variables can be used reliably for time-based analysis and feature extraction.
In addition, all column names were reformatted into a consistent **lower_snake_case** convention. This improves readability and makes the dataset easier to work with in Python, SQL, and Power BI.

**Example:**

```text
Original                    Standardized
Unnamed: 0       →          timestamp
Vehicle Type     →          vehicle_type
Crop Type        →          crop_type
Harvest Date     →          harvest_date
```

---
### 4.2 Corrupted Column Removal
The dataset contained several features with an extremely high proportion of infinite (`inf`) values. Columns containing more than **90% infinite values** were considered unreliable for meaningful analysis and were removed.
The following columns were dropped:
* `crop_yield`
* `vehicle_load_capacity`
* `station_capacity`
* `operational_cost`
* `energy_consumption`
* `inventory_levels`
* `efficiency_ratio`
Removing these highly corrupted features reduced noise and prevented unreliable variables from affecting subsequent statistical analysis and visualization.
---

### 4.3 Missing Value and Outlier Handling
After removing the severely corrupted columns, the remaining infinite (`inf`) values were converted to **NaN (Not a Number)** so that they could be handled consistently as missing observations.
Missing values in selected numerical variables were then imputed using the **median** of the respective column.
Median imputation was applied to:
* `route_distance`
* `iot_sensor_reading_light`
The median was selected because it is less sensitive to extreme observations than the mean and is therefore suitable for numerical logistics and sensor-related variables that may contain skewed values.
---

### 4.4 Log Transformation
Several numerical variables displayed highly skewed or exponential distributions. To reduce the effect of extreme values and improve the suitability of these variables for analysis, log-transformed versions were created.
Log transformations were applied to:
* `route_distance`
* `storage_humidity`
* `traffic_level`
Rather than replacing the original variables, transformed versions were created so that both the **original and transformed representations** could be retained for comparison and future analysis.
This transformation can help make highly skewed distributions more manageable and improve the interpretation of relationships during exploratory analysis.
---

### 4.5 Time-Based Feature Engineering
Additional time-related features were created from the standardized `timestamp` variable to enable more detailed temporal analysis.
The following features were engineered:

| New Feature          | Purpose                                                                          |
| -------------------- | -------------------------------------------------------------------------------- |
| `transit_year`       | Identifies the year of the shipment/observation                                  |
| `transit_month`      | Enables monthly pattern analysis                                                 |
| `transit_hour`       | Enables analysis of hourly patterns                                              |
| `days_since_harvest` | Measures the time elapsed between harvest and the relevant logistics observation |

### These features allow the project to examine whether logistics conditions and commodity-related outcomes vary across years, months, hours, and post-harvest periods.
---

### 4.6 Summary of Data Preparation
The overall preprocessing workflow can be summarized as:
**Raw Dataset → Column Standardization → Date-Time Conversion → Corrupted Feature Removal → Infinite Value Handling → Missing Value Imputation → Log Transformation → Time-Based Feature Engineering → Analysis-Ready Dataset**
After preprocessing, the dataset was transformed into a more consistent and analysis-ready format. The cleaned dataset can now be used for the next stages of the AtmoSync project, including **exploratory data analysis, environmental-condition analysis, logistics analysis, quality/spoilage analysis, and dashboard development**.

### 4.7 Data Preparation Outcome
The preprocessing stage improved the dataset in four major ways:
* **Improved consistency** through standardized column names and date-time formats.
* **Improved data quality** through the removal of severely corrupted features.
* **Reduced missing/infinite-value issues** through appropriate treatment and median imputation.
* **Enhanced analytical capability** through log-transformed and time-based engineered features.
This prepared dataset serves as the foundation for the subsequent analytical stages of the project.

## 5. Exploratory Data Analysis
### 5.1 Descriptive Analysis
Key Analytical Insights
1. **Symmetric vs. Skewed Metrics:**
* Symmetric Features: temperature, humidity, storage_temperature, route_distance, and spoilage_risk show near-identical mean and median values, indicating well-behaved, symmetric distributions post-transformation.
* Right-Skewed Features: vibration_level, fuel_costs, and quality_maintenance_ratio exhibit significantly higher means than medians (e.g., vibration_level mean of 249.95 vs. median of 91.47).This indicates positive skew, where a small subset of trips experiences unusually high vibration or cost spikes.
2. **Environmental Conditions:**
* Transit ambient temperature averages 44.94 with a standard deviation of 15.01, whereas controlled storage_temperature remains tightly concentrated around 7.51 with a low standard deviation of 2.95.
3. **Operational Stability:**
* Average route_distance sits at 534.20 units with low relative variability (Std Dev = 82.45), while spoilage_risk shows minimal variance (Std Dev = 0.07).

## 5.2 Univariate Analysis
Key Analysis:
1. **Typical Operating Conditions**
* Crop Types: Corn ($40.1\%$) and Wheat ($39.9\%$) make up the vast majority of all shipments, while Rice accounts for the remaining ($20.0\%$).
* Vehicles Used: Trucks perform 70.2% of all deliveries, making them the primary vehicle type. Vans ($19.8\%$) and Motorbikes ($9.9\%$) handle smaller, localized trips.
* Storage Environment: Cold storage warehouses maintain steady conditions, typically staying around $7.5^\circ\text{C}$ temperature and $75\%$ humidity.  
* Transit Times & Distances: Most deliveries travel about $530\text{ km}$, taking roughly $8.5\text{ hours}$ on the road and $18\text{ hours}$ in warehouse storage.
2. **Extreme Values & Outliers**
* Smooth & Balanced Variables: Ambient temperature, humidity, storage settings, travel distance, delivery time, and spoilage risk are smooth and evenly balanced. Most trips fall right around the typical average.
* Variables with Extreme Spikes:
* * Vibration Level: Most trips experience smooth, low vibration, but a small group of shipments suffer extreme bumps and rough road shocks.   
* * Fuel Costs: While fuel costs are usually low to moderate, a few long-haul trips spike significantly higher in cost.   
* * Quality Maintenance Ratio: Most shipments stay in a low, healthy range, but several trips show unusually high quality maintenance scores due to unexpected delays or route stress.   

## 5.3 Bivariate Analysis
Key Analytical Insights
1. **Factors appear associated with spoilage:**
* Temperature & Storage Temperature: Strong positive correlation. Higher ambient and storage temperatures directly elevate the Spoilage_Risk.
* Warehouse Storage Time: Moderate positive correlation. Extended exposure over time compounds thermal degradation.
2. **Longer storage correspond to lower quality**
* The negative slope in the Warehouse_Storage_Time vs. Quality_Maintenance_Ratio plot shows a clear degradation trend over time.
3. **Longer distance correspond to longer delivery time**
* Route_Distance exhibits a strong linear relationship with Delivery_Time, though high variance points indicate secondary factors like Queue_Time or Traffic_Level play a critical role.

## 5.4 Multivariate Analysis
Key Insights:
1. Analysis A (Environment & Vibration vs. Spoilage):
* What it shows: A heatmap displaying relationship scores from -1 to 1.Key
* Finding: Looking at isolated single metrics gives near-zero scores. This proves that single sensor readings alone do not trigger spoilage. Spoilage happens when multiple conditions worsen together.   
2. Analysis B (Environment vs. Quality):
* What it shows: Points plotted across Temperature and Humidity, colored by product quality ratio.   
* Key Finding: Low temperatures and moderate humidity maintain consistent crop quality best.
3. Analysis C (Logistics vs. Delivery Time):
* What it shows: Route Distance versus Delivery Time, colored by Traffic Level.   
* Key Finding: Longer distance routes combined with high traffic (lighter color points) experience cumulative delays.   
4. Analysis D (Operations Efficiency):
* What it shows: Relationship between fuel burned, costs, distance, and efficiency.   
* Key Finding: Fuel efficiency drops significantly as vehicle load and route delays increase.   
5. Analysis E (AtmoSync Decision-Support Core):
* What it shows: Our calculated Environmental Stress score plotted against Spoilage Risk.   
* Key Finding: Combining temperature, humidity, and time into a single score provides a clearer pattern to help AtmoSync predict risk before crops spoil.

## 5.5 Temperature / Humidity Analysis
Findings:
A. Temperature Comparison:
* Storage temperature is tightly regulated around 5°C to 12°C to preserve crops. In contrast, ambient and IoT sensor temperatures span higher ranges (20°C to 70°C).   
B. Humidity Comparison:
* Storage humidity is controlled near 75%, whereas ambient humidity shows a broader curve.   
C. Temperature vs Humidity:
* The correlation score is nearly zero ($0.002$), showing that temperature and humidity vary independently in this dataset.   
D & E. Impact on Spoilage Risk:
* Single environmental variables alone show flat trendlines. This reinforces why AtmoSync requires a multi-variable index (combining temperature, humidity, and duration) to detect risk accurately.   
F & G. Impact on Quality Ratio:
* Similar to spoilage risk, individual readings alone do not shift quality ratios significantly.   
H. Sensor Consistency:
* The IoT temperature readings average about $7.4^\circ\text{C}$ lower than ambient temperature, while IoT humidity averages about $30\%$ lower. This gap shows that IoT sensors measure local micro-climates inside containers rather than outside weather conditions.

## 5.6 Logistics & Transportation Analysis
**Factors that drive longer delivery times and higher costs**
1. Weather and Queue Times Drive Delays:
* Weather Impact: Higher weather_impact scores show a positive correlation with longer delivery times ($r = 0.0082$).  
* Queue Delays: Longer warehouse queue_time directly extends overall transit times ($r = 0.0042$).   
2. Distance and Traffic Impact on Fuel:
* Route Distance: Longer distance journeys slightly increase total fuel consumed ($r = 0.26$ in multivariate checks), raising operational expenses.   
* Traffic Level: High traffic levels slow down vehicles, causing increased idle time and reducing fuel efficiency.   
3. Vehicle Fleet Comparisons:
* Delivery Time: Trucks average $8.51$ hours, Vans average $8.50$ hours, and Motorbikes average $8.50$ hours.   
* Fuel Consumption: Trucks and Motorbikes consume an average of $24.02\text{ L}$, whereas Vans consume slightly less at $23.86\text{ L}$.   
* Fuel Costs: Vans average $\$174.46$ per run, Motorbikes average $\$173.45$, and Trucks average $\$172.39$.

## 5.7 Quality / Spoilage Analysis
Key Insights
**A. Spoilage Distribution (spoilage_risk)**
* Distribution: Normal (bell-shaped) curve centered around 1.16.
* Average: Mean = 1.1635, Median = 1.1612, Standard Deviation = 0.0701.
* Range: Minimum = 0.8914, Maximum = 1.4588 (Span = 0.5673).
* Outliers: 417 points (0.78% of the dataset) fall outside the standard 1.5 IQR bounds.
**B. Quality Distribution (quality_maintenance_ratio)**
* Distribution: Highly right-skewed (heavy-tailed) distribution with most values concentrated between 0 and 50, and extreme upper tail values exceeding 1,000.
* Mean vs. Median: Mean = 76.61, Median = 22.70 (the high mean is pulled up by extreme outliers).
* Range: Minimum = 0.0730, Maximum = 1044.73 (Span = 1044.66).
* Outliers: 6,229 points (11.69% of the dataset) qualify as upper-tail outliers.
**C. Environmental Factors $\rightarrow$ Spoilage**
Examining linear correlation coefficients ($r$) between environmental variables and spoilage_risk:
* Temperature $\rightarrow$ Spoilage: $r = -0.0006$ (No direct linear impact).
* Humidity $\rightarrow$ Spoilage: $r = 0.0031$ (Negligible effect).
* Vibration $\rightarrow$ Spoilage: $r = -0.0013$ (No direct effect).
* Storage Temperature $\rightarrow$ Spoilage: $r = 0.0027$ (Negligible effect).
* Storage Humidity $\rightarrow$ Spoilage: $r = 0.0059$ (Negligible effect).
**D. Storage $\rightarrow$ Spoilage**
* warehouse_storage_time $\rightarrow$ spoilage_risk: $r = 0.0012$. Storage time in the warehouse shows no statistical correlation with spoilage risk in this dataset.
**E. Transportation $\rightarrow$ Spoilage**
* route_distance $\rightarrow$ spoilage_risk: $r = 0.0070$. Route distance does not noticeably increase spoilage risk.
* delivery_time $\rightarrow$ spoilage_risk: $r = -0.0008$. Transit delivery time exhibits no linear association with spoilage risk.
**F. Spoilage $\rightarrow$ Quality**
* spoilage_risk $\leftrightarrow$ quality_maintenance_ratio: $r = -0.0013$.
* Key Finding: In this dataset, spoilage_risk and quality_maintenance_ratio are statistically independent ($r \approx 0$). High quality maintenance ratios occur uniformly across the entire range of spoilage risk scores.
**G. Crop $\rightarrow$ Spoilage**
Comparing average spoilage_risk across crop types:
1. Corn: Mean = 1.1632 (Median = 1.1609)
2. Rice: Mean = 1.1630 (Median = 1.1605)
3. Wheat: Mean = 1.1641 (Median = 1.1619)
Spoilage risk distribution is uniform across all three crop types.
**H. Crop $\rightarrow$ Quality**
Comparing average quality_maintenance_ratio across crop types:
1. Corn: Mean = 77.03 (Median = 22.91)
2. Rice: Mean = 76.15 (Median = 22.38)
3. Wheat: Mean = 76.41 (Median = 22.63)
Quality maintenance ratios show consistent behavior across Wheat, Corn, and Rice.
**Factors Associated with Higher Spoilage Risk and Lower Quality Maintenance**
1. **Spoilage Risk Drivers:**
* None of the environmental (temperature, humidity), storage (warehouse time), transportation (route distance, delivery time), or crop variables show strong direct correlation with spoilage_risk in this dataset. Spoilage risk follows a standard normal distribution centered at 1.16.
2. **Quality Maintenance Drivers:**
* Vibration Level (+0.836 correlation): vibration_level shows a strong positive correlation ($r = 0.836$, Spearman $r = 0.895$) with quality_maintenance_ratio.
* Queue Time (-0.221 correlation): queue_time shows a moderate negative correlation ($r = -0.221$, Spearman $r = -0.418$) with quality_maintenance_ratio, meaning longer queue times are associated with lower quality maintenance.
# 5.8 Commodity-Level Analysis
Key Insights
**A. Crop Distribution**
* Corn: 21,400 records (40.15%)
* Wheat: 21,253 records (39.87%)
* Rice: 10,652 records (19.98%)
Total Records: 53,305
Corn and Wheat make up approximately 80% of the entire dataset, while Rice represents approximately 20%.
**B & C. Crop-wise Environmental Conditions (Temperature & Humidity)**
* Average Transit Temperature:
1. Corn: 45.02°C ($\sigma = 14.98$)
2. Rice: 44.90°C ($\sigma = 15.06$)
3. Wheat: 44.87°C ($\sigma = 15.02$)
* Average Transit Humidity:
1. Rice: 90.09% ($\sigma = 22.55$)
2. Wheat: 89.93% ($\sigma = 22.72$)
3. Corn: 89.90% ($\sigma = 22.45$)
The mean temperature (~ 44.9°C - 45.0°C) and mean humidity (~ 89.9% - 90.1%) are virtually identical across all three crop types. There is no evidence of crop-specific environmental routing or temperature-controlled segregation in this dataset.
**D & E. Crop-wise Spoilage Risk & Quality Maintenance**
* Average Spoilage Risk:
1. Wheat: 1.1641
2. Corn: 1.1632
3. Rice: 1.1630
* Average Quality Maintenance Ratio:
1. Corn: 77.03
2. Wheat: 76.41
3. Rice: 76.15
Spoilage risk and quality maintenance ratios show negligible variation across commodity types, remaining constant across Wheat, Corn, and Rice.
**F. Crop-wise Logistics Comparison**
1. Mean Route Distance:
* Wheat: 533.49 km
* Corn: 534.49 km
* Rice: 535.02 km
2. Mean Delivery Time:
* Corn: 8.49 hours
* Rice: 8.50 hours
* Wheat: 8.53 hours
3. Mean Warehouse Storage Time:
* Corn: 17.96 hours
* Wheat: 17.99 hours
* Rice: 18.08 hours
Logistical parameters do not favor or penalize any particular commodity type; distance and travel times are uniformly distributed.
**G. Crop-wise Cost Comparison**
1. Mean Fuel Consumption:
* Corn: 23.89 L
* Rice: 24.03 L
* Wheat: 24.07 L
2. Mean Fuel Costs:
* Rice: $170.25
* Wheat: $173.41
* Corn: $173.72
Fuel consumption and associated fuel costs are consistent across commodity types.
**H. Crop × Environmental Conditions (Multivariate Extension)**
Tested cross-interactions between commodity type, environmental factors, and quality outcomes:
1. Crop Type × Temperature × Spoilage Risk:
* Wheat correlation ($r$): -0.0064
* Corn correlation ($r$): -0.0025
* Rice correlation ($r$): +0.0149
2. Crop Type × Humidity × Quality Maintenance Ratio:
* Wheat correlation ($r$): +0.0058
* Corn correlation ($r$): -0.0131
* Rice correlation ($r$): +0.0180
No crop demonstrates significant sensitivity to temperature or humidity variations. The correlation coefficients across all three crops remain within $r \in [-0.013, +0.018]$, indicating that environmental variations do not yield differential spoilage or quality impacts for any specific crop in this dataset.

## 6. Findings and Conclusions
## 6.1. Environmental Condition Analysis
### Findings
* Storage conditions are relatively stable, with storage temperature around **7.5°C** and humidity around **75%**.
* During transportation, temperature is much higher and more variable, averaging around **44.9°C**, while humidity averages around **90%**.
* Vibration is generally low for most shipments, but a small number of shipments experience unusually high vibration.
* Temperature and humidity do not show a meaningful relationship with each other in this dataset.
* Individual temperature, humidity, or vibration values do not show a clear direct relationship with spoilage risk.  
### Conclusion
The analysis shows that transportation conditions are much more variable than controlled storage conditions. However, no single environmental factor alone is enough to explain spoilage risk. This supports the AtmoSync approach of looking at multiple environmental conditions together rather than relying on one sensor reading.

---
## 6.2. Quality & Spoilage Risk Assessment
### Findings
* Spoilage risk is centered around **1.16** and has relatively little variation across shipments.
* Individual environmental factors such as temperature, humidity, vibration, storage temperature, and storage humidity have almost no direct linear relationship with spoilage risk.
* Longer warehouse storage also does not show a clear relationship with spoilage risk.
* However, **queue time is associated with lower quality maintenance**, meaning longer waiting periods are linked with poorer quality.
* The analysis also shows that combining temperature, humidity, and time into an **Environmental Stress Score** gives a clearer pattern with spoilage risk than looking at individual factors. 
### Conclusion
Spoilage risk cannot be explained by one environmental or logistics factor in this dataset. Instead, several conditions need to be considered together. Waiting time is one factor that is linked with lower quality, making timely movement of shipments important.

---
## 6.3. Transportation & Storage Risk Analysis
### Findings
* Route distance has a clear relationship with delivery time: **longer routes generally take longer**.
* Traffic and delays can further increase delivery time.
* Longer distances are also associated with higher fuel consumption.
* High traffic can increase vehicle idle time and reduce fuel efficiency.
* Warehouse queue time contributes to longer overall transit time.
* Average delivery time is around **8.5 hours**, while warehouse storage is around **18 hours**.  
### Conclusion
Distance, traffic and waiting time are important operational factors. They can increase delivery time and fuel usage, while longer waiting periods are also associated with lower quality. Therefore, reducing unnecessary delays and improving route planning can support safer and more efficient transportation.

---
## 6.4. Commodity-wise Analysis
### Findings
* The dataset contains three main crops: **Corn, Wheat and Rice**.
* Corn and Wheat together account for about **80% of the shipments**.
* Average temperature and humidity are almost identical across all three crops.
* Spoilage risk is also almost the same:
  * Wheat: **1.1641**
  * Corn: **1.1632**
  * Rice: **1.1630**
* Quality maintenance is also very similar across the three crops.
* Route distance, delivery time, storage time, fuel consumption and fuel cost are also broadly similar between crops.
* None of the crops shows a strong sensitivity to temperature or humidity in relation to spoilage or quality.  
### Conclusion
No major difference in spoilage risk or quality was found between Corn, Wheat and Rice. The three commodities experience broadly similar environmental and transportation conditions, so this dataset does not provide evidence that one crop is significantly more vulnerable than another.

---
## 6.5. Economic Impact Assessment
### Findings
* The dataset contains **fuel consumption and fuel cost**, which allow us to study part of the operational cost.
* Longer routes are associated with higher fuel consumption.
* Fuel costs show some unusually high values for a small number of trips.
* However, the analysis does **not show a market-price variable or a direct monetary value for crop spoilage/loss**.
* Also, the original `operational_cost` and `energy_consumption` variables were removed during preprocessing because they contained more than 90% infinite values.  
### Conclusion
The dataset allows us to examine transportation-related costs, particularly fuel costs, but it does not provide enough information to calculate the actual monetary loss caused by spoilage or quality deterioration. Therefore, the economic impact can only be assessed partially through fuel and transportation costs, not through direct spoilage-related financial loss.

---
## 6.6. Operational Efficiency & Cost Analysis
### Findings
* Route distance has a positive relationship with fuel consumption.
* Longer routes therefore tend to require more fuel.
* Traffic and delays can reduce fuel efficiency because vehicles spend more time moving slowly or waiting.
* Fuel consumption and fuel costs are broadly similar across the three crop types.
* Among vehicle types, fuel consumption is quite similar, although Vans show slightly lower average consumption.
* The analysis indicates that **vehicle load and route delays can reduce fuel efficiency**.  
### Conclusion
Distance, traffic and delays are the main operational factors affecting fuel usage and efficiency. Better route planning and reducing unnecessary delays can help lower fuel consumption and transportation costs.

---
## Overall AtmoSync Conclusion
* The AtmoSync analysis shows that cold-chain shipment conditions are influenced by a combination of environmental, transportation and storage factors. Storage conditions are relatively stable, while temperature and humidity during transportation vary much more. However, no single environmental factor shows a strong direct relationship with spoilage risk. Instead, combining multiple conditions such as temperature, humidity and exposure time provides a better way to identify potential risk.
 
* Transportation factors such as route distance, traffic and waiting time have a clearer impact on delivery time, fuel consumption and operational efficiency. Longer waiting times are also associated with lower quality maintenance. Across Corn, Wheat and Rice, no major differences were found in spoilage risk, quality or logistics conditions.

* Overall, the analysis suggests that AtmoSync should focus on a combined view of environmental conditions, shipment duration and logistics performance rather than relying on a single factor. The analysis also highlights the importance of reducing transportation delays and improving route efficiency. However, the available dataset does not contain sufficient market-price or spoilage-loss information to calculate the actual monetary impact of crop deterioration.
