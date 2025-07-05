

---

### 1. Period-over-Period (PoP) Comparison Functions

*   **Core Concept:** The goal is to **compare** a value from one time period to the equivalent value in another time period. This is all about answering questions like:
    *   "How did our sales in April 2023 compare to our sales in **April 2022**?" (Year-over-Year)
    *   "How did our sales this quarter compare to the **previous quarter**?" (Quarter-over-Quarter)
*   **How They Work in DAX:** These functions are **filter modifiers**. They work inside a `CALCULATE` function. They take the current time period you are looking at in your report (we call this the "filter context") and they "travel back in time" to create a new, parallel filter for the previous period.
*   **Analogy:** Imagine you're looking at a calendar showing "April 2023". You ask a function like `SAMEPERIODLASTYEAR` to get the sales for the same period last year. The function doesn't calculate the sales; it simply points `CALCULATE` to a different set of dates on the calendar: "April 2022". `CALCULATE` then computes the `[Total Sales]` measure using that new set of dates.

#### Example Scenario:
You have a table visual showing sales by month.

| Month | Total Sales | Sales Last Year |
| :--- | :--- | :--- |
| Mar 2023 | $50,000 | $45,000 |
| Apr 2023 | $55,000 | $48,000 |
| May 2023 | $60,000 | $52,000 |

*   For the row **"Apr 2023"**:
    *   `Total Sales` is calculated using the filter context `Month = "Apr 2023"`.
    *   `Sales Last Year` is calculated using a measure like `CALCULATE([Total Sales], SAMEPERIODLASTYEAR(DimDate[Date]))`. For this row, `SAMEPERIODLASTYEAR` changes the filter context to `Month = "Apr 2022"`, and then `[Total Sales]` is calculated for that period.

*   **Functions in this group:** `DATEADD`, `SAMEPERIODLASTYEAR`, `PARALLELPERIOD`.

---

### 2. Period-to-Date (PTD) Aggregation Functions

*   **Core Concept:** The goal is to **accumulate** or create a **running total** from the beginning of a specific period (Year, Quarter, or Month) up to the current point in time. This answers questions like:
    *   "What are our total sales **so far this year**?" (Year-to-Date or YTD)
    *   "What is our profit **from the beginning of this quarter up to today**?" (Quarter-to-Date or QTD)
*   **How They Work in DAX:** Like the PoP functions, these are also **filter modifiers** used inside `CALCULATE`. However, instead of *shifting* the time period, they **expand** it. They take the last date in the current filter context and create a new filter that starts at the beginning of the period and ends on that last date.
*   **Analogy:** Imagine your report is filtered to a single day: **April 15, 2023**. If you use `DATESYTD`, it tells `CALCULATE`: "Ignore the fact that we're only looking at April 15th. Instead, I want you to calculate the total for the entire range of dates from **January 1, 2023, through April 15, 2023**."

#### Example Scenario:
You have a line chart showing sales by day.

*   A normal `[Total Sales]` measure would show a spiky line going up and down each day.
*   A `[Sales YTD]` measure would show a line that only ever goes up or stays flat, representing the cumulative total for the year. On January 1st, it equals the sales for that day. On January 2nd, it equals sales from day 1 + day 2. This continues until December 31st.

*   **Functions in this group:** `DATESYTD`, `DATESMTD`, `DATESQTD`. (And their cousins `TOTALYTD`, `TOTALMTD`, `TOTALQTD` which are just shorthand for `CALCULATE([Measure], DATESYTD(...))`).

---

### 3. Scalar Date Calculation Functions

*   **Core Concept:** These functions are fundamentally different. They are **not** filter modifiers. They perform a direct calculation and return a **single value** (a "scalar"), which is either a date or a number.
*   **How They Work in DAX:** They are simple calculators. You give them inputs, and they give you one output. They are most often used to create **calculated columns** in your data tables, or as an input to another function. They do **not** need to be wrapped in `CALCULATE` to work (though their results can be used inside one).
*   **Analogy:** Think of these like the basic functions on a calculator. `DATEDIFF` is like the subtraction button (`Date 2 - Date 1`). `EDATE` is like an "add months" button. They perform a straightforward operation and give you a result.

#### Example Scenario:
You have a `Sales` table with an `OrderDate` and a `ShipDate`.

1.  **To create a new column:** You want to know how many days it took to ship each order. You would add a calculated column to your `Sales` table:
    ```dax
    Days to Ship = DATEDIFF(Sales[OrderDate], Sales[ShipDate], DAY)
    ```
    This formula runs for each row, takes the two dates in that row, and calculates the difference, putting the resulting number in the new column.

2.  **To find a future date:** You want to calculate a warranty expiration date that is 2 years after the `OrderDate`. You add a calculated column:
    ```dax
    Warranty Expiration = EDATE(Sales[OrderDate], 24) -- 24 months
    ```

*   **Functions in this group:** `EDATE`, `EOMONTH`, `DATEDIFF`, `NOW()`, `TODAY()`, `YEAR()`, `MONTH()`, `DAY()`.

### Summary of Differences

| Characteristic       | Period-over-Period (PoP)                     | Period-to-Date (PTD)                        | Scalar Calculation                       |
| :------------------- | :------------------------------------------- | :------------------------------------------ | :--------------------------------------- |
| **Primary Goal**     | Comparison                                   | Accumulation / Running Total                | Direct Calculation                       |
| **Typical Use Case** | In Measures (YoY, QoQ)                       | In Measures (YTD, MTD)                      | In Calculated Columns                    |
| **How it Works**     | **Shifts** the filter context                | **Expands** the filter context              | Returns a single value (date/number)     |
| **Returns**          | A **Table** of dates                         | A **Table** of dates                        | A **Single Value** (Scalar)              |
| **DAX Context**      | Used inside `CALCULATE`                      | Used inside `CALCULATE`                     | Used standalone or as input              |
| **Example Question** | "How does this April compare to last April?" | "What are my total sales so far this year?" | "How many days between these two dates?" |
### Crucial Prerequisite: The Date Table

Before we start, know that **all effective time intelligence functions in DAX require a proper Date Table**. This table must:
1.  Have a column of data type `date`.
2.  Contain a continuous range of dates (no gaps), covering the full period of your data (e.g., from the first sale date to the last sale date).
3.  Be marked as a "Date Table" in your Power BI model.
4.  Have a one-to-many relationship from its date column to the date column in your fact table (e.g., `DimDate[Date]` -> `Sales[OrderDate]`).

In all examples below, we'll assume:
*   We have a Date table named `DimDate` with a column `DimDate[Date]`.
*   We have a base measure: `Total Sales = SUM(Sales[SalesAmount])`.

---

### Group 1: Period-over-Period Comparison Functions

These functions are used to compare a value in the current period to the same value in a previous (or future) period.

#### 1. `DATEADD`
*   **Purpose:** The most flexible function for shifting a period of time. It returns a table of dates shifted forward or backward by a specified number of intervals from the dates in the current context.
*   **Syntax:** `DATEADD(<dates>, <number_of_intervals>, <interval>)`
*   **Parameters:**
    *   `<dates>`: Your date column (`DimDate[Date]`).
    *   `<number_of_intervals>`: An integer. Negative for past, positive for future.
    *   `<interval>`: `DAY`, `MONTH`, `QUARTER`, `YEAR`.
*   **How it Works:** If your current filter context is **April 10 to April 20, 2023**, then `DATEADD(DimDate[Date], -1, MONTH)` will return a table of dates from **March 10 to March 20, 2023**. It shifts the exact period.
*   **Example:**
    ```dax
    -- Sales from the exact same period one month prior
    Sales Prior Month =
    CALCULATE(
        [Total Sales],
        DATEADD(DimDate[Date], -1, MONTH)
    )
    ```
*   **When to Use:** When you need full flexibility to go back or forward by any number of days, months, quarters, or years. This is the workhorse of period shifting.

---

#### 2. `SAMEPERIODLASTYEAR`
*   **Purpose:** A specialized and more readable shorthand for getting the same period in the previous year.
*   **Syntax:** `SAMEPERIODLASTYEAR(<dates>)`
*   **How it Works:** It's exactly equivalent to `DATEADD(<dates>, -1, YEAR)`. If your current context is **Q2 2023 (April 1 to June 30, 2023)**, this function returns a table of dates for **Q2 2022 (April 1 to June 30, 2022)**.
*   **Example:**
    ```dax
    -- Sales for the same period last year
    Sales SPLY =
    CALCULATE(
        [Total Sales],
        SAMEPERIODLASTYEAR(DimDate[Date])
    )
    ```
*   **When to Use:** Specifically for year-over-year (YoY) comparisons. It's less flexible than `DATEADD` but makes your code clearer for this common scenario.

---

#### 3. `PARALLELPERIOD`
*   **Purpose:** Returns a table containing a column of dates that represents a period *parallel* to the dates in the current context, but shifted by a number of intervals.
*   **The Critical Difference from `DATEADD`:** `PARALLELPERIOD` always returns **full periods**. `DATEADD` returns a shifted partial period if the current context is a partial period.
*   **Syntax:** `PARALLELPERIOD(<dates>, <number_of_intervals>, <interval>)`
*   **How it Works (The Key Comparison):**
    *   Assume your current filter context is **April 1 to April 15, 2023**.
    *   `DATEADD(DimDate[Date], -1, MONTH)` would return **March 1 to March 15, 2023**.
    *   `PARALLELPERIOD(DimDate[Date], -1, MONTH)` would return the **entire prior month: March 1 to March 31, 2023**.
*   **Example:**
    ```dax
    -- Sales for the entire previous quarter (useful for comparing a partial current quarter to a full previous one)
    Sales Prior Full Quarter =
    CALCULATE(
        [Total Sales],
        PARALLELPERIOD(DimDate[Date], -1, QUARTER)
    )
    ```
*   **When to Use:** When you need to compare a period (e.g., the current month-to-date) against a **complete** prior period (e.g., the entire previous month).

| Function | If Current Context is April 1-15, 2023 | Interval = -1 MONTH |
| :--- | :--- | :--- |
| `DATEADD` | Shifts the partial period | Returns **March 1-15, 2023** |
| `PARALLELPERIOD` | Shifts and returns the full period | Returns **March 1-31, 2023** |
| `SAMEPERIODLASTYEAR` | Not applicable for months, but if interval was -1 YEAR | Returns **April 1-15, 2022** |

---

### Group 2: Period-to-Date Aggregation Functions

These functions are used for calculating running totals, like Year-to-Date (YTD). They all return a table of dates that `CALCULATE` can use as a filter.

#### 4. `DATESYTD`, `DATESMTD`, `DATESQTD`
*   **Purpose:**
    *   `DATESYTD`: Returns a table of dates from the beginning of the year to the last date in the current context.
    *   `DATESMTD`: Returns a table of dates from the beginning of the month to the last date in the current context.
    *   `DATESQTD`: Returns a table of dates from the beginning of the quarter to the last date in the current context.
*   **Syntax:**
    *   `DATESYTD(<dates> [, <year_end_date>])`
    *   `DATESMTD(<dates>)`
    *   `DATESQTD(<dates>)`
*   **How it Works:** If the last date visible in your filter context is **April 15, 2023**:
    *   `DATESMTD` returns dates from **April 1, 2023 to April 15, 2023**.
    *   `DATESQTD` returns dates from **April 1, 2023 to April 15, 2023** (since April is the start of Q2).
    *   `DATESYTD` returns dates from **January 1, 2023 to April 15, 2023**.
*   **Example:**
    ```dax
    -- Sales Year-to-Date
    Sales YTD =
    CALCULATE(
        [Total Sales],
        DATESYTD(DimDate[Date])
    )

    -- For a fiscal year ending in June, you would write:
    Fiscal Sales YTD =
    CALCULATE(
        [Total Sales],
        DATESYTD(DimDate[Date], "6/30")
    )
    ```
*   **When to Use:** The standard and most efficient way to calculate YTD, QTD, and MTD values.

---

### Group 3: Scalar Date Calculation Functions

These functions return a **single date value (scalar)**, not a table of dates. They are often used in calculated columns or as inputs for other functions.

#### 5. `EDATE`
*   **Purpose:** Returns a date that is the specified number of months before or after a start date. It keeps the same day of the month, unless that day doesn't exist (e.g., Feb 30), in which case it returns the last day of the month.
*   **Syntax:** `EDATE(<start_date>, <months>)`
*   **Example (in a Calculated Column):** You want to find the warranty expiration date, which is 24 months after the purchase date.
    ```dax
    -- In the 'Sales' table
    Warranty Expiration = EDATE(Sales[OrderDate], 24)
    ```
    If `OrderDate` is `Jan 15, 2023`, this returns `Jan 15, 2025`.
    If `OrderDate` is `Feb 29, 2024` (leap year), `EDATE(..., 12)` returns `Feb 28, 2025`.

---

#### 6. `EOMONTH`
*   **Purpose:** Returns the date of the **last day of the month**, a specified number of months before or after a start date.
*   **Syntax:** `EOMONTH(<start_date>, <months>)`
*   **Example (in a Calculated Column):** Invoices are due at the end of the following month.
    ```dax
    -- In the 'Invoices' table
    Payment Due Date = EOMONTH(Invoices[InvoiceDate], 1)
    ```
    If `InvoiceDate` is `Jan 15, 2023`, this returns `Feb 28, 2023`.
*   **Comparison `EDATE` vs. `EOMONTH`:**
    *   `EDATE` tries to keep the day number.
    *   `EOMONTH` always jumps to the end of the target month.

---

#### 7. `DATEDIFF`
*   **Purpose:** Returns the count of specified interval **boundaries** crossed between two dates.
*   **Syntax:** `DATEDIFF(<start_date>, <end_date>, <interval>)`
*   **The "Boundaries" Nuance:** This is very important. `DATEDIFF` doesn't count the total elapsed time in that unit.
    *   `DATEDIFF("Dec 31, 2022", "Jan 1, 2023", YEAR)` returns **1**, because one year-end boundary was crossed, even though they are only one day apart.
    *   `DATEDIFF("Jan 1, 2023", "Jan 31, 2023", MONTH)` returns **0**. No month-end boundary was crossed.
    *   `DATEDIFF("Jan 1, 2023", "Feb 1, 2023", MONTH)` returns **1**.
*   **Example (in a Calculated Column):** Calculate the number of days it took to ship an order.
    ```dax
    -- In the 'Sales' table
    Days to Ship = DATEDIFF(Sales[OrderDate], Sales[ShipDate], DAY)
    ```
*   **When to Use:** For calculating durations like age, days to ship, or tenure in a specific unit (day, week, month, etc.). Be mindful of the boundary-crossing logic.

---

### Group 4: The Fundamental Building Block

#### 8. `DATESINPERIOD`
*   **Purpose:** The most fundamental "moving window" function. It returns a table of dates that begins at a specified `start_date` and continues for the specified number and type of intervals.
*   **Syntax:** `DATESINPERIOD(<dates>, <start_date>, <number_of_intervals>, <interval>)`
*   **How it Works:** You give it an anchor date (`start_date`) and tell it how far to go forward (positive number) or backward (negative number).
*   **Example:** A common use is for rolling/moving averages.
    ```dax
    -- Calculate sales over the last 30 days from whatever date is selected
    Sales Rolling 30 Days =
    CALCULATE(
        [Total Sales],
        DATESINPERIOD(
            DimDate[Date],
            MAX(DimDate[Date]), -- Anchor to the latest date in the current context
            -30,               -- Go back 30
            DAY                -- days
        )
    )
    ```
*   **When to Use:** For any custom moving window calculation (e.g., rolling 7-day average, 6-month sum, etc.). It is more explicit and flexible than `DATEADD` for this specific purpose because you explicitly define the anchor point.

### Summary Comparison Table

| Function                   | Returns              | Main Purpose                               | Key Differentiator                                                       |
| :------------------------- | :------------------- | :----------------------------------------- | :----------------------------------------------------------------------- |
| **`DATEADD`**              | Table of Dates       | Flexible period shifting (past/future)     | Shifts the exact partial/full period.                                    |
| **`SAMEPERIODLASTYEAR`**   | Table of Dates       | Year-over-Year (YoY) comparison            | Shorthand for `DATEADD(..., -1, YEAR)`. Very readable.                   |
| **`PARALLELPERIOD`**       | Table of Dates       | Period-over-period comparison              | Always returns **full** periods, even if current context is partial.     |
| **`DATESYTD / MTD / QTD`** | Table of Dates       | Period-to-date running totals              | Standard, optimized functions for YTD, MTD, QTD logic.                   |
| **`DATESINPERIOD`**        | Table of Dates       | Creating custom moving/rolling windows     | The most fundamental "window" function; requires an explicit start date. |
| **`EDATE`**                | Single Date (Scalar) | Find a date X months away                  | Returns the same day of the month (or last day if not possible).         |
| **`EOMONTH`**              | Single Date (Scalar) | Find the last day of a month X months away | Always returns the end of the month.                                     |
| **`DATEDIFF`**             | Number (Scalar)      | Calculate duration between two dates       | Counts interval **boundaries** crossed, not total elapsed time.          |
