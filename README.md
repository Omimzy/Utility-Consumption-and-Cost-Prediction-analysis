# Utility-Consumption-and-Cost-Prediction-analysis
This project focuses on analyzing and predicting utility consumption patterns—primarily electricity and water usage across various neighborhoods and structure types in Bangalore, India.
## 🔍 Project Overview
#### This project analyzes utility consumption patterns specifically electricity and water usage across different neighborhoods (Site Areas) and structure types in Bangalore, India. The data visualized in Power BI reveals usage efficiency, cost hotspots, and sustainability metrics for better decision-making in urban infrastructure planning and also a cost prediction for the consumption of Electricity using Python.

## Dataset
#### •	Source: [Simulated Utility Dataset - Bangalore]
#### •	Records: 11,220 rows
#### •	Fields include:
##### o	Site_Area, Structure_Type,
##### o	Water_Consumption_Per_Building, Electricity_Cost,
##### o	Resident_Count, Air_Quality_Index, Utilization_Rate, etc.

## 📌 Key Performance Indicators (KPIs)
#### Metric	                   -                 Value
#### Average Electricity Cost	      -        18,000
#### Average Water Consumption	      -      673 units/building
#### Total Resident Count	           -       716,000
#### Average Air Quality Index	     -       48 (Moderate)

## Location Insight (by Site Area)
### Top 5 Areas by Electricity Cost:
#### 1.	HSR Layout – 18.2K
#### 2.	Yelahanka – 18.1K
#### 3.	Jayanagar – 18.1K
#### 4.	Banashankari – 17.9K
#### 5.	Whitefield – 17.8K
### Lowest:
#### •	Electronic City – 17.5K (despite being a tech hub)

##  KPI QUERY 
```
---Electricity Cost by Structure
SELECT Structure_Type, ROUND(AVG(Electricity_Cost), 3) AS Avg_Electricity_Cost
FROM train
GROUP BY Structure_Type

---List top 5 areas with highest average recycling rate.
SELECT TOP 5 Site_Area, ROUND(AVG(Recycling_Rate),3) AS MAX_Recycling_rate 
FROM Train
GROUP BY Site_Area

--- Identify buildings where water usage > 1000 but electricity cost < 10,000.

SELECT 
	Site_Area, Water_consumption_per_building, 
	electricity_cost
FROM Train
WHERE 
	Water_consumption_per_building > 1000 
AND 
	electricity_cost < 10000
GROUP BY 
	Site_Area, Water_consumption_per_building, 
	electricity_cost

--- Correlate 'Utilization_Rate' and 'Electricity_Cost' per site.

SELECT
    Site_Area,
    -- Pearson Correlation Coefficient Formula
    SUM((Utilization_Rate - AvgUtil) * (Electricity_Cost - AvgCost)) /
    NULLIF(
        SQRT(SUM(POWER(Utilization_Rate - AvgUtil, 2))) * 
        SQRT(SUM(POWER(Electricity_Cost - AvgCost, 2))),
        0
    ) AS Correlation_Coefficient
FROM (
    SELECT *,
 -- Calculate mean per Site_ID
        AVG(Utilization_Rate) OVER (PARTITION BY Site_Area) AS AvgUtil,
        AVG(Electricity_Cost) OVER (PARTITION BY Site_Area) AS AvgCost
    FROM Train
) AS SubQuery
GROUP BY Site_Area;


--- Count buildings with air quality index > 100.
SELECT COUNT(Site_Area) AS Building_Count
FROM
(
	SELECT Site_Area, air_quality_index 
	FROM Train
	WHERE air_quality_index > 100
) AS FilteredData;
```
## Analytical Insight
### ⚡ Electricity Cost vs Structure Type
#### •	Industrial & Commercial buildings have the highest cost, followed by Residential and Institutional.
### 💧 Water Consumption
#### •	Uniform across sites (~0.6K–0.7K units), suggesting efficient baseline usage citywide.
### 🌍 Environmental Observation
#### •	Average AQI = 48: Indicates moderately healthy air, though areas like Indiranagar may need targeted environmental policies.
### 📈 Cost vs Consumption Correlation
#### •	Positive trend between electricity cost and consumption rate (640–720 units) indicates predictable load, with potential for demand optimization.


## Dashboard Features
#### •	Dynamic filters for Structure Type and Site Area
#### •	Map Visualization of electricity usage by location
#### •	Cost breakdowns by type and location
#### •	Scatter plots for consumption analysis
#### •	KPI cards for executive-level overview



## 📌 Recommendations
#### •	🎯 Target Whitefield & Koramangala for energy optimization
#### •	🌱 Consider sustainability programs in high-density residential zones
#### •	🧪 Further analysis with weather and real-time grid data can improve planning


# COST PREDICTION WITH PYTHON
```
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_squared_error, r2_score
import numpy as np

# 1. Load and prepare data
df = pd.read_csv(r"/content/Train.csv")  # Raw string to avoid backslash issues
X = df[['Resident_Count', 'Water_Consumption_Per_Building', 'Utilization_Rate', 'Air_Quality_Index']]
y = df['Electricity_Cost']

# 2. Train/test split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# 3. Train model
model = RandomForestRegressor()
model.fit(X_train, y_train)

# 4. Predict
y_pred = model.predict(X_test)

# 5. Evaluate
mse = mean_squared_error(y_test, y_pred)
rmse = np.sqrt(mse)
print("RMSE:", rmse)
print("R²:", r2_score(y_test, y_pred))

# Convert test results to DataFrame
results = pd.DataFrame({
    'Actual': y_test,
    'Predicted': y_pred
})

# View top 10
print(results.head(10))

import matplotlib.pyplot as plt
import pandas as pd

# Step 1: Combine actual and predicted into a DataFrame
results = pd.DataFrame({
    'Actual': y_test.values,
    'Predicted': y_pred
})

# Step 2: Reset index for plotting
results = results.reset_index(drop=True)

# Step 3: Plot
plt.figure(figsize=(12, 6))
plt.plot(results['Actual'], label='Actual', color='blue')
plt.plot(results['Predicted'], label='Predicted', color='red')
plt.title('Electricity Cost Prediction - Actual vs Predicted')
plt.xlabel('Sample Index')
plt.ylabel('Electricity Cost')
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()


```


## 🧰 Tools Used
#### •	Power BI Desktop
#### •	Python (Pandas for preprocessing)
#### •	Geo Mapping (PIN codes + Lat/Lon coordinates)
#### .  EXCEL
#### .  SQL SERVER

## Files Include
#### 📂 /dashboard
#### ├── ELECT DONE.pdf                # Final Dashboard Export
#### ├── Train_with_Pin_and_Geo.csv   # Cleaned Dataset with Geolocation
#### ├── README.md                     # Project Summary


