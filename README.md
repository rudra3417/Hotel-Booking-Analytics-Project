# Hotel Booking & Cancellation Analytics \| Power BI

## Project Overview

This project analyzes hotel booking data to understand booking
performance and cancellation patterns across hotel types, market
segments, and booking lead-time groups. An interactive Power BI
dashboard was developed to turn the booking data into meaningful
insights and practical recommendations.

## Business Problem

The business problem is to understand hotel booking performance and
cancellation patterns across different customer segments and time
periods to support better business decisions.

## Project Objective

The objective is to analyze booking performance and cancellation
patterns and provide data-driven insights and recommendations for better
business decisions.

## Dataset

-   **Dataset:** Hotel Booking Demand
-   **Source:** [Kaggle -- Hotel Booking
    Demand](https://www.kaggle.com/datasets/jessemostipak/hotel-booking-demand)
-   **Hotels covered:** City Hotel and Resort Hotel
-   **Original records:** 119,390 rows
-   **Final records after cleaning:** 119,204 rows

The dataset contains booking-related information such as hotel type,
cancellation status, arrival date, lead time, guest details, market
segment, customer type, average daily rate (ADR), and length of stay.

## Tools Used

-   **Power BI** -- Dashboard development and data visualization
-   **Power Query** -- Data cleaning and transformation
-   **DAX** -- Measures and calculated columns
-   **Excel** -- Data inspection and validation

## Data Preparation

The data preparation process included:

-   Examining missing values and handling them according to the column
    and analysis requirements.
-   Removing records with missing values in the `Children` column where
    the correct values could not be established.
-   Replacing missing `Country` values with `Unknown`.
-   Categorizing missing `Agent` and `Company` values as `No Agent` and
    `No Company`.
-   Removing records where the total number of registered guests was
    zero.
-   Retaining zero-night records because there was insufficient evidence
    to classify them as invalid.
-   Retaining exact duplicate rows because the dataset does not provide
    a unique booking identifier, and identical attribute values may
    belong to separate bookings.
-   Removing two extreme ADR records: one negative value and one
    unusually high value.
-   Creating `Total_Guests` and `Total_Nights`.
-   Creating `Arrival_Date` by combining the arrival year, month, and
    day fields.

After data preparation, the final dataset contained **119,204 records**.

## Data Model

The report uses a simple two-table model:

-   **Fact_Bookings** -- Contains the booking-level data.
-   **Dim_Calendar** -- A dedicated calendar table for time-based
    analysis.

The tables are connected through an active, one-to-many relationship:

`Dim_Calendar[Date]` → `Fact_Bookings[Arrival_Date]`

The Calendar table includes Year, Month, and Month Number fields. Month
is sorted by Month Number to maintain chronological order.

## Dashboard Pages

### 1. Booking Performance Overview

This page provides an overview of booking performance through:

**Key Performance Indicators** - Total Bookings - Successful Bookings -
Cancelled Bookings - Cancellation Rate - Average ADR

**Visuals** - Total Bookings by Month - Bookings by Hotel Type -
Bookings by Market Segment - Average ADR by Hotel Type

### 2. Cancellation Analysis

This page focuses on cancellation patterns through:

**Key Performance Indicators** - Cancelled Bookings - Cancellation
Rate - Average Booking Lead Days

**Visuals** - Cancellation Rate by Hotel Type - Monthly Cancellation
Rate Trend - Cancellation Rate by Market Segment - Cancellation Rate by
Booking Lead Time Group

## Key Insights

-   Out of 119,204 bookings, 44,194 were cancelled, resulting in an
    overall cancellation rate of approximately **37.07%**.
-   City Hotel contributed approximately **66.4%** of total bookings and
    had a higher cancellation rate (**41.8%**) than Resort Hotel
    (**27.8%**).
-   Online TA was the largest market segment, contributing approximately
    **56.4K bookings**.
-   The Groups market segment had the highest cancellation rate at
    approximately **61.1%**.
-   Cancellation rates increased across the booking lead-time groups,
    from approximately **9.6% for 0--7 days** to **57.0% for 181+
    days**.
-   City Hotel had a higher Average ADR (approximately **106.1**) than
    Resort Hotel (approximately **95.4**).

## Recommendations

Based on the analysis, the following actions may be considered:

-   Pay closer attention to bookings made far in advance through
    suitable reminders or reconfirmation processes.
-   Review confirmation procedures and appropriate cancellation or
    deposit policies for group bookings.
-   Prioritize cancellation monitoring for City Hotel bookings, which
    combine higher booking volume with a higher cancellation rate.
-   Monitor the Online TA channel because it contributes the largest
    booking volume.
-   Use historical monthly booking patterns to support operational
    planning.

## Repository Contents

``` text
Hotel-Booking-Cancellation-Analytics/
│
├── Hotel_Booking_Analytics.pbix
│
├── Dashboard_Screenshots/
│   ├── Booking_Performance.png
│   └── Cancellation_Analysis.png
│
└── README.md
```

## Notes and Limitations

-   The analysis describes patterns and associations in the available
    booking data; it does not establish causation.
-   Higher ADR does not necessarily mean higher profit. The dataset does
    not provide all costs needed for profitability analysis.
-   The dataset records arrival dates. Time-based visuals therefore
    analyze bookings by arrival date, not necessarily by the date on
    which a booking was created or cancelled.
-   The dataset's currency is not specified here, so ADR values are
    presented without a currency symbol.
-   The dataset covers historical bookings from July 2015 to August
    2017; findings should not be treated as current market conditions.

------------------------------------------------------------------------

**Project:** Hotel Booking & Cancellation Analytics\
**Tool:** Microsoft Power BI
