# Carbon Emission Analysis
## 1. Introduction

![image](https://github.com/user-attachments/assets/ab401dcd-3f98-4175-a63a-3c1875067eb9)

Photo by Chris LeBoutillier (unsplash.com)

This report aims to analyze carbon emissions to examine the carbon footprint across various industries. We aim to identify sectors with the highest levels of emissions by analyzing them across countries and years, as well as to uncover trends.

Carbon emissions play a crucial role in the environment, accounting for over 75% of global emissions and posing a significant environmental challenge. These emissions contribute to the accumulation of greenhouse gases in the atmosphere, leading to climate change, planetary warming, and involvement in various environmental disasters.

Through this analysis, we hope to understand the environmental impact of different industries and contribute to making informed decisions in sustainable development.

### 1.1. Data Source
Our dataset is compiled from publicly available data from nature.com and encompasses the product carbon footprints (PCF) for various companies. PCFs represent the greenhouse gas emissions associated with specific products, quantified in CO2 (carbon dioxide equivalent).

### 1.2. Data Model
The dataset consists of 4 tables containing information regarding carbon emissions generated during the production of goods.

![image](https://github.com/user-attachments/assets/6d8aec6d-739f-4a72-b57d-27728c1cafc3)

### 1.3. Data Structure
**Tables' columns description**
**Table 'product_emissions'**
1. id: Identifier for each product emission record.
2. company_id: Identifier for the company associated with the product.
3. country_id: Identifier for the country where the product is being produced.
4. industry_group_id: Identifier for the industry group to which the product belongs.
5. year: The year in which the emissions data was recorded.
6. product_name: The name of the product associated with the emissions data.
7. weight_kg: The weight of the product in kilograms.
8. carbon_footprint_pcf: The carbon footprint of the product, measured in CO2 equivalent.
9. upstream_percent_total_pcf: The percentage of the total carbon footprint attributed to upstream activities.
10. operations_percent_total_pcf: The percentage of the total carbon footprint attributed to operations.
11. downstream_percent_total_pcf: The percentage of the total carbon footprint attributed to downstream activities.

**Table 'industry_groups'**
1. id: Unique identifier for each industry group.
2. industry_group: The name of the industry group, categorizing businesses within similar sectors based on their products or services offered.

**Table 'countries'**
1. id: Unique identifier for each country.
2. country_name: The name of the country.

## 2. Data explores
**Data duplicated**
```SQL
SELECT 
	*,
	COUNT(*) AS "duplicated_count"
FROM product_emissions
GROUP BY 
	id,
	company_id,
	country_id,
	industry_group_id ,
	year,
	product_name,
	weight_kg,
	carbon_footprint_pcf,
	operations_percent_total_pcf,
	downstream_percent_total_pcf
;
```
**Duplicated result**

## 3. Data analysis
### 3.1. Which products contribute the most to carbon emissions?

```SQL
SELECT
	product_name,
	ROUND(AVG(carbon_footprint_pcf),2) AS "Average PCF"
FROM	product_emissions
GROUP BY product_name
ORDER BY carbon_footprint_pcf DESC
LIMIT 10;
```


| product_name                                                                                                                       | Average PCF | 
| ---------------------------------------------------------------------------------------------------------------------------------: | ----------: | 
| Wind Turbine G128 5 Megawats                                                                                                       | 3718044.00  | 
| Wind Turbine G132 5 Megawats                                                                                                       | 3276187.00  | 
| Wind Turbine G114 2 Megawats                                                                                                       | 1532608.00  | 
| Wind Turbine G90 2 Megawats                                                                                                        | 1251625.00  | 
| Land Cruiser Prado. FJ Cruiser. Dyna trucks. Toyoace.IMV def unit.                                                                 | 191687.00   | 
| Retaining wall structure with a main wall (sheet pile): 136 tonnes of steel sheet piles and 4 tonnes of tierods per 100 meter wall | 167000.00   | 
| TCDE                                                                                                                               | 99075.00    | 
| Mercedes-Benz GLE (GLE 500 4MATIC)                                                                                                 | 91000.00    | 
| Mercedes-Benz S-Class (S 500)                                                                                                      | 85000.00    | 
| Mercedes-Benz SL (SL 350)                                                                                                          | 72000.00    | 


### 3.2. What are the industry groups of these products?

### 3.3. What are the industries with the highest contribution to carbon emissions?

### 3.4. What are the companies with the highest contribution to carbon emissions?

### 3.5. What are the countries with the highest contribution to carbon emissions?

### 3.6. What is the trend of carbon footprints (PCFs) over the years?

### 3.7. Which industry groups has demonstrated the most notable decrease in carbon footprints (PCFs) over time?

