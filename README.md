# Comprehensive Project: Analyzing Keywords Using Google Trends & YouTube Ads APIs

## Overview
Welcome to the repository for our comprehensive project focused on keyword analysis using Google Trends and YouTube Ads APIs. This project aims to provide actionable insights into keyword performance by leveraging data from two powerful platforms: Google Trends and YouTube Ads.

## Project Objectives
The primary goal of this project is to create a dynamic Power BI dashboard that visualizes and analyzes keyword trends, helping businesses make data-driven decisions for optimizing their digital marketing strategies. By integrating data from Google Trends and YouTube Ads, we provide a robust tool for understanding keyword popularity, rising trends, and effective ad performance.

## Features

- **Google Trends Integration:** Utilize Google Trends API to track and visualize keyword search trends over time, providing insights into the popularity and regional interest of specific keywords.
- **YouTube Ads Analysis:** Leverage YouTube Ads API to analyze video ad performance, including ad durations and engagement metrics, to optimize advertising strategies.
- **Interactive Dashboard:** A comprehensive Power BI dashboard that integrates data from both APIs, offering visualizations and analytics to support keyword optimization and strategic planning.
- **Data-Driven Insights:** Extract meaningful patterns and trends from the data, enabling users to identify opportunities and refine their keyword strategies.
  
## Key Sections

- **Data Collection:** Detailed explanations of how data is gathered from Google Trends and YouTube Ads APIs, including API calls for country-specific trends, relevant queries, and rising keywords.
- **Schema Design:** Overview of the schema used to manage data, including the rationale behind the absence of relational keys and handling redundant columns.
- **Dashboard Development:** Insights into the development of the Power BI dashboard, including key visualizations, calculations, and the integration process.
- **Case Studies & Guesstimates:** Analyzing real-world business problems and proposing strategies to improve keyword performance and advertising effectiveness based on the collected data.
- **Business Impact:** How the dashboard and keyword analysis can help businesses optimize their marketing strategies and achieve better ROI.


## Power Query Implementation

### **1. Base Table Creation**

In Power Query, we start by creating a base table to hold the raw data extracted from the APIs. This table serves as the foundation for further data processing and analysis. The base table includes essential fields such as:
- Keyword
- Date
- Country
- Past 7 days Search
- Related Keywords
- Youtube Ads

  ![Screenshot 2024-07-26 041816](https://github.com/user-attachments/assets/8914425d-b0ae-4ad4-a3db-cc5cb8571022)

### **2. Parameterized API Calls**


![Screenshot 2024-07-26 041748](https://github.com/user-attachments/assets/4145f64b-0adc-45ff-a199-c32250677113)

![Screenshot 2024-07-26 042042](https://github.com/user-attachments/assets/2576be0b-aeff-4d4d-8ea6-0068698b6c1d)

To make the analysis dynamic, parameters are used to adjust API calls. Here's how it works:
- **Creating Parameters**: Define parameters in Power Query that can be used in API calls. These parameters allow for flexibility in keyword analysis.
- **Using Parameters in API Calls**: Incorporate these parameters into the API URL to fetch specific data. For example, you can set parameters for different keywords or time ranges.
- **Editable Parameters**: Parameters can be edited directly within Power Query or through external configuration, making it easy to refresh data based on updated criteria.

### **3. Data Expansion and Analysis**

Once the base table is established, we create additional tables that reference the base table for expanded analysis. This process includes:
- **Data Expansion**: Adding columns and transforming data to suit analytical needs.
- **Creating Relationships**: Although there are no formal relationships (primary/foreign keys), data from various API calls are used to generate comprehensive visuals.
- **Visualizations**: Developing Power BI visuals based on the processed data, including trend graphs, keyword performance charts, and ad engagement metrics.

### Power Query Code

The provided Power Query code handles data extraction, parameter management, and data transformation. Below is a simplified version of the code used in the project:

```m
// Define parameters
let
    Keyword = ParameterKeyword,
    StartDate = ParameterStartDate,
    EndDate = ParameterEndDate,

    // API URL construction
    ApiUrl = Text.Format("https://api.example.com/data?keyword={0}&startDate={1}&endDate={2}", {Keyword, StartDate, EndDate}),

    // Data extraction
    Source = Json.Document(Web.Contents(ApiUrl)),
    DataTable = Table.FromList(Source[results], Splitter.SplitByNothing(), null, null, ExtraValues.Error),

    // Data transformation
    ExpandedTable = Table.ExpandRecordColumn(DataTable, "Column1", {"Keyword", "Date", "SearchVolume", "AdDuration", "EngagementMetrics"})
in
    ExpandedTable
```


## Time Series Visual with Dynamic Slicers in Power BI

## Steps

### 1. Create New Columns for Dynamic Date Slicers

Adding the following columns to `By_Date_API` table for filtering by year, quarter, and month-year:

1. **Month_Year Column:**
   ```DAX
   Month_Year = FORMAT(By_Date_API[Date], "mmm-yy")
   ```

2. **Q_Year Column:**
   ```DAX
   Q_Year = By_Date_API[Quaterly] & "-" & RIGHT(FORMAT(By_Date_API[Date], "yyyy"), 2)
   ```

3. **Quarterly Column:**
   ```DAX
   Quarterly = "Q" & FORMAT(By_Date_API[Date], "Q")
   ```

4. **Year Column:**
   ```DAX
   Year = YEAR(By_Date_API[Date])
   ```

   ![Screenshot 2024-07-26 043936](https://github.com/user-attachments/assets/878daab7-827d-4967-b073-57907c6c8648)

![Screenshot 2024-07-26 044150](https://github.com/user-attachments/assets/6dda95f7-eab6-4f7a-bd1e-5306f7186af1)


Adding columns like `Month_Year`, `Q_Year`, `Quarterly`, and `Year` to the `By_Date_API` table enables enhanced data filtering and analysis. These columns break down date information into more specific components, facilitating:

- **`Month_Year`**: Filters data by month and year in the "mmm-yy" format, aiding in monthly trend analysis.
- **`Q_Year`**: Combines the quarter and the last two digits of the year, useful for quarterly trend comparisons across different years.
- **`Quarterly`**: Represents the quarter of the year in "QX" format, allowing for quarter-based data filtering.
- **`Year`**: Provides the year from the date, simplifying annual data filtering and analysis.

### 2. **Creating Dynamic Date Parameters**

The creation of a Date Range parameter facilitates dynamic date filtering in reports. This parameter enables:

- **Customizable Date Filters**: Users can adjust the start and end dates to focus on specific periods.
- **Enhanced Interactivity**: Provides a flexible date range selection for tailored data analysis.

### 3. **Adding and Configuring Slicers**

![Screenshot 2024-07-26 050944](https://github.com/user-attachments/assets/562e903d-d5c6-4580-ab22-9903582f908a)


Incorporating slicers for `Year`, `Quarterly`, `Month_Year`, and `DateRange` enhances report interactivity:

- **`Year` Slicer**: Filters data based on the selected year, supporting annual comparisons.
- **`Quarterly` Slicer**: Filters data by quarters, aiding in quarterly performance evaluations.
- **`Month_Year` Slicer**: Enables filtering by specific months and years, which is beneficial for monthly trend analysis.
- **`DateRange` Slicer**: Allows users to select a custom date range, providing flexible filtering options.

### 4. **Creating the Time Series Visual**

![Screenshot 2024-07-26 043950](https://github.com/user-attachments/assets/6aee3ea7-a4f6-40f6-a57d-9a46e7ea2c63)

A time series visual, such as a line chart, displays data trends over time:

- **Date Axis**: Utilizes the `Date` column to visualize changes and trends over time.
- **Measure Values**: Plots measures on the values axis to reveal trends, peaks, and troughs in the data.

    




