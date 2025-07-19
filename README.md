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


## 🧰 Tools Used
#### •	Power BI Desktop
#### •	Python (Pandas for preprocessing)
#### •	Geo Mapping (PIN codes + Lat/Lon coordinates)

##📎 Files Included
#### 📂 /dashboard
#### ├── ELECT DONE.pdf                # Final Dashboard Export
#### ├── Train_with_Pin_and_Geo.csv   # Cleaned Dataset with Geolocation
#### ├── README.md                     # Project Summary


