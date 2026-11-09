1. Task 2 :- Exploratory Data Analysis (Week 2)
2. Dataset :- Hotel Booking Dataset

## 1. Importing Libraries

In this section, we import the Python libraries required to perform exploratory data analysis.

- Pandas: Used for loading, manipulating, cleaning, and analysing structured datasets.
- NumPy: Used for numerical calculations and mathematical operations.
- Matplotlib: Used to create different types of data visualizations.
- Seaborn: Used to create statistical visualizations such as histograms, box plots, and correlation heatmaps.
- Warnings: Used to control unnecessary warning messages during analysis.

## 2. Loading the Dataset

In this section, we load the Hotel Booking Demand dataset into a Pandas DataFrame.

The dataset is stored in CSV format. We use the `read_csv()` function to import the data.

A DataFrame allows us to access, inspect, manipulate, and analyse the dataset using Pandas.

The raw dataset will be preserved separately so that the original data remains unchanged during our analysis.

## 3. Initial Data Inspection

Before performing exploratory data analysis, it is important to understand the structure and contents of the dataset.

In this section, we will inspect the dataset dimensions, view sample records, examine column names, and identify numerical and categorical variables.

This initial inspection helps us understand what information is available and which analysis techniques can be applied to different columns.

### 3.1 Initial Data Inspection – Observations

The initial inspection of the Hotel Booking Demand dataset reveals the following:

1. Dataset Dimensions: The dataset contains 119,390 rows and 32 columns, indicating a large collection of hotel booking records.

2. Numerical Variables: The dataset contains 20 numerical columns, including lead time, arrival year, number of guests, booking changes, and average daily rate (ADR).

3. Categorical Variables: The dataset contains 12 columns identified as categorical, including hotel type, meal plan, market segment, customer type, and reservation status.

4. Data Types: Most numerical variables have integer or floating-point data types, while categorical variables are stored as strings.

5. Potential Data Quality Issues: The initial inspection shows missing values in some columns, including children, country, agent, and company. These will be investigated in the data quality assessment.

6. Date Information: The reservation_status_date column is currently stored as a string and may need conversion into datetime format for date-based analysis.


## 4. Data Quality Assessment

Data quality assessment is an important step in exploratory data analysis. It helps identify issues that may affect the accuracy and reliability of our analysis.

## 5. Missing Value Handling

Missing values can affect statistical calculations and data analysis. Therefore, it is important to handle them before proceeding with exploratory data analysis.

Based on the initial data quality assessment, missing values were identified in four columns: `company`, `agent`, `country`, and `children`.

The following strategies will be applied:

- Company: Replace missing values with 0.
- Agent: Replace missing values with 0.
- Country: Replace missing values with "Unknown".
- Children: Replace missing values with 0.

## 5.1 Observations

Missing values were handled successfully in the company, agent, country, and children columns using the selected replacement strategies.

Missing company and agent identifiers were replaced with 0.

Missing country values were replaced with "Unknown".

Missing children values were replaced with 0.

After applying these treatments, the dataset was checked again to verify the remaining missing values.

## 6. Duplicate Records Handling

Duplicate records are rows that contain identical values across all columns in a dataset.

Duplicates can affect statistical calculations, frequency distributions, and analytical results. Therefore, identifying and handling duplicate records is an important part of data cleaning.

## 6.1 Identifying Duplicate Records

Before removing duplicate records, we need to identify how many exact duplicate rows are present in the dataset.

The Pandas duplicated() method identifies rows that have already appeared earlier in the dataset.

By default, the first occurrence of a record is considered unique, while subsequent identical occurrences are marked as duplicates.

## 6.2 Removing Duplicate Records

After identifying duplicate records, we will remove exact duplicate rows using the Pandas drop_duplicates() method.

The keep='first' parameter retains the first occurrence of each identical record and removes subsequent occurrences.

This approach eliminates repeated rows while retaining one representative record from each duplicate group.

The dataset initially contained 31,994 exact duplicate records. These records were removed using `drop_duplicates(keep="first")`, retaining one copy of each identical record.

- Original records: 119,390
- Duplicate records removed: 31,994
- Records after cleaning: 87,396
- Remaining exact duplicates: 0

The dataset now contains 87,396 rows and 32 columns. No columns were removed. Only exact duplicate rows were eliminated.

### 7. Save the Cleaned Dataset

After handling missing values and removing exact duplicate records, save the cleaned dataset in the `data/cleaned` folder. This file will be used for the upcoming exploratory data analysis.

### 8 Descriptive Statistics of Numerical Columns

Descriptive statistics provide a statistical summary of numerical variables. Measures such as mean, median, standard deviation, minimum, maximum and quartiles help us understand the central tendency, spread and distribution of the data.

Identifier columns such as `agent` and `company` will be excluded from the main numerical summary because their values represent IDs rather than measurable quantities.

### Interpretation of Numerical Descriptive Statistics

1. Booking cancellations: The mean of `is_canceled` is approximately 0.275, indicating that around 27.49% of bookings in the cleaned dataset were canceled.

2. Lead time: The average lead time is approximately 79.89 days, while the median is 49 days. This indicates that the distribution is right-skewed, with some bookings made much earlier than others.

3. Stay duration: Guests stay an average of approximately 1 weekend night and 2.63 weekday nights. The median weekday stay is 2 nights.

4. Guest composition: The average number of adults is approximately 1.88 per booking. The median values for children and babies are both zero, suggesting that most bookings do not include children or babies.

5. Repeated guests: The mean of `is_repeated_guest` is approximately 0.039, suggesting that around 3.91% of bookings belong to repeated guests.

6. Special requests: The average number of special requests is approximately 0.70 per booking, while the median is zero.

7. Potential outliers: Some variables have unusually high maximum values, such as `lead_time` (737), `adults` (55), `adr` (5400), and `days_in_waiting_list` (391). The negative minimum ADR value (-6.38) also requires investigation.

These unusual values will be examined further during outlier analysis rather than removed without investigation.

### 8.1 Descriptive Statistics of Categorical Columns

Categorical descriptive statistics help us understand the different categories present in the dataset.

We will examine:
- Count: Total non-null records
- Unique: Number of distinct categories
- Top: Most frequently occurring category
- Freq: Frequency of the most common category

### Interpretation of Categorical Descriptive Statistics

1. Hotel type: City Hotel is the most frequent hotel type, with 53,428 records out of 87,396.

2. Arrival month: August is the most frequently recorded arrival month, with 11,257 bookings.

3. Meal plan: BB is the most common meal plan, appearing in 67,978 records.

4. Country: PRT (Portugal) is the most frequently recorded country, with 27,453 records.

5. Market segment: Online TA (Online Travel Agents) is the most common market segment, with 51,618 records.

6. Distribution channel: TA/TO (Travel Agents/Tour Operators) is the most frequent distribution channel, with 69,141 records.

7. Room type: Room type A is the most frequently reserved room type, with 56,552 records. It is also the most frequently assigned room type, with 46,313 records.

8. Deposit type: No Deposit is the dominant deposit category, appearing in 86,251 records.

9. Customer type: Transient customers are the most frequent customer type, with 71,986 records.

10. Reservation status: Check-Out is the most common reservation status, with 63,371 records.

Overall, the dataset contains a strong concentration of City Hotel bookings, online travel-agent bookings, and transient customers.

## 9. Data Visualization – Univariate Analysis

### 9.1 Distribution of Numerical Features

Histograms show the frequency distribution of numerical variables, while Kernel Density Estimation (KDE) curves provide a smoothed representation of the distribution.

We will visualize selected numerical features, including lead time, average daily rate (ADR), stay duration, waiting-list days, and special requests. These variables can help us understand booking patterns and guest behavior.

## 10. Correlation Analysis

Correlation analysis helps us understand the strength and direction
of relationships between numerical variables.

We use the Pearson correlation coefficient, which ranges from -1 to +1.

### Correlation Heatmap

A correlation heatmap provides a visual representation of relationships
between numerical variables.

Positive correlations indicate variables moving in the same direction,
while negative correlations indicate variables moving in opposite directions.

### Interpretation

1. The strongest positive correlation was observed between `stays_in_week_nights` and `stays_in_weekend_nights` (0.56). This indicates that guests staying longer during weekdays also tend to stay longer during weekends.

2. The strongest negative correlation was observed between `arrival_date_week_number` and `arrival_date_year` (-0.51). This indicates a moderate negative relationship between these variables, although it may be influenced by the distribution of booking dates across different years.

3. A moderate positive correlation (0.44) was observed between `is_repeated_guest` and `previous_bookings_not_canceled`, suggesting that repeat guests tend to have a history of bookings that were not canceled.

4. A weak positive correlation (0.18) was observed between `is_canceled` and `lead_time`, suggesting that bookings made further in advance have a slightly higher tendency to be canceled.

5. Most variable pairs do not show very strong linear relationships, indicating that hotel booking patterns are influenced by multiple factors.



## 11. Box Plot Analysis

Box plots help visualize the distribution of numerical variables
and identify potential outliers.

In this analysis, we compare booking characteristics between
City Hotel and Resort Hotel to understand differences in
booking patterns and identify unusual observations.


### Interpretation

1. The box plots show differences in the distribution of booking
   characteristics between City Hotel and Resort Hotel.

2. The median values indicate the typical booking characteristics
   for each hotel type.

3. Potential outliers were identified using the IQR method.
   These values represent observations outside the expected range.

4. Outlier percentages help identify which numerical features
   contain more unusual observations.

5. Outliers will not be removed automatically because they may
   represent genuine booking behavior.

### Additional Outlier Investigation – ADR

During the investigation of the highest ADR values, an unusually high ADR of 5400 was identified in a City Hotel booking.

The next highest values were considerably lower, indicating that the maximum value requires further investigation.

The record was not removed automatically because extreme values may represent genuine booking observations. Additional booking details will be examined to determine whether the value is valid or a potential data-quality issue.

### ADR Outlier Investigation – Findings

An unusually high ADR value of 5400 was identified in a City Hotel booking.

Further investigation revealed that the booking involved two adults staying for one weekday night. The reservation was canceled before the scheduled arrival date.

This observation is significantly higher than other ADR values in the dataset and may represent a potential data-quality anomaly.

However, the record was retained because there is insufficient evidence to confirm that it is incorrect.



## 12. Time-Series Analysis

Time-series analysis helps identify booking trends and seasonal
patterns over different months and years.

In this analysis, we examine monthly booking volumes and
cancellation rates using arrival dates.

### Monthly Booking Trends

This analysis examines the number of hotel bookings received
during each month across the available years.


1. Monthly Hotel Booking Trends

The first line chart tracks the total volume of monthly hotel bookings over a multi-year period stretching from mid-2015 to mid-2017.

Key Observations

• Overall Growth Trajectory: The dataset showcases a strong macro-upward trend. Total bookings started around 2,500 in mid-2015 and surged to peaks well above 4,500 by mid-2017.
• Cyclical Seasonality: Clear seasonal patterns emerge with bookings consistently plunging during the winter months (dipping near or below 2,500 around January 2016 and January 2017) and peaking during warmer summer intervals.
• Peak Booking Windows: Major volume surges occurred during late summer 2016 and reached their highest historical levels around May/July 2017.


2. Monthly Hotel Cancellation Rate

The second line chart tracks the percentage of bookings canceled each month across the exact same timeline.

Key Observations

• Correlated Volatility: Cancellations fluctuated dynamically between roughly 15% and over 40%.
• The 2015 Drop & Recovery: The cancellation rate saw a sharp initial decline from mid-2015 down to its lowest historical floor (around 15%) near January 2016. From that point onward, the rate steadily climbed back up.
• Upward Trend in Rejections: By late 2016 and moving into 2017, the baseline cancellation rate shifted upward, culminating in an all-time high of over 40% near the end of the observed timeline in mid-2017.


## 13. Group-by Analysis

Group-by analysis helps us compare booking patterns across
different categorical variables.

In this section, we analyze booking volumes and cancellation
rates across hotel types, market segments, customer types,
and distribution channels.


## Key Observations

• The Online TA Risk: Online Travel Agencies represent the single biggest segment by a massive margin (51,618 bookings). However, they also suffer from a highly severe cancellation rate of 35.35%. Over a third of your main revenue pipeline falls through.
• Groups and Volatility: Group bookings show the second highest structured cancellation rate at 27.01%. When groups cancel, it leaves large blocks of rooms empty simultaneously, creating a distinct revenue management risk.
• Stable Channels: Direct bookings and Corporate accounts demonstrate excellent stability, maintaining low cancellation rates between 12% and 15%.


## Key Observations

• Transient Dominance: Standard "Transient" customers (independent, individual travelers) make up the overwhelming majority of your customer base (71,986 bookings). They also cancel at a high rate of 30.11%.
• Transient-Party vs. Transient: Interestingly, when transient customers book as part of a package or party (Transient-Party), their cancellation rate drops by half down to 15.24%, indicating significantly stronger commitment.


## Key Observations

• TA/TO Dependency: The hotel relies heavily on Third-Party intermediaries (TA/TO) for 69,141 bookings. This reliance introduces major volatility with a 30.97% cancellation rate, likely driven by easy "free cancellation" terms offered on modern booking apps.
• Direct Channel Value: Direct bookings are vastly superior in terms of reliability, holding steady at a low 14.82% cancellation rate.

##  14. Scatter Plot Analysis

Scatter plots help identify relationships, patterns, clusters,
and unusual observations between two numerical variables.

In this section, we explore relationships between booking
lead time, average daily rate, and length of stay.

## 14.1 Scatter plot: Lead time vs ADR

### Interpretation 

1. Lead Time vs ADR

The scatter plot shows that ADR values are widely distributed across different lead times. There is no clear pattern indicating that bookings made earlier have higher or lower daily rates. This suggests that booking lead time does not have a noticeable relationship with the average daily rate.



## 14.2 Scatter plot: Weeknight stays vs ADR

### Interpretation 
2. Weeknight Stays vs ADR

The scatter plot shows that ADR varies across different weekday stay durations. However, there is no strong visible pattern between the number of weeknight stays and ADR. This indicates that guests staying for more weekdays do not necessarily pay higher daily rates.

## 14.3 Scatter plot: Weekend stays vs Weeknight stays

### Interpretation

3. Weekend Stays vs Weeknight Stays

The scatter plot shows a positive relationship between weekend and weeknight stays. Guests who stay for more weekend nights generally also tend to stay for more weeknights. Most bookings are concentrated around shorter stay durations, with fewer bookings involving longer stays.

## Key Findings and Data-Driven Insights

### 1. Guest Stay Duration
The analysis found a moderate positive relationship between weeknight stays and weekend stays (approximately 0.56). Guests who stay for more weekend nights generally tend to stay for more weeknights as well.

**Business Recommendation:** Hotels can use guest stay-duration patterns to improve room availability, staffing, and resource allocation.

### 2. Booking Lead Time and Cancellation
The correlation between lead time and cancellations was approximately 0.18, indicating a weak positive relationship. This suggests that bookings made further in advance are slightly more likely to be associated with cancellations.

**Business Recommendation:** Hotels can monitor bookings with longer lead times and consider sending booking reminders or offering suitable confirmation policies to reduce cancellation risks.

### 3. Differences in Potential Outliers Between Hotels
City Hotels had higher potential outlier percentages than Resort Hotels for lead time (3.18% vs. 1.78%), ADR (4.66% vs. 2.22%), and weeknight stays (1.29% vs. 0.53%). Resort Hotels had a slightly higher percentage of weekend-stay outliers (0.41% vs. 0.15%).

**Business Recommendation:** Hotels should monitor unusual booking durations, lead times, and room rates separately for each hotel type to identify unusual booking patterns and maintain data quality.

### 4. Relationship Between ADR and Booking Behaviour
The scatter plots showed no clear relationship between ADR and lead time or between ADR and weekday stay duration.

**Business Recommendation:** Hotels should consider additional factors, such as customer type, seasonality, and market segment, when reviewing room pricing strategies rather than relying only on booking lead time or stay duration.

### Overall Finding
The analysis highlights differences in guest booking behaviour, stay duration, and potential outliers between hotel types. These findings can help hotel management improve booking management, room allocation, pricing reviews, and operational planning.

## Conclusion and Business Recommendations

### Conclusion

The exploratory data analysis of the Hotel Booking Demand dataset provided useful insights into hotel booking patterns, customer behaviour, cancellation trends, room pricing, and stay durations.

The analysis revealed that City Hotels and Resort Hotels have differences in booking characteristics and potential outlier patterns. A moderate positive relationship was observed between weekend and weeknight stays, while ADR showed no clear relationship with lead time or weekday stay duration. The analysis also highlighted unusual ADR values that require further investigation.

Overall, the findings help understand customer booking behaviour and identify areas where hotel management can improve operational efficiency and decision-making.

### Business Recommendations

1. Improve Cancellation Management: Monitor cancellation rates across different market segments and distribution channels. Hotels can review booking confirmation processes and consider reminders for bookings made well in advance.

2. Optimize Room and Resource Allocation: Use monthly booking trends and guest stay-duration patterns to plan room availability, housekeeping schedules, and staff requirements more effectively.

3. Review Pricing Strategies: Analyze ADR across hotel types, customer segments, and seasons to identify opportunities for better pricing decisions. Avoid relying on lead time or stay duration alone when setting room rates.

4. Improve Data Quality: Investigate unusual ADR values, negative rates, and extreme booking durations before using the data for business reporting or pricing decisions.

5. Understand Customer Behaviour: Study booking patterns across customer types and distribution channels to develop targeted marketing strategies and improve the guest experience.

### Final Summary

This analysis demonstrates how exploratory data analysis can transform raw hotel booking data into meaningful business insights. By monitoring cancellations, understanding customer preferences, improving resource planning, and reviewing pricing patterns,
