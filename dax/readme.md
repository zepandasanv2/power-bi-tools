# DAX

A collection of reusable DAX formulas for data modeling, calculations, and analysis in Power BI.

## Available Scripts

### 1. Date Dimension

**File:** [date-dimension.dax](date-dimension.dax)

#### Description

Creates a date dimension table (`DimDate`) with calendar attributes for time-based analysis and reporting.

The table contains one row per day and includes year, quarter, month, week, day, and weekend information.

#### Usage

1. Open Power BI Desktop.
2. Navigate to **Modeling → New Table**.
3. Copy the formula from the `.dax` file.
4. Adjust `StartDate` and `EndDate` to match your reporting period.
5. Create a relationship between `DimDate[Date]` and the appropriate date column in your fact table.
6. Mark `DimDate` as a date table using the `Date` column when required.
7. Sort `Month Name` and `Month Short` by `Month Number`.

#### How It Works

- `CALENDAR()` generates a continuous range of dates.
- `ADDCOLUMNS()` adds calculated calendar attributes.
- `YEAR()`, `MONTH()`, `DAY()` and `QUARTER()` extract date components.
- `FORMAT()` generates English month and weekday names using `en-US`.
- `WEEKDAY()` identifies weekdays and weekends.
- `WEEKNUM()` calculates week numbers using Monday as the first day of the week.

#### Notes

- The default date range is January 1, 2020, to December 31, 2030.
- The date range can be customized.
- Week numbers use Monday as the first day of the week but do not follow the ISO 8601 week-numbering system.
- The `Date` column contains unique, consecutive dates without blanks.
- This table uses calendar years, starting in January and ending in December.

### 2. Date Difference

**File:** [date-difference.dax](date-difference.dax)

#### Description

Calculates the difference between two dates using the DAX `DATEDIFF()` function.

The interval can be configured to return the difference in years, quarters, months, weeks, days, hours, minutes, or seconds.

#### Example

| StartDate | EndDate | Result (DAY) |
|---|---|---|
| 2026-10-01 | 2026-10-13 | 12 |
| 2026-01-01 | 2026-01-31 | 30 |
| 2026-10-15 | 2026-10-13 | -2 |

#### Usage

1. Open Power BI Desktop.
2. Navigate to **Modeling → New Column**.
3. Copy the formula from the `.dax` file.
4. Replace `'Table'[StartDate]` and `'Table'[EndDate]` with your column references.
5. Change the interval (`DAY`, `MONTH`, `YEAR`, etc.) if necessary.

#### How It Works

The `DATEDIFF()` function takes three arguments:

- `StartDate`: The initial date or datetime.
- `EndDate`: The final date or datetime.
- `Interval`: The unit used to calculate the difference.

The function returns the number of interval boundaries crossed between the two values.

#### Notes

- The result is positive when the end date is later than the start date.
- The result is negative when the end date is earlier than the start date.
- The function counts interval boundaries, not necessarily complete elapsed periods.
- Both columns should use a valid Date or Date/Time data type.
- The formula is intended for a calculated column; it can also be adapted for measures.