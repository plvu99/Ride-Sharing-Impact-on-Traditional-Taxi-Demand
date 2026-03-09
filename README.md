# Ride-Sharing Impact on Traditional Taxi Demand

## 🔎 Overview

Ride-sharing platforms such as Uber have rapidly transformed urban transportation systems. As these platforms expand, an important question arises: _How do ride-sharing services affect traditional taxi demand?_

This project analyzes over 20 million ride records from Uber, Yellow Cabs, and Green Cabs in New York City during June 2015 to examine whether **Uber rides act as substitutes or complements to traditional taxi services**.

Using **exploratory data analysis and regression modeling**, the project evaluates how changes in Uber ride volume relate to taxi ride demand while controlling for weather conditions.

The analysis provides insights into how different transportation services respond to shared urban demand patterns.

## 🔐 Business Problem

Urban transportation operates as a multi-platform ecosystem, where different services compete for the same pool of riders.

With the rise of ride-sharing platforms, policymakers and transportation planners must understand:

* whether ride-sharing reduces taxi demand
* whether both services respond to common demand drivers
* how external factors such as weather affect transportation choices

If Uber and taxis are strong substitutes, the expansion of ride-sharing could significantly disrupt traditional taxi markets.

However, if both services respond to similar demand shocks—such as commuting patterns or weather conditions—they may function more as complements within the urban mobility system.

Understanding this relationship is crucial for:

* transportation policy
* urban mobility planning
* ride-hailing platform strategy

## 📊 Dataset

The project analyzes four datasets covering June 2015 transportation activity in New York City.

| Dataset           | Description                       |
| ----------------- | --------------------------------- |
| Yellow Taxi Trips | Trip records from NYC Yellow Cabs |
| Green Taxi Trips  | Trip records from NYC Green Cabs  |
| Uber Pickups      | Uber ride pickup data             |
| Weather Data      | Daily precipitation levels        |

The datasets were filtered to include pickup locations in Manhattan, the core operating zone for both Uber and Yellow taxis. 

After preprocessing, the dataset included:

* 11.2M Yellow Cab trips
* 2.0M Uber trips
* 0.46M Green Cab trips

with additional temporal features such as:

* date
* day of week
* hour of day
* pickup location

Here is the notebook for [data preprocessing](https://github.com/plvu99/Ride-Sharing-Impact-on-Traditional-Taxi-Demand/blob/main/data_preprocessing.ipynb).

## 📍 Methodology

The analysis follows three main steps:

### 1. Data Preprocessing

Trip data from all services were cleaned and standardized.

Key steps included:

* filtering pickups occurring in Manhattan
* converting timestamps to datetime format
* extracting time features (day, week, hour)
* aggregating ride counts by date and location

Taxi zone lookup tables were used to identify Manhattan pickup locations. 

### 2. Exploratory Data Analysis

EDA examined:

* total ride volume by service
* average daily rides
* trip patterns across days of the week

Results show that Yellow Cabs dominated the market in 2015, while Uber already demonstrated strong growth.

<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/912ea16c-b357-443d-987f-c7dcfaa15f73" />

Average daily rides:

| Service    | Avg Daily Trips |
| ---------- | --------------- |
| Yellow Cab | ~372,000        |
| Uber       | ~66,000         |
| Green Cab  | ~15,000         |

Trip demand peaks on Tuesdays and declines toward Sundays, suggesting strong commuter-driven demand patterns. 

<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/92cdfd6c-5235-46f3-9653-556e76f0b8d0" />

### 3. Regression Modeling

Two regression models were used to estimate the relationship between Uber rides and taxi demand.

**Model 1: Baseline Model**

Taxi rides predicted using Uber ride volume only.

Results:

* Uber coefficient ≈ 4.07
* p < 0.001
* R² = 0.525

This indicates that Uber ride volume alone explains 52.5% of variation in taxi ride demand. 

**Model 2: Weather-Controlled Model**

The model includes precipitation as a control variable.

Results:

* Uber coefficient ≈ 3.99
* precipitation coefficient ≈ 0.126
* R² = 0.526

Precipitation shows only marginal significance and adds minimal explanatory power to the model. 

## 🔑 Key Insights

### 1. Uber and Taxi demand move together

Uber ride volume is a strong predictor of taxi demand, explaining over 50% of demand variation.

This suggests both services respond to shared transportation demand patterns.

### 2. Traditional taxis still dominated the market in 2015

Yellow Cabs recorded over 11 million trips in Manhattan, significantly higher than Uber’s 2 million trips.

However, Uber had already achieved substantial market penetration.

### 3. Ride demand is strongly driven by weekday commuting

Both Uber and taxi rides peak on Tuesdays and weekdays, indicating that commuting and business travel drive ride demand.

### 4. Weather has limited impact on ride demand

While precipitation may increase transportation demand, it contributes very little explanatory power in predicting ride volume.

## ✍️ Business Recommendations

### 1. Transportation planning should consider shared demand drivers

Taxi and ride-sharing demand appear to respond to common urban mobility patterns, suggesting both services are part of the same transportation ecosystem.

### 2. Ride-sharing platforms should anticipate commuter demand

Demand spikes during weekday commuting hours present opportunities to optimize driver allocation, surge pricing strategies, and supply positioning.

### 3. Policymakers should view ride-sharing as complementary mobility

Rather than completely replacing taxis, ride-sharing platforms may expand overall transportation demand, serving riders who previously used other transport modes.

## ⚙ Tools & Technologies

* Python
* Data preprocessing (Pandas, NumPy)
* Data visualization (Matplotlib, Seaborn)
* Statsmodels (OLS regression)
* Parquet datasets
