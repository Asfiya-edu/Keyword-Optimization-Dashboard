# Analyzing Keywords Using Google Trends & YouTube Ads APIs

## Overview
Welcome to the repository for our comprehensive project focused on keyword analysis using Google Trends and YouTube Ads APIs. This project aims to provide actionable insights into keyword performance by leveraging data from two powerful platforms: Google Trends and YouTube Ads.

![rainbowline](https://github.com/Asfiya-edu/Travel-Hospitality-Analysis-Dashboard-Excel/assets/135417984/7b2fe4d0-348c-4094-96e8-d12a40fffb4c)
---

## Table of Contents

1. [Project Objectives](#project-objectives)
2. [Dashboards](#dashboards)
3. [Features](#features)
4. [Key Sections](#key-sections)
5. [Power Query Implementation](#power-query-implementation)
   - [Base Table Creation](#base-table-creation)
   - [Parameterized API Calls](#parameterized-api-calls)
   - [Data Expansion and Analysis](#data-expansion-and-analysis)
   - [Power Query Code](#power-query-code)
6. [Time Series Visual with Dynamic Slicers in Power BI](#time-series-visual-with-dynamic-slicers-in-power-bi)
7. [Scope of Keywords Analytics Dashboard](#scope-of-keywords-analytics-dashboard)
   - [Enhanced Data Integration and Customization](#enhanced-data-integration-and-customization)
   - [Advanced Analysis and Insights](#advanced-analysis-and-insights)
   - [Interactive and Real-Time Features](#interactive-and-real-time-features)
   - [Consolidated Reporting](#consolidated-reporting)
6. [Future Scope of the Project](#future-scope-of-the-project)

---
![rainbowline](https://github.com/Asfiya-edu/Travel-Hospitality-Analysis-Dashboard-Excel/assets/135417984/7b2fe4d0-348c-4094-96e8-d12a40fffb4c)

## Project Objectives
The primary goal of this project is to create a dynamic Power BI dashboard that visualizes and analyzes keyword trends, helping businesses make data-driven decisions for optimizing their digital marketing strategies. By integrating data from Google Trends and YouTube Ads, we provide a robust tool for understanding keyword popularity, rising trends, and effective ad performance.

![rainbowline](https://github.com/Asfiya-edu/Travel-Hospitality-Analysis-Dashboard-Excel/assets/135417984/7b2fe4d0-348c-4094-96e8-d12a40fffb4c)

## **Dashboards**

### **Dashboard link:** https://app.powerbi.com/groups/me/reports/14c0887e-99c7-49ed-8268-406dbc8ad26b/4bb83930be30a02ce778?clientSideAuth=0&experience=power-bi

# **Overview**

![Screenshot 2024-07-26 015044](https://github.com/user-attachments/assets/8a3c3aee-42cf-46d5-bdf5-762385668bc7)

# **Keywords by Date**

![Screenshot 2024-07-26 015231](https://github.com/user-attachments/assets/31d360ae-b67f-4590-a67a-72888c83db08)

# **Real - Time**

![Screenshot 2024-07-26 015259](https://github.com/user-attachments/assets/201730d1-2cec-4b6a-bc5b-35b05956bd91)

# **Rising & Top Keywords**

![Screenshot 2024-07-26 015325](https://github.com/user-attachments/assets/66c81c29-e616-48ed-8a1f-b4a4080ab516)

# **Youtube Relevant Ads**

![Screenshot 2024-07-26 015412](https://github.com/user-attachments/assets/9009fc0b-4ea3-4a78-a4c1-f15dc5bc78c1)

![rainbowline](https://github.com/Asfiya-edu/Travel-Hospitality-Analysis-Dashboard-Excel/assets/135417984/7b2fe4d0-348c-4094-96e8-d12a40fffb4c)

## Features

- **Google Trends Integration:** Utilize Google Trends API to track and visualize keyword search trends over time, providing insights into the popularity and regional interest of specific keywords.
- **YouTube Ads Analysis:** Leverage YouTube Ads API to analyze video ad performance, including ad durations and engagement metrics, to optimize advertising strategies.
- **Interactive Dashboard:** A comprehensive Power BI dashboard that integrates data from both APIs, offering visualizations and analytics to support keyword optimization and strategic planning.
- **Data-Driven Insights:** Extract meaningful patterns and trends from the data, enabling users to identify opportunities and refine their keyword strategies.

![rainbowline](https://github.com/Asfiya-edu/Travel-Hospitality-Analysis-Dashboard-Excel/assets/135417984/7b2fe4d0-348c-4094-96e8-d12a40fffb4c)
  
## Key Sections

- **Data Collection:** Detailed explanations of how data is gathered from Google Trends and YouTube Ads APIs, including API calls for country-specific trends, relevant queries, and rising keywords.
- **Schema Design:** Overview of the schema used to manage data, including the rationale behind the absence of relational keys and handling redundant columns.
- **Dashboard Development:** Insights into the development of the Power BI dashboard, including key visualizations, calculations, and the integration process.
- **Case Studies & Guesstimates:** Analyzing real-world business problems and proposing strategies to improve keyword performance and advertising effectiveness based on the collected data.
- **Business Impact:** How the dashboard and keyword analysis can help businesses optimize their marketing strategies and achieve better ROI.

![rainbowline](https://github.com/Asfiya-edu/Travel-Hospitality-Analysis-Dashboard-Excel/assets/135417984/7b2fe4d0-348c-4094-96e8-d12a40fffb4c)

## Power Query Implementation

### Base Table Creation

In Power Query, we start by creating a base table to hold the raw data extracted from the APIs. This table serves as the foundation for further data processing and analysis. The base table includes essential fields such as:
- Keyword
- Date
- Country
- Past 7 days Search
- Related Keywords
- Youtube Ads

  ![Screenshot 2024-07-26 041816](https://github.com/user-attachments/assets/8914425d-b0ae-4ad4-a3db-cc5cb8571022)

### Parameterized API Calls


![Screenshot 2024-07-26 041748](https://github.com/user-attachments/assets/4145f64b-0adc-45ff-a199-c32250677113)

![Screenshot 2024-07-26 042042](https://github.com/user-attachments/assets/2576be0b-aeff-4d4d-8ea6-0068698b6c1d)

To make the analysis dynamic, parameters are used to adjust API calls. Here's how it works:
- **Creating Parameters**: Define parameters in Power Query that can be used in API calls. These parameters allow for flexibility in keyword analysis.
- **Using Parameters in API Calls**: Incorporate these parameters into the API URL to fetch specific data. For example, you can set parameters for different keywords or time ranges.
- **Editable Parameters**: Parameters can be edited directly within Power Query or through external configuration, making it easy to refresh data based on updated criteria.

### Data Expansion and Analysis

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

![rainbowline](https://github.com/Asfiya-edu/Travel-Hospitality-Analysis-Dashboard-Excel/assets/135417984/7b2fe4d0-348c-4094-96e8-d12a40fffb4c)

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

![rainbowline](https://github.com/Asfiya-edu/Travel-Hospitality-Analysis-Dashboard-Excel/assets/135417984/7b2fe4d0-348c-4094-96e8-d12a40fffb4c)

### 2. **Creating Dynamic Date Parameters**

The creation of a Date Range parameter facilitates dynamic date filtering in reports. This parameter enables:

- **Customizable Date Filters**: Users can adjust the start and end dates to focus on specific periods.
- **Enhanced Interactivity**: Provides a flexible date range selection for tailored data analysis.

![rainbowline](https://github.com/Asfiya-edu/Travel-Hospitality-Analysis-Dashboard-Excel/assets/135417984/7b2fe4d0-348c-4094-96e8-d12a40fffb4c)

### 3. **Adding and Configuring Slicers**

![Screenshot 2024-07-26 050944](https://github.com/user-attachments/assets/562e903d-d5c6-4580-ab22-9903582f908a)


Incorporating slicers for `Year`, `Quarterly`, `Month_Year`, and `DateRange` enhances report interactivity:

- **`Year` Slicer**: Filters data based on the selected year, supporting annual comparisons.
- **`Quarterly` Slicer**: Filters data by quarters, aiding in quarterly performance evaluations.
- **`Month_Year` Slicer**: Enables filtering by specific months and years, which is beneficial for monthly trend analysis.
- **`DateRange` Slicer**: Allows users to select a custom date range, providing flexible filtering options.

![rainbowline](https://github.com/Asfiya-edu/Travel-Hospitality-Analysis-Dashboard-Excel/assets/135417984/7b2fe4d0-348c-4094-96e8-d12a40fffb4c)

### 4. **Creating the Time Series Visual**

![Screenshot 2024-07-26 043950](https://github.com/user-attachments/assets/6aee3ea7-a4f6-40f6-a57d-9a46e7ea2c63)

A time series visual, such as a line chart, displays data trends over time:

- **Date Axis**: Utilizes the `Date` column to visualize changes and trends over time.
- **Measure Values**: Plots measures on the values axis to reveal trends, peaks, and troughs in the data.

![rainbowline](https://github.com/Asfiya-edu/Travel-Hospitality-Analysis-Dashboard-Excel/assets/135417984/7b2fe4d0-348c-4094-96e8-d12a40fffb4c)

## **Scope of Keywords Analytics Dashboard** 

### Enhanced Data Integration and Customization

1. **Multi-Source Integration**: Power BI allows to combine data from Google Trends with other sources, such as YouTube Ads data, CRM systems, or social media analytics. This integration can provide a more holistic view of marketing landscape and consumer behavior.

2. **Customizable Visualizations**: Power BI offers extensive visualization options and customization capabilities. We can tailor charts, graphs, and dashboards to meet specific business needs or stakeholder preferences, which can make the data more actionable.

### Advanced Analysis and Insights

1. **In-Depth Comparative Analysis**: With Power BI, you can perform advanced comparative analyses, such as benchmarking keyword performance across different time periods, regions, or platforms, and visualizing these comparisons effectively.

2. **Custom Metrics and KPIs**: We can create custom metrics and Key Performance Indicators (KPIs) that align with your business objectives, providing deeper insights into how keywords and ads are impacting your goals.

### Interactive and Real-Time Features

1. **Interactive Dashboards**: Power BI dashboards are interactive, allowing users to drill down into specific data points, filter information, and explore different aspects of the data dynamically.

2. **Real-Time Data Updates**: By connecting directly to Google Trends and YouTube Ads APIs, we can ensure that your dashboard reflects real-time or near-real-time data, enabling timely decision-making.

### Consolidated Reporting

1. **Comprehensive Reports**: You can generate consolidated reports that integrate data from various sources and present it in a unified format, making it easier for stakeholders to understand and act upon the insights.

![rainbowline](https://github.com/Asfiya-edu/Travel-Hospitality-Analysis-Dashboard-Excel/assets/135417984/7b2fe4d0-348c-4094-96e8-d12a40fffb4c)

## Future Scope of the Project

### **Enhanced Data Integration and Customization**

1. **Expansion to Additional Data Sources**:
   - **Integration with More Platforms**: Future enhancements may include integration with additional data sources such as Google Ads, Bing Ads, or e-commerce platforms, providing an even more comprehensive view of digital marketing efforts.
   - **API Expansion**: Leveraging more APIs to integrate with other business systems (e.g., customer feedback systems, sales databases) will enhance the ability to cross-reference Google Trends data with other relevant business metrics.

2. **Advanced Customization Options**:
   - **Enhanced Visualization Features**: Further development could include creating advanced visualizations such as heat maps, advanced scatter plots, or custom charts tailored to specific business needs.
   - **Personalized Dashboards**: Offering more granular customization options for different user roles or departments to ensure that each stakeholder has access to the most relevant and actionable insights.

### **Advanced Analysis and Insights**

1. **Deeper Comparative Analysis**:
   - **Cross-Platform Benchmarking**: Future work could focus on benchmarking performance across different digital platforms and channels, including social media and content marketing, to provide a more integrated view of marketing effectiveness.
   - **Historical Data Analysis**: Enhancements could include more sophisticated analysis of historical data trends to identify long-term patterns and correlations.

2. **Enhanced Metrics and KPIs**:
   - **Custom Metrics Development**: Developing additional custom metrics and KPIs tailored to evolving business objectives, such as customer engagement scores or ROI on specific marketing activities.
   - **Predictive Analytics**: Incorporating predictive analytics to forecast future keyword trends and ad performance based on historical data and emerging patterns.






