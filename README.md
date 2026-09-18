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
1. Analyze environmental conditions such as temperature, humidity, and vibration across cold-chain shipments.
2. Evaluate the relationship between environmental conditions and product quality/spoilage risk.
3. Identify key transportation and storage factors associated with product deterioration and shipment risk.
4. Compare commodity-wise quality and spoilage patterns to identify products that are more vulnerable during transportation.
5. Integrate commodity market-price information to assess the potential economic impact of quality deterioration and spoilage.
6. Analyze operational efficiency and costs to examine relationships among fuel consumption,fuel costs, energy consumption, operational costs,and efficiency ratio.
7. Develop an interactive Power BI decision-support dashboard to monitor shipment conditions, identify high-risk shipments, and support timely logistics decisions.

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
* **Missing values:** No missing values were identified in the dataset after preprocessing.

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
