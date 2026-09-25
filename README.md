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
### Key Findings:
### 1. Spoilage risk is comparatively stable
* Mean spoilage risk is 1.1635 and median is 1.1612.
* Its low standard deviation (0.0701) indicates relatively limited variation across observations.
### 2. Vibration has substantial variability
* Median vibration is 91.47, while the mean is 277.14.
* The maximum value of 57,952.53 indicates strong right-skewness and potential extreme vibration events/outliers.
### 3. Queue time appears more interpretable than several other operational fields
* Mean queue time: 5.17
* Median queue time: 4.05
* Maximum queue time: 66.22
* The mean above the median suggests some longer-delay observations.
### 4. Days since harvest is broadly dispersed
* Mean: 1,443 days
* Median: 1,445 days
* Standard deviation: 649 days
* Since the mean and median are very close, this measure is substantially more balanced than the highly skewed sensor/operational fields.
