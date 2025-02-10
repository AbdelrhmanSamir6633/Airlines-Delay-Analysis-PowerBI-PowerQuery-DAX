# Airlines-Delay-Analysis-PowerBI-PowerQuery-DAX

## Project Description
The primary goal of this project is to analyze the Airlines Delay Dataset, which encompasses comprehensive data on airlines, airports, and regions worldwide, along with delay durations and reasons. By leveraging data analysis and visualization techniques, the project aims to uncover hidden insights, identify patterns, and understand the factors contributing to airline delays. 
The findings will help stakeholders, including airlines, airports, and passengers, make informed decisions to improve operational efficiency and customer satisfaction.

## Contents 

<a href="">**1) Business Case.**</a>

<a href="">**2) Database Description.**</a>

<a href="">**3) Tools and Technologies Used.**</a>

<a href="">**4) Data Cleaning and Transformation.**</a>

<a href="">**5) Data Model.**</a>

<a href="">**6) Key Visualizations Using PowerBI.**</a>

<a href="">**7) Data Source & Project Files.**</a>
_____________________________________________________________________________________
<a href="">**Work Environment & Contributors**</a>

## (1/7) Business Case

### 1.1. Overview
The Airline Delay Analysis project is designed to support operational efficiency improvement, delay root cause analysis, customer experience enhancement, and strategic decision-making for airlines and airports. 

### 1.2. Key Business Questions
#### 1.2.1. Delay Performance Analysis
- What are the total delay durations and frequencies across airlines, airports, and regions?

- Which airlines or airports have the highest and lowest delay rates?

- How do delay durations vary by time of day, day of the week, or season?

#### 1.2.2. Root Cause Analysis
- What are the most common reasons for delays (e.g., weather, technical issues, air traffic)?

- Which factors contribute the most to delay durations?

- Are there specific airports or regions where certain delay reasons are more prevalent?

#### 1.2.3. Customer Impact and Experience
- How do delays impact passenger satisfaction and loyalty?

- Which airlines or airports have the best on-time performance, and how does this correlate with customer reviews?

- What are the most frequent complaints or issues reported by passengers during delays?

#### 1.2.4. Operational Efficiency
- How do delays impact airline operational costs (e.g., fuel, crew, maintenance)?

- Are there specific routes or flight schedules that are more prone to delays?

- How can airlines optimize flight schedules to minimize delays?

#### 1.2.5. Geospatial and Regional Analysis
- Which regions or airports experience the highest frequency and duration of delays?

- How do regional factors (e.g., weather, air traffic density) influence delays?

- Are there specific airports that act as bottlenecks for delays?

## (2/7) Database Description

The database for the Airline Delay Analysis consists of three main tables, each sourced from a corresponding CSV file:

- (A) Delayed Flights – This table contains detailed records of actual flights, including flight numbers, departure and arrival times, delays, origin and destination airports, and carrier information. It serves as the primary fact table for analysis.

- (B) Carrier – This table stores airline-specific data, including carrier codes and airline names. It acts as a lookup table to provide contextual information about airlines in the flight data.

- (C) Airport Codes – This table contains information about airports, including airport codes, names, and locations. It helps map airport identifiers to their respective geographic details.

## (3/7) Tools and Technologies Used

- Power BI – Data visualization and dashboard creation.
- DAX (Data Analysis Expressions) – For creating measures and calculations.
- Power Query – For data cleaning and preprocessing.
- GitHub – For version control and project hosting.
- Jira – for ensuring efficient task tracking.

## (4/7) Data Cleaning and Transformation

4.1. Power Query Editor:
Using Power Query Editor I was able to make some transformation on data like:
- Handling missing values by imputing or removing some unused columns.
- Standardizing date and time formats for trend analysis.
- Aggregating data by day, week, and month to identify trends.

4.2. DAX expressions:

- Creating Date Dimension:
![DIM_Date](https://github.com/user-attachments/assets/c6d4d8a4-d31b-49d8-852d-c5e25aff50ef)


- Creating Time Dimension:
![DIM_Time](https://github.com/user-attachments/assets/b19f1e0e-92ed-435d-8ea6-51c84ed5b319)


- Example of the Created Measures:
  
  - % On-Time Performance Measure
    ![% On-Time Performance Measure](https://github.com/user-attachments/assets/959d9af9-16c8-4d73-804d-91bb835966cd)

  - % Delay Performance Measure
    ![% Delay Performance Measure](https://github.com/user-attachments/assets/d3af6470-372a-4efb-98b6-7e10a6dc6829)

  - Total No. of Flights Measure
    ![Total No  of Flights Measure](https://github.com/user-attachments/assets/555771a4-6c9b-44e1-9e1c-76bfc86b0a09)

  - Total Arrival Delay Measure
    ![Total Arrival Delay Measure](https://github.com/user-attachments/assets/c9837c69-abc1-4788-bc37-1abc664ece32)

  
## (5/7) Data Model

### 5.1. Overview
This data model follows a star schema design, optimized for analytical queries in Power BI. The central fact table (Fact_DelayedFlights) records flight delay details, while multiple dimension tables provide descriptive attributes.

![Data_Model](https://github.com/user-attachments/assets/c938e807-57a9-47db-89c9-ee8a16107bc7)


### 5.2. Data Model Components

5.2.1. Fact Table: Fact_Delayed Flights

This table contains all measurable flight delay metrics, including:

- Delay Information: ArrDelay, CarrierDelay, WeatherDelay, NASDelay, SecurityDelay, LateAircraftDelay.
- Flight Details: CRSDepTime, CRSArrTime, DepTime, ArrTime.
- Categorization Flags: DelayCategory, DelayCauseFlag, Cancelled, Diverted.
- Keys for Joins: DateKey, DepTimeKey, DestCode (links to dimensions).

This table is the core of the analysis, as it stores all delay-related numerical values for reporting and trend analysis.

5.2.2. Dimension Tables:

5.2.2.1. Dim_Date (Date Dimension)
Provides temporal attributes: Year, Month, Day, Weekday, Quarter.
Helps in time-based aggregations (e.g., delays by month/year).

5.2.2.2. Dim_Time (Time Dimension)
Stores time-based attributes: Hour, Minute, Second, HourBucket.
Allows detailed analysis of peak delay times.

5.2.2.3. Dim_Airport Codes (Airport Codes Dimension)
Contains airport-specific details: airport, iata, icao, region_name.
Used to analyze delays by departure/destination airport.

5.2.2.4. Dim_Carrier (Carrier Dimension)
Stores airline-related attributes: Carrier Name, IATA Carrier Code, ICAO Carrier Code.
Helps track airline-specific delay patterns.


### 5.3. Importance of Star Schema Design

- Optimized Performance.
- Faster Queries: Joins between fact and dimension tables are simplified using one-to-many relationships.
- Improved Data Consistency: Centralized dimensions ensure consistent data across reports.
- Scalability: Easily extensible by adding new dimensions or measures without modifying the core fact table.

This model is designed for Power BI analytics, enabling users to:

- Analyze delay trends by time, airport, and carrier.
- Build KPIs and dashboards for flight performance monitoring.
- Identify patterns and root causes of delays for optimization.



