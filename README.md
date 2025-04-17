# **Cyclistic Bike-Share Analysis**

## 📄 Project Overview

This project is part of the Google Data Analytics Capstone case study. The goal is to analyze historical bike trip data provided by Cyclistic, a Chicago-based bike-share company, to identify how annual members and casual riders use the service differently. The insights are used to support marketing strategies aimed at converting casual riders into annual members.

## 🔗 Business Objective

**Key Question: How do annual members and casual riders use Cyclistic bikes differently?**

Marketing Director Moreno believes that converting casual riders to members is crucial for long-term profitability. Understanding usage patterns is the first step toward designing data-driven marketing campaigns.

## 📚 Dataset Summary

- **Source:** 12 CSV files (Sept 2021 – Aug 2022)  
- **Total Size:** ~927.83 MB  
- **Total Rows:** ~5.8 million records  
- **Storage:** Cleaned and merged using Google Sheets & BigQuery  

## ⚖️ Tools Used

| Tool                  | Purpose                                  |
|-----------------------|------------------------------------------|
| Google Sheets         | Cleaning small-to-medium files           |
| Google BigQuery       | Uploading and querying large datasets    |
| SQL                   | Aggregation, transformation, and filtering |
| Python (Jupyter Notebook) | EDA and Visualization             |
| Seaborn & Matplotlib  | Statistical plotting                     |

## ✏️ Data Cleaning Steps

- Removed NULLs in essential columns (station names, timestamps).
- Filtered invalid rides (e.g. ride duration ≤ 0 or ≥ 9 hours).
- Computed ride duration using ended_at - started_at in minutes.
- **Added** day_of_week using weekday functions.
- Merged data into one BigQuery table via GCS.
- Verified data integrity via logical constraints and summary stats.

## 🔢 Feature Engineering

- **Ride Duration (min):** Time difference between start and end time.
- **Day of Week:** Categorical feature to track usage trends.
- **Displacement (km):** Haversine formula applied to start and end lat/lng.
- **Time per Kilometer (min/km):** Efficiency metric to compare rider groups.

## 📊 Key Visualizations

1. **Ride Duration by Rider Type**  
   - Boxplot shows casual riders take longer rides on average.  
   - Outliers removed using `showfliers=False`.

2. **Displacement by Rider Type**  
   - Casual riders also tend to travel further distances.  
   - Members are more consistent, likely using bikes for commuting.

3. **Time Taken per Kilometer**  
   - Calculated as `duration_min / displacement_km`  
   - Members are more efficient, suggesting intentional routes vs. leisure.

4. **Ride Count by Hour of Day**  
   - Members peak during commute hours (8 AM & 5 PM)  
   - Casual riders peak in the afternoon (12 PM – 4 PM)

5. **Ride Count by Day of Week**  
   - Members: consistent weekday usage  
   - Casuals: heavy usage on weekends (leisure behavior)

6. **Bike Type Preference**  
   - Classic bikes are most used  
   - Casual riders use electric bikes more than members

## 🤝 Insights & Recommendations

- Casual riders tend to take longer rides, often during non-peak hours and on weekends. This pattern suggests that many casual riders use Cyclistic for leisure, sightseeing, or occasional transportation rather than daily commutes.

- Annual members show more consistent usage throughout the week, especially during morning and evening peak hours (8–10 AM and 5–7 PM). This indicates they rely on Cyclistic as a part of their routine, possibly for commuting to work, school, or running errands.

- Displacement and speed data show that members ride shorter distances more efficiently, while casual riders often cover longer routes at a slower pace. This further supports the idea that members are goal-oriented riders, while casual users are more recreational.

- Time per kilometer is significantly lower for members, showing they ride with greater purpose and route familiarity. Casual riders may be less familiar with bike lanes or the city layout, leading to slower and less efficient trips.

- Bike type preferences highlight that casual riders are more likely to use electric bikes, potentially due to their ease of use or appeal to tourists and occasional users.

✅ **Focus marketing efforts on:**

- Highlighting the value of annual plans for regular riders
- Weekend promotions to convert frequent casual users
- Social media ads targeting riders who use electric bikes
