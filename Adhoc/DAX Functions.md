# 1. Aggregation Functions

**Sample Table: `Sales`**

| Product | Sales Amount | Quantity | Status | Unit Cost |
| :--- | :--- | :--- | :--- | :--- |
| Book | 15.00 | 2 | Shipped | 5.00 |
| Pen | 2.50 | 5 | Shipped | 0.50 |
| Paper | 10.00 | 1 | Pending | 8.00 |
| Book | 15.00 | 3 | Shipped | 5.00 |
| Eraser | | 10 | Pending | 0.25 |
| Ink | 20.00 | 2 | Canceled | 10.00 |
| Pen | 2.50 | | Shipped | 0.50 |

---

### **1. AVERAGE**
*   **Definition:** Calculates the arithmetic mean (average) of all numbers in a column. It ignores blank cells, text, and logical values.
*   **Syntax:** `AVERAGE(<column>)`
*   **Example:** To find the average sales amount.
    ```dax
    Average Sales = AVERAGE(Sales[Sales Amount])
    ```
    **Result:** 12.5. (Calculated as `(15.00 + 2.50 + 10.00 + 15.00 + 20.00) / 5`). The blank cell for "Eraser" is ignored.

### **2. AVERAGEA**
*   **Definition:** Calculates the average of values in a column. Unlike `AVERAGE`, it handles non-numeric data: text values are treated as `0`, the logical value `TRUE` is `1`, and `FALSE` is `0`. It still ignores blank cells.
*   **Syntax:** `AVERAGEA(<column>)`
*   **Example:** Imagine a column `TestScores` with values `[100, 80, "Absent", 90, BLANK]`.
    ```dax
    Average Score = AVERAGEA(TestScores)
    ```
    **Result:** 67.5. (Calculated as `(100 + 80 + 0 + 90) / 4`). The text "Absent" is counted as 0, and the `BLANK` is ignored.

### **3. COUNT**
*   **Definition:** Counts only the numeric values in a column.
*   **Syntax:** `COUNT(<column>)`
*   **Example:** To count how many sales transactions have a recorded sales amount.
    ```dax
    Count of Sales = COUNT(Sales[Sales Amount])
    ```
    **Result:** 5. (It counts the 5 numeric values and ignores the blank cell).

### **4. COUNTA**
*   **Definition:** Counts the number of cells in a column that are not empty. This includes numbers, text, dates, errors, etc.
*   **Syntax:** `COUNTA(<column>)`
*   **Example:** To count the number of items that have a recorded quantity.
    ```dax
    Count of Items with Quantity = COUNTA(Sales[Quantity])
    ```
    **Result:** 6. (It counts all cells with a value and ignores the one blank cell for "Pen").

### **5. COUNTBLANK**
*   **Definition:** Counts the number of blank cells in a column.
*   **Syntax:** `COUNTBLANK(<column>)`
*   **Example:** To find how many items are missing a `Sales Amount`.
    ```dax
    Missing Sales Amount = COUNTBLANK(Sales[Sales Amount])
    ```
    **Result:** 1. (It finds the one blank cell in the "Eraser" row).

### **6. COUNTROWS**
*   **Definition:** Counts the total number of rows in a table.
*   **Syntax:** `COUNTROWS(<table>)`
*   **Example:** To count the total number of orders in the sales table.
    ```dax
    Total Orders = COUNTROWS(Sales)
    ```
    **Result:** 7.

### **7. DISTINCTCOUNT**
*   **Definition:** Counts the number of unique (distinct) values in a column. A blank value is counted as one of the distinct values if it exists.
*   **Syntax:** `DISTINCTCOUNT(<column>)`
*   **Example:** To find the number of unique products sold.
    ```dax
    Unique Products Sold = DISTINCTCOUNT(Sales[Product])
    ```
    **Result:** 5. (The distinct values are "Book", "Pen", "Paper", "Eraser", and "Ink").

### **8. DISTINCTCOUNTNOBLANK**
*   **Definition:** Counts the number of unique (distinct) non-blank values in a column.
*   **Syntax:** `DISTINCTCOUNTNOBLANK(<column>)`
*   **Example:** To count the unique sales amounts, excluding any missing values.
    ```dax
    Unique Sales Values = DISTINCTCOUNTNOBLANK(Sales[Sales Amount])
    ```
    **Result:** 4. (The distinct values are 15.00, 2.50, 10.00, and 20.00. The blank is not counted).

### **9. MAX**
*   **Definition:** Returns the largest numeric value in a column. Ignores text and logical values.
*   **Syntax:** `MAX(<column>)`
*   **Example:** To find the highest sales amount for a single transaction.
    ```dax
    Highest Sale = MAX(Sales[Sales Amount])
    ```
    **Result:** 20.00.

### **10. MAXA**
*   **Definition:** Returns the largest value in a column. It compares numbers and logical values (`TRUE` = 1, `FALSE` = 0).
*   **Syntax:** `MAXA(<column>)`
*   **Example:** On a purely numeric column like `Sales Amount`, `MAXA` returns the same result as `MAX`. The difference appears when logical values are present. If a column `TestValues` contained `[5, 10, TRUE]`, `MAXA(TestValues)` would return `10`. If the column contained `[-2, -5, FALSE]`, `MAXA` would return `0` (since `FALSE` is treated as 0).

### **11. MIN**
*   **Definition:** Returns the smallest numeric value in a column. Ignores text and logical values.
*   **Syntax:** `MIN(<column>)`
*   **Example:** To find the lowest sales amount for a single transaction.
    ```dax
    Lowest Sale = MIN(Sales[Sales Amount])
    ```
    **Result:** 2.50.

### **12. MINA**
*   **Definition:** Returns the smallest value in a column. It compares numbers and logical values (`TRUE` = 1, `FALSE` = 0).
*   **Syntax:** `MINA(<column>)`
*   **Example:** If a column `TestValues` contained `[5, 2, TRUE]`, `MINA(TestValues)` would return `1` (since `TRUE` is treated as 1, which is smaller than 2). If a column `Unit Cost` contained `[0.50, 0.25, FALSE]`, `MINA` would return `0`.

### **13. PRODUCT**
*   **Definition:** Multiplies all the numbers in a column and returns the product. It ignores non-numeric values and blanks.
*   **Syntax:** `PRODUCT(<column>)`
*   **Example:** To calculate the product of all recorded quantities.
    ```dax
    Product of Quantities = PRODUCT(Sales[Quantity])
    ```
    **Result:** 600. (Calculated as `2 * 5 * 1 * 3 * 10 * 2`).

### **14. SUM**
*   **Definition:** Adds all the numbers in a column. It ignores text and blank cells.
*   **Syntax:** `SUM(<column>)`
*   **Example:** To calculate the total revenue from all sales.
    ```dax
    Total Sales = SUM(Sales[Sales Amount])
    ```
    **Result:** 62.50. (Calculated as `15.00 + 2.50 + 10.00 + 15.00 + 20.00`).


# 2. Iterator (...X) Functions

**Sample Table: `Sales`**

| Product | Sales Amount | Quantity | Unit Cost |
| :--- | :--- | :--- | :--- |
| Book | 15.00 | 2 | 5.00 |
| Pen | 2.50 | 5 | 0.50 |
| Paper | 10.00 | 1 | 8.00 |
| Book | 15.00 | 3 | 5.00 |
| Eraser | | 10 | 0.25 |
| Ink | 20.00 | 2 | 10.00 |
| Pen | 2.50 | | 0.50 |


### **1. AVERAGEX**
*   **Definition:** Iterates through a table, evaluates an expression for each row, and then calculates the arithmetic mean (average) of the results. It ignores any results that are not numbers.
*   **Syntax:** `AVERAGEX(<table>, <expression>)`
*   **Example:** To find the average revenue per order line, which is `Quantity` multiplied by `Unit Cost`.
    ```dax
    Average Revenue Per Line = AVERAGEX(Sales, Sales[Quantity] * Sales[Unit Cost])
    ```
    **How it works:**
    1.  It creates a temporary list of values: `[10.00, 2.50, 8.00, 15.00, 2.50, 20.00, BLANK]`.
    2.  It calculates the average of these numbers: `(10.00 + 2.50 + 8.00 + 15.00 + 2.50 + 20.00) / 6 = 9.67`.

### **2. COUNTX**
*   **Definition:** Iterates through a table, evaluates an expression for each row, and counts how many of the results are numbers.
*   **Syntax:** `COUNTX(<table>, <expression>)`
*   **Example:** To count how many order lines have a `Sales Amount` greater than `10`.
    ```dax
    Count of Large Sales = COUNTX(Sales, IF(Sales[Sales Amount] > 10, Sales[Sales Amount], BLANK()))
    ```
    **How it works:**
    1.  It evaluates the `IF` statement for each row, creating a temporary list: `[15.00, BLANK, BLANK, 15.00, BLANK, 20.00, BLANK]`.
    2.  It counts the numeric values in that list.
    **Result:** 3.

### **3. COUNTAX**
*   **Definition:** Iterates through a table, evaluates an expression for each row, and counts how many of the results are not blank (includes numbers, text, errors, etc.).
*   **Syntax:** `COUNTAX(<table>, <expression>)`
*   **Example:** To count how many rows have a calculated revenue (`Quantity * Unit Cost`).
    ```dax
    Count of Lines with Revenue = COUNTAX(Sales, Sales[Quantity] * Sales[Unit Cost])
    ```
    **How it works:**
    1.  It creates the temporary list: `[10.00, 2.50, 8.00, 15.00, 2.50, 20.00, BLANK]`.
    2.  It counts all the non-blank results.
    **Result:** 6.

### **4. GEOMEANX**
*   **Definition:** Iterates through a table, evaluates an expression for each row, and returns the geometric mean of the results. The geometric mean is often used for data that represents rates of change or growth factors.
*   **Syntax:** `GEOMEANX(<table>, <expression>)`
*   **Example:** Suppose you have a table `InvestmentReturns` with a column `GrowthFactor` (`[1.05, 1.02, 1.08]`).
    ```dax
    Average Compounded Growth = GEOMEANX(InvestmentReturns, [GrowthFactor])
    ```
    **Result:** It would calculate `(1.05 * 1.02 * 1.08)^(1/3)`. This gives a more accurate average growth rate than a simple `AVERAGE`.

### **5. MAXX**
*   **Definition:** Iterates through a table, evaluates an expression for each row, and returns the largest value from the results.
*   **Syntax:** `MAXX(<table>, <expression>)`
*   **Example:** To find the highest revenue from any single order line.
    ```dax
    Highest Revenue Per Line = MAXX(Sales, Sales[Quantity] * Sales[Unit Cost])
    ```
    **How it works:**
    1.  It creates the temporary list of revenues: `[10.00, 2.50, 8.00, 15.00, 2.50, 20.00, BLANK]`.
    2.  It finds the maximum value in that list.
    **Result:** 20.00.

### **6. MINX**
*   **Definition:** Iterates through a table, evaluates an expression for each row, and returns the smallest value from the results.
*   **Syntax:** `MINX(<table>, <expression>)`
*   **Example:** To find the lowest revenue from any single order line (that had revenue).
    ```dax
    Lowest Revenue Per Line = MINX(Sales, Sales[Quantity] * Sales[Unit Cost])
    ```
    **How it works:**
    1.  It creates the same temporary list: `[10.00, 2.50, 8.00, 15.00, 2.50, 20.00, BLANK]`.
    2.  It finds the minimum value in that list.
    **Result:** 2.50.

### **7. PRODUCTX**
*   **Definition:** Iterates through a table, evaluates an expression for each row, and returns the product (multiplication) of all the results.
*   **Syntax:** `PRODUCTX(<table>, <expression>)`
*   **Example:** To calculate the product of all `Unit Costs` for items with a quantity greater than 1.
    ```dax
    Product of Costs (Qty > 1) = PRODUCTX(FILTER(Sales, Sales[Quantity] > 1), Sales[Unit Cost])
    ```
    **How it works:**
    1.  `FILTER` creates a temporary table of rows where `Quantity` > 1 (Book, Pen, Book, Eraser, Ink).
    2.  `PRODUCTX` iterates this temporary table and gets the `Unit Cost` for each: `[5.00, 0.50, 5.00, 0.25, 10.00]`.
    3.  It multiplies them: `5.00 * 0.50 * 5.00 * 0.25 * 10.00`.
    **Result:** 31.25.

### **8. RANKX**
*   **Definition:** A powerful iterator that returns the ranking of a number in a list. It can be used to rank customers, products, etc., based on a measure.
*   **Syntax:** `RANKX(<table>, <expression>, [<value>], [<order>], [<ties>])`
*   **Example:** To rank each product based on its total sales amount, from highest to lowest.
    ```dax
    // First, create a base measure for total sales
    Total Sales = SUM(Sales[Sales Amount])
    
    // Then, create the ranking measure
    Product Rank = 
    RANKX(
        ALL(Sales[Product]), 
        [Total Sales], 
        , 
        DESC, 
        DENSE
    )
    ```
    **How it works:**
    *   `ALL(Sales[Product])`: This creates a table of all unique products, removing any filters from the visual. This is the list we rank *within*.
    *   `[Total Sales]`: This is the expression we are ranking. For each product in the list, DAX calculates its total sales.
    *   `DESC`: We want descending order (highest sales get rank 1).
    *   `DENSE`: This handles ties. If two products have the same rank (e.g., 3), the next product will be rank 4. (The alternative, `SKIP`, would make the next rank 5).

### **9. SUMX**
*   **Definition:** The most common iterator function. It iterates through a table, evaluates an expression for each row, and then adds up (sums) all the results.
*   **Syntax:** `SUMX(<table>, <expression>)`
*   **Example:** This is the canonical example for calculating total revenue when you only have `Quantity` and `Unit Cost`.
    ```dax
    Total Revenue = SUMX(Sales, Sales[Quantity] * Sales[Unit Cost])
    ```
    **How it works:**
    1.  It iterates the `Sales` table row by row, multiplying `Quantity` by `Unit Cost` each time.
    2.  It creates a temporary, in-memory list of results: `[10.00, 2.50, 8.00, 15.00, 2.50, 20.00, BLANK]`.
    3.  It sums the values in that list.
    **Result:** 58.00.


# 3. Filter and Evaluation Functions

**Table: `Sales`**


![[Assets/da07f5559f76624ac15d94f1d8287657_MD5.jpeg]]

**Table: `Products`** (Related to `Sales` on `ProductKey`)

![[Assets/2b8ebab583aeb71ae67b9129cef8500f_MD5.jpeg]]

---

### **1. CALCULATE**
*   **Definition:** The most important function in DAX. It evaluates an expression in a modified filter context. It is the only function that can change the context in which a calculation occurs.
*   **Syntax:** `CALCULATE(<expression>, [<filter1>], [<filter2>]…)`
*   **Example:** To calculate sales for only the "Electronics" category, ignoring any other category filters.
    ```dax
    Electronics Sales = CALCULATE(
        SUM(Sales[Sales Amount]),
        Products[Category] = "Electronics"
    )
    ```
    **Result:** 470 (150 + 200 + 120). This formula takes the sum of sales but applies a *new* filter where the category must be "Electronics".

### **2. ALL**
*   **Definition:** A table function that removes all filters from the specified table or columns. It's most often used inside `CALCULATE` to compute grand totals or percentages.
*   **Syntax:** `ALL(<table> or <column1>, [<column2>]…)`
*   **Example:** To calculate the percentage of total sales.
    ```dax
    // Base measure
    Total Sales = SUM(Sales[Sales Amount])
    
    // % of Grand Total measure
    % of All Sales = DIVIDE(
        [Total Sales],
        CALCULATE([Total Sales], ALL(Sales))
    )
    ```
    **How it works:** If you have a visual filtered by "Apparel", `[Total Sales]` would be 50. The `CALCULATE([Total Sales], ALL(Sales))` part calculates the sales for *all* products (520), because `ALL(Sales)` removes the "Apparel" filter. The result would be `50 / 520`.

### **3. ALLEXCEPT**
*   **Definition:** Removes all context filters from a table *except* for filters that have been applied to the specified columns. It's a shortcut.
*   **Syntax:** `ALLEXCEPT(<table>, <column_to_keep_filter_on1>, ...)`
*   **Example:** To calculate the percentage of category total.
    ```dax
    % of Category Sales = DIVIDE(
        [Total Sales],
        CALCULATE([Total Sales], ALLEXCEPT(Products, Products[Category]))
    )
    ```
    **How it works:** In a visual with `Category` and `Product Name`, this formula calculates each product's sales as a percentage of its category total. `ALLEXCEPT` removes the filter on `Product Name` but *keeps* the filter on `Category`.

### **4. ALLSELECTED**
*   **Definition:** Removes context filters from columns and rows in the current query, while retaining all other context filters or explicit filters (like from slicers). This is useful for calculating the percentage of a visual's total.
*   **Syntax:** `ALLSELECTED(<table> or <column>)`
*   **Example:** To calculate the percentage of the visible total in a chart.
    ```dax
    % of Visible Total = DIVIDE(
        [Total Sales],
        CALCULATE([Total Sales], ALLSELECTED(Products))
    )
    ```
    **How it works:** If you have a slicer for `Color` and select "Silver" and "Black", and a chart shows sales by `Product Name`, `ALLSELECTED` will use the total for just Silver and Black products as the denominator, ignoring the filtering that happens inside the chart.

### **5. FILTER**
*   **Definition:** A table function that returns a table representing a subset of another table or expression. It is an iterator and is often used inside `CALCULATE` to apply complex filtering conditions.
*   **Syntax:** `FILTER(<table>, <filter_expression>)`
*   **Example:** To calculate sales for transactions with a `Sales Amount` greater than 100.
    ```dax
    Sales for Large Orders = CALCULATE(
        SUM(Sales[Sales Amount]),
        FILTER(
            Sales,
            Sales[Sales Amount] > 100
        )
    )
    ```
    **Result:** 470 (150 + 200 + 120). `FILTER` creates a temporary table of sales rows that meet the condition, and `CALCULATE` then sums the sales for that temporary table.

### **6. KEEPFILTERS**
*   **Definition:** A modifier used inside `CALCULATE` that changes how filters are applied. Instead of overwriting the existing filter context, it creates an intersection of the existing context and the new filter.
*   **Syntax:** `KEEPFILTERS(<filter_expression>)`
*   **Example:** Imagine you have a slicer on `Color` and select "Silver". A normal measure for "Blue Sales" would be `CALCULATE(SUM(Sales[Sales Amount]), Products[Color] = "Blue")`. This would show the sales for Blue products, ignoring your "Silver" selection. But if you use `KEEPFILTERS`:
    ```dax
    Blue Sales (Filtered) = CALCULATE(
        SUM(Sales[Sales Amount]),
        KEEPFILTERS(Products[Color] = "Blue")
    )
    ```
    **Result:** This will be BLANK because it tries to find products that are *both* "Silver" (from the slicer) *and* "Blue" (from the formula), which is an empty set.

### **7. REMOVEFILTERS**
*   **Definition:** This is a modern, more readable synonym for the `ALL` function. It removes filters from the specified tables or columns.
*   **Syntax:** `REMOVEFILTERS(<table> or <column1>, ...)`
*   **Example:** The `% of All Sales` example can be rewritten for clarity:
    ```dax
    % of All Sales = DIVIDE(
        [Total Sales],
        CALCULATE([Total Sales], REMOVEFILTERS(Sales))
    )
    ```
    It functions identically to `ALL`.

### **8. SELECTEDVALUE**
*   **Definition:** A very convenient function that checks if there is only one distinct value for a column in the current filter context. If so, it returns that value; otherwise, it returns a specified alternate result (or BLANK).
*   **Syntax:** `SELECTEDVALUE(<columnName>, [<alternateResult>])`
*   **Example:** Creating a dynamic title for a card or visual.
    ```dax
    Dynamic Card Title = "Sales for " & SELECTEDVALUE(Products[Category], "All Categories")
    ```
    **How it works:** If you click on "Electronics" in a slicer, the title will be "Sales for Electronics". If no single category is selected, it will be "Sales for All Categories".

### **9. LOOKUPVALUE**
*   **Definition:** Retrieves a value from a column in a table when it finds a matching value in another column. It's similar to VLOOKUP in Excel and does not require a formal relationship between tables.
*   **Syntax:** `LOOKUPVALUE(<result_columnName>, <search_columnName>, <search_value>, ...)`
*   **Example:** To get the product `Category` in a calculated column within the `Sales` table.
    ```dax
    // This is a calculated column in the 'Sales' table
    Product Category = LOOKUPVALUE(
        Products[Category],
        Products[ProductKey],
        Sales[ProductKey]
    )
    ```
    **Result:** The `Sales` table will now have a new column showing "Electronics", "Electronics", "Apparel", "Electronics" for each row.

---


*   **CALCULATETABLE:** Same as `CALCULATE`, but it returns a table instead of a single value.
*   **ALLCROSSFILTERED:** Removes filters from tables that are on the "many" side of a relationship, used for specific relationship modeling.
*   **ALLNOBLANKROW:** Used to remove the special "blank row" that DAX adds to dimension tables to handle data integrity issues.
*   **EARLIER / EARLIEST:** Used to access an "outer row context" during nested iterations (e.g., in complex calculated columns). Modern DAX often uses variables (`VAR`) instead, which are easier to read and more efficient.


# 4. Time Intelligence Functions


### **Closing Balance Functions**
These are for semi-additive measures (like inventory or account balances), where you need the value at the very end of a period, not the sum over the period.

#### 1. CLOSINGBALANCEMONTH
*   **Definition:** Evaluates an expression at the last date of the month in the current context.
*   **Syntax:** `CLOSINGBALANCEMONTH(<expression>, <dates>, [<filter>])`
*   **Example:** To get the inventory count at the end of the month.
    ```dax
    Inventory End of Month = CLOSINGBALANCEMONTH(SUM(Inventory[StockCount]), 'Date'[Date])
    ```

#### 2. CLOSINGBALANCEQUARTER
*   **Definition:** Evaluates an expression at the last date of the quarter.
*   **Syntax:** `CLOSINGBALANCEQUARTER(<expression>, <dates>, [<filter>])`
*   **Example:** To get the account balance at the end of the quarter.
    ```dax
    Account Balance EOQ = CLOSINGBALANCEQUARTER(SUM(Accounts[Balance]), 'Date'[Date])
    ```

#### 3. CLOSINGBALANCEYEAR
*   **Definition:** Evaluates an expression at the last date of the year.
*   **Syntax:** `CLOSINGBALANCEYEAR(<expression>, <dates>, [<filter>], [<year_end_date>])`
*   **Example:** To get the total number of active subscribers at year-end.
    ```dax
    Subscribers EOY = CLOSINGBALANCEYEAR(COUNT(Subscribers[SubID]), 'Date'[Date], "12-31")
    ```

---

### **Date Table Manipulation Functions**

#### 4. DATEADD
*   **Definition:** Returns a table containing a column of dates, shifted either forward or backward in time by the specified number of intervals from the dates in the current context.
*   **Syntax:** `DATEADD(<dates>, <number_of_intervals>, <interval>)` where `interval` is DAY, MONTH, QUARTER, or YEAR.
*   **Example:** To calculate sales from the previous month.
    ```dax
    Sales Previous Month = CALCULATE([Total Sales], DATEADD('Date'[Date], -1, MONTH))
    ```

#### 5. DATESBETWEEN
*   **Definition:** Returns a table that contains a column of dates that begins with a specified start date and continues until a specified end date.
*   **Syntax:** `DATESBETWEEN(<dates>, <start_date>, <end_date>)`
*   **Example:** To get sales for a fixed period (Q1 2023).
    ```dax
    Q1 2023 Sales = CALCULATE([Total Sales], DATESBETWEEN('Date'[Date], "2023-01-01", "2023-03-31"))
    ```

#### 6. DATESINPERIOD
*   **Definition:** Returns a table containing a column of dates that begins with a start date and continues for the specified number of intervals. Excellent for rolling averages.
*   **Syntax:** `DATESINPERIOD(<dates>, <start_date>, <number_of_intervals>, <interval>)`
*   **Example:** To calculate a rolling 90-day sales total.
    ```dax
    Rolling 90 Day Sales = CALCULATE([Total Sales], DATESINPERIOD('Date'[Date], LASTDATE('Date'[Date]), -90, DAY))
    ```

#### 7. DATESMTD / 8. DATESQTD / 9. DATESYTD
*   **Definition:** These functions return a table that contains a column of dates for the month, quarter, or year to date, in the current context. They are the engines behind the `TOTALMTD/QTD/YTD` functions.
*   **Syntax:** `DATESMTD(<dates>)`, `DATESQTD(<dates>)`, `DATESYTD(<dates>)`
*   **Example:** The long-form way to write a Year-to-Date calculation.
    ```dax
    Sales YTD (Long Form) = CALCULATE([Total Sales], DATESYTD('Date'[Date]))
    ```

#### 10. ENDOFMONTH / 11. ENDOFQUARTER / 12. ENDOFYEAR
*   **Definition:** Returns the last date of the month, quarter, or year in the current context.
*   **Syntax:** `ENDOFMONTH(<dates>)`, `ENDOFQUARTER(<dates>)`, `ENDOFYEAR(<dates>)`
*   **Example:** To find the last date of the current quarter.
    ```dax
    Last Day of Quarter = ENDOFQUARTER('Date'[Date])
    ```

#### 13. FIRSTDATE / 14. LASTDATE
*   **Definition:** Returns the first or last date in the current filter context for the specified column of dates.
*   **Syntax:** `FIRSTDATE(<dates>)`, `LASTDATE(<dates>)`
*   **Example:** To show the last date a sale was made in the selected period.
    ```dax
    Last Sale Date in Period = LASTDATE(Sales[OrderDate])
    ```

#### 15. FIRSTNONBLANK / 16. LASTNONBLANK
*   **Definition:** Returns the first/last value in a column, filtered by the first/last date for which a given expression is not blank.
*   **Syntax:** `FIRSTNONBLANK(<column>, <expression>)`
*   **Example:** To find the sales amount on the very last day that had any sales.
    ```dax
    Sales on Last Activity Date = CALCULATE([Total Sales], LASTNONBLANK('Date'[Date], [Total Sales]))
    ```

#### 17. NEXTDAY / 18. NEXTMONTH / 19. NEXTQUARTER / 20. NEXTYEAR
*   **Definition:** Returns a table that contains a column of all dates from the next day, month, quarter, or year, based on the last date in the input column.
*   **Syntax:** `NEXTMONTH(<dates>)`
*   **Example:** To calculate sales for the next month.
    ```dax
    Sales Next Month = CALCULATE([Total Sales], NEXTMONTH('Date'[Date]))
    ```

---

### **Opening Balance Functions**
The opposite of Closing Balance; these find the value at the *start* of a period.

#### 21. OPENINGBALANCEMONTH
*   **Definition:** Evaluates an expression at the last date of the *previous* month.
*   **Syntax:** `OPENINGBALANCEMONTH(<expression>, <dates>, [<filter>])`
*   **Example:** To get the inventory count at the start of the month.
    ```dax
    Inventory Start of Month = OPENINGBALANCEMONTH(SUM(Inventory[StockCount]), 'Date'[Date])
    ```

#### 22. OPENINGBALANCEQUARTER
*   **Definition:** Evaluates an expression at the last date of the *previous* quarter.
*   **Syntax:** `OPENINGBALANCEQUARTER(<expression>, <dates>, [<filter>])`
*   **Example:** To get the account balance at the start of the quarter.
    ```dax
    Account Balance SOQ = OPENINGBALANCEQUARTER(SUM(Accounts[Balance]), 'Date'[Date])
    ```

#### 23. OPENINGBALANCEYEAR
*   **Definition:** Evaluates an expression at the last date of the *previous* year.
*   **Syntax:** `OPENINGBALANCEYEAR(<expression>, <dates>, [<filter>], [<year_end_date>])`
*   **Example:** To get the number of subscribers at the start of the year.
    ```dax
    Subscribers SOY = OPENINGBALANCEYEAR(COUNT(Subscribers[SubID]), 'Date'[Date], "12-31")
    ```

---

### **Period Comparison and Shifting**

#### 24. PARALLELPERIOD
*   **Definition:** Returns a table that contains a column of dates that represents a period parallel to the dates in the specified dates column, in the current context, with the dates shifted a number of intervals.
*   **Syntax:** `PARALLELPERIOD(<dates>, <number_of_intervals>, <interval>)`
*   **Example:** To get sales for the full corresponding month from the previous year.
    ```dax
    Sales Parallel Period Last Year = CALCULATE([Total Sales], PARALLELPERIOD('Date'[Date], -1, YEAR))
    ```

#### 25. PREVIOUSDAY / 26. PREVIOUSMONTH / 27. PREVIOUSQUARTER / 28. PREVIOUSYEAR
*   **Definition:** Returns a table that contains a column of all dates from the previous day, month, quarter, or year.
*   **Syntax:** `PREVIOUSMONTH(<dates>)`
*   **Example:** To get sales for the entire previous quarter.
    ```dax
    Sales Previous Quarter = CALCULATE([Total Sales], PREVIOUSQUARTER('Date'[Date]))
    ```

#### 29. SAMEPERIODLASTYEAR
*   **Definition:** A very common and convenient function that returns a table of dates shifted one year back in time from the dates in the current context. It's perfect for Year-over-Year (YoY) growth calculations.
*   **Syntax:** `SAMEPERIODLASTYEAR(<dates>)`
*   **Example:** To calculate sales for the same period in the prior year.
    ```dax
    Sales Last Year = CALCULATE([Total Sales], SAMEPERIODLASTYEAR('Date'[Date]))
    ```

#### 30. STARTOFMONTH / 31. STARTOFQUARTER / 32. STARTOFYEAR
*   **Definition:** Returns the first date of the month, quarter, or year in the current context.
*   **Syntax:** `STARTOFMONTH(<dates>)`, `STARTOFQUARTER(<dates>)`, `STARTOFYEAR(<dates>)`
*   **Example:** To find the first date of the current year.
    ```dax
    First Day of Year = STARTOFYEAR('Date'[Date])
    ```

---

### **Cumulative Totals (Syntactic Sugar)**
These are easy-to-use shortcut functions for the most common cumulative calculations.

#### 33. TOTALMTD / 34. TOTALQTD / 35. TOTALYTD
*   **Definition:** Evaluates the value of an expression for the month-to-date, quarter-to-date, or year-to-date.
*   **Syntax:** `TOTALMTD(<expression>, <dates>, [<filter>])`
*   **Example:** The simplest way to calculate Year-to-Date sales.
    ```dax
    Sales YTD = TOTALYTD([Total Sales], 'Date'[Date])
    ```


# 5. Logical Functions


**Sample Table: `Sales`**


![[Assets/a552bd14dd01705849b8f882b3cf0743_MD5.jpeg]]



### 1. AND
*   **Definition:** Checks whether both arguments are TRUE, and returns TRUE if both are TRUE. Otherwise, it returns FALSE. The `&&` operator is a common equivalent.
*   **Syntax:** `AND(<logical1>, <logical2>)` or `[Condition1] && [Condition2]`
*   **Example:** Create a calculated column to identify "High-Value Electronics".
    ```dax
    High-Value Electronics = 
    AND(
        Sales[Category] = "Electronics",
        Sales[Sales Amount] > 1000
    )
    
    // Using the operator (more common)
    High-Value Electronics = (Sales[Category] = "Electronics") && (Sales[Sales Amount] > 1000)
    ```
    **Result:** This column will be TRUE only for the "Laptop" row.

### 2. COALESCE
*   **Definition:** Returns the first expression in a list that does not evaluate to BLANK. If all expressions evaluate to BLANK, it returns BLANK. It's excellent for handling missing data from multiple sources.
*   **Syntax:** `COALESCE(<expression1>, <expression2>, ...)`
*   **Example:** Create a column to show the `Profit`, but if `Profit` is blank, show `0`.
    ```dax
    Profit Or Zero = COALESCE(Sales[Profit], 0)
    ```
    **Result:** For the "Monitor" row, this will return `0` instead of `BLANK()`.

### 3. FALSE
*   **Definition:** Simply returns the logical value `FALSE`.
*   **Syntax:** `FALSE()`
*   **Example:** Often used for readability or to force a specific outcome in another function.
    ```dax
    Is Not Stationery = IF(Sales[Category] = "Stationery", FALSE(), TRUE())
    ```
    While you could just write `Sales[Category] <> "Stationery"`, using `TRUE()`/`FALSE()` can sometimes make complex nested `IF` statements clearer.

### 4. IF
*   **Definition:** The most common conditional function. It checks a condition, and returns one value if the condition is TRUE, and another value if it's FALSE. It uses "lazy evaluation," meaning it only executes the branch (true or false) that is chosen.
*   **Syntax:** `IF(<logical_test>, <value_if_true>, <value_if_false>)`
*   **Example:** Categorize sales size.
    ```dax
    Sales Size = IF(Sales[Sales Amount] > 100, "Large", "Small")
    ```
    **Result:** This returns "Large" for Laptop and Monitor, and "Small" for the rest.

### 5. IF.EAGER
*   **Definition:** Identical in syntax to `IF`, but it uses "eager evaluation." This means it *always executes both* the `value_if_true` and `value_if_false` expressions, regardless of the condition's outcome. This can cause performance issues or errors that a standard `IF` would avoid.
*   **Syntax:** `IF.EAGER(<logical_test>, <value_if_true>, <value_if_false>)`
*   **Example:** Consider a profit margin calculation.
    ```dax
    // This will cause an error on the "Ink" row because 10 / BLANK() is an error.
    // IF.EAGER evaluates the division even when the condition is false.
    Eager Margin = IF.EAGER(Sales[Sales Amount] = 0, 0, Sales[Profit] / Sales[Sales Amount])

    // A standard IF would work fine, as it would not attempt the division for the "Ink" row.
    Safe Margin = IF(Sales[Sales Amount] > 0, Sales[Profit] / Sales[Sales Amount], 0)
    ```

### 6. IFERROR
*   **Definition:** Checks if the first expression evaluates to an error. If it does, it returns a specified alternative value. If it doesn't, it returns the result of the expression itself.
*   **Syntax:** `IFERROR(<value>, <value_if_error>)`
*   **Example:** Safely calculate profit margin without an error on division by zero or blank.
    ```dax
    Profit Margin = IFERROR(Sales[Profit] / Sales[Sales Amount], 0)
    ```
    **Result:** For the "Ink" row, this will return `0` instead of an error.

### 7. IN
*   **Definition:** Checks if a value exists within a provided list of values. It's a clean and efficient substitute for multiple `OR` conditions.
*   **Syntax:** `<expression> IN {<value1>, <value2>, ...}`
*   **Example:** Identify if a product is an "Apparel" or "Stationery" item.
    ```dax
    Is Soft Good or Stationery = Sales[Category] IN {"Apparel", "Stationery"}
    ```
    **Result:** This would be TRUE for Book, Pen, T-Shirt, and Ink. This is much cleaner than writing `Sales[Category] = "Apparel" || Sales[Category] = "Stationery"`.

### 8. NOT
*   **Definition:** Reverses the logical value of its argument. `NOT(TRUE)` becomes `FALSE`, and `NOT(FALSE)` becomes `TRUE`. The `!` operator is an equivalent.
*   **Syntax:** `NOT(<logical>)` or `![Condition]`
*   **Example:** Find items that are not on sale.
    ```dax
    Is Not On Sale = NOT(Sales[On Sale])
    ```
    **Result:** This returns TRUE for the Pen, Monitor, and Ink rows.

### 9. OR
*   **Definition:** Checks whether one of the arguments is TRUE. Returns TRUE if at least one argument is TRUE. The `||` operator is the common equivalent.
*   **Syntax:** `OR(<logical1>, <logical2>)` or `[Condition1] || [Condition2]`
*   **Example:** Identify items that are either in the "Apparel" category or have negative profit.
    ```dax
    Flag for Review = OR(Sales[Category] = "Apparel", Sales[Profit] < 0)
    
    // Using the operator
    Flag for Review = (Sales[Category] = "Apparel") || (Sales[Profit] < 0)
    ```
    **Result:** The "T-Shirt" row would be TRUE.

### 10. SWITCH
*   **Definition:** A powerful function that elegantly replaces multiple nested `IF` statements. It evaluates an expression against a list of value/result pairs and returns the corresponding result.
*   **Syntax:** `SWITCH(<expression>, <value1>, <result1>, [<value2>, <result2>]…, <else>)`
*   **Example:** Assign a priority level based on the product category.
    ```dax
    Priority = SWITCH(
        Sales[Category],
        "Electronics", "High",
        "Stationery", "Medium",
        "Apparel", "Low",
        "Other"  // This is the optional "else" result
    )
    ```
    A very common pattern is `SWITCH(TRUE(), ...)` which allows you to test a series of logical conditions.
    ```dax
    Sales Group = SWITCH(
        TRUE(),
        Sales[Sales Amount] > 1000, "Tier 1",
        Sales[Sales Amount] > 100, "Tier 2",
        "Tier 3"
    )
    ```

### 11. TRUE
*   **Definition:** Simply returns the logical value `TRUE`.
*   **Syntax:** `TRUE()`
*   **Example:** Most commonly used to improve the readability of `SWITCH` statements, as shown in the example above (`SWITCH(TRUE(), ...)`). It provides a clear anchor for evaluating a sequence of logical tests.


# 6. Text Functions


**Sample Table: `Customers`**

| CustomerID | FirstName | LastName | City | ZipCode (Text) |
| :--- | :--- | :--- | :--- | :--- |
| 1 | ` John` | Smith | New York | 10001 |
| 2 | Jane | Doe | Los Angeles| 90001 |
| 3 | Peter | Jones | NEW YORK | 10001 |

---

### 1. CONCATENATE
*   **Definition:** Joins two text strings into one. For joining more than two strings, the `&` operator is preferred.
*   **Syntax:** `CONCATENATE(<text1>, <text2>)`
*   **Example:** Create a full name.
    ```dax
    Full Name = CONCATENATE(Customers[FirstName], Customers[LastName]) 
    // Preferred Method using the & operator for better readability:
    // Full Name = Customers[FirstName] & " " & Customers[LastName]
    ```
    **Result for Row 1:** ` JohnSmith` (Note the lack of a space). Using the `&` operator makes adding separators easier.

### 2. CONCATENATEX
*   **Definition:** An iterator that concatenates the result of an expression evaluated for each row in a table. You can specify a delimiter.
*   **Syntax:** `CONCATENATEX(<table>, <expression>, [<delimiter>])`
*   **Example:** Create a measure that lists all customers in a selected city.
    ```dax
    // This is a MEASURE, not a column
    Customer List = CONCATENATEX(Customers, Customers[FirstName], ", ")
    ```
    **Result:** ` John, Jane, Peter`

### 3. COMBINEVALUES
*   **Definition:** Joins two or more text strings into one, using a specified delimiter. Its primary purpose is to support multi-column relationships in DirectQuery models.
*   **Syntax:** `COMBINEVALUES(<delimiter>, <expression1>, <expression2>…)`
*   **Example:** Create a composite key for a relationship.
    ```dax
    CompositeKey = COMBINEVALUES("-", Customers[CustomerID], Customers[ZipCode])
    ```
    **Result for Row 1:** `1-10001`

### 4. EXACT
*   **Definition:** Compares two text strings and returns TRUE if they are exactly the same (including case); otherwise, returns FALSE.
*   **Syntax:** `EXACT(<text1>, <text2>)`
*   **Example:** Check if the city is "New York" with exact casing.
    ```dax
    Is_Exact_NY = EXACT(Customers[City], "New York")
    ```
    **Result:** TRUE for Row 1, FALSE for Row 3 (because of the case difference).

### 5. FIND
*   **Definition:** Locates one text string within another and returns the starting position of the string. It is **case-sensitive**.
*   **Syntax:** `FIND(<find_text>, <within_text>, [<start_num>], [<if_not_found_value>])`
*   **Example:** Find the position of the letter 'o' in `FirstName`.
    ```dax
    Find_o = FIND("o", Customers[FirstName], 1, 0)
    ```
    **Result for Row 1:** `3` (since 'J' is 2, after the leading space). It would return `0` (the not-found value) for Jane and Peter.

### 6. FIXED
*   **Definition:** Rounds a number to a specified number of decimals and returns the result as text.
*   **Syntax:** `FIXED(<number>, [<decimals>], [<no_commas>])`
*   **Example:** Format a number `1234.567` as text.
    ```dax
    Formatted Number = FIXED(1234.567, 1, FALSE)
    ```
    **Result:** `"1,234.6"` (The number is rounded and returned as a text string with a comma).

### 7. FORMAT
*   **Definition:** Converts a value (number, date, etc.) to text according to a specified format string. Extremely versatile.
*   **Syntax:** `FORMAT(<value>, <format_string>)`
*   **Example:** Format a date and a number.
    ```dax
    // Assume today is October 20, 2023
    Formatted Date = FORMAT(TODAY(), "dd-mmm-yyyy") 
    Formatted Currency = FORMAT(1500.5, "$#,##0.00")
    ```
    **Result:** `"20-Oct-2023"` and `"$1,500.50"`.

### 8. LEFT
*   **Definition:** Returns the specified number of characters from the start (left side) of a text string.
*   **Syntax:** `LEFT(<text>, [<num_chars>])`
*   **Example:** Get the first three letters of the `LastName`.
    ```dax
    LastName_3_Letters = LEFT(Customers[LastName], 3)
    ```
    **Result for Row 1:** `"Smi"`

### 9. LEN
*   **Definition:** Returns the number of characters in a text string.
*   **Syntax:** `LEN(<text>)`
*   **Example:** Find the length of the `FirstName`.
    ```dax
    FirstName_Length = LEN(Customers[FirstName])
    ```
    **Result for Row 1:** `5` (The leading space is included in the count).

### 10. LOWER
*   **Definition:** Converts all letters in a text string to lowercase.
*   **Syntax:** `LOWER(<text>)`
*   **Example:** Standardize the `City` column to lowercase.
    ```dax
    City_Lower = LOWER(Customers[City])
    ```
    **Result for Row 3:** `"new york"`

### 11. MID
*   **Definition:** Returns a string of characters from the middle of a text string, given a starting position and length.
*   **Syntax:** `MID(<text>, <start_num>, <num_chars>)`
*   **Example:** Extract the middle two characters from `LastName` starting at position 2.
    ```dax
    LastName_Middle = MID(Customers[LastName], 2, 2)
    ```
    **Result for Row 1 ("Smith"):** `"mi"`

### 12. REPLACE
*   **Definition:** Replaces part of a text string with a different text string, based on a start position and number of characters.
*   **Syntax:** `REPLACE(<old_text>, <start_num>, <num_chars>, <new_text>)`
*   **Example:** Anonymize the last two digits of the zip code.
    ```dax
    Anon_Zip = REPLACE(Customers[ZipCode], 4, 2, "XX")
    ```
    **Result for Row 1:** `"100XX"`

### 13. REPT
*   **Definition:** Repeats text a given number of times. Useful for creating simple in-cell visualizations.
*   **Syntax:** `REPT(<text>, <num_times>)`
*   **Example:** Create a 5-star rating.
    ```dax
    Rating = REPT("★", 5)
    ```
    **Result:** `"★★★★★"`

### 14. RIGHT
*   **Definition:** Returns the specified number of characters from the end (right side) of a text string.
*   **Syntax:** `RIGHT(<text>, [<num_chars>])`
*   **Example:** Get the last 2 digits of the `ZipCode`.
    ```dax
    Zip_Last_2 = RIGHT(Customers[ZipCode], 2)
    ```
    **Result for Row 1:** `"01"`

### 15. SEARCH
*   **Definition:** Locates one text string within another and returns its starting position. It is **not case-sensitive**.
*   **Syntax:** `SEARCH(<find_text>, <within_text>, [<start_num>], [<if_not_found_value>])`
*   **Example:** Find the position of 'n', regardless of case.
    ```dax
    Search_n = SEARCH("n", Customers[City], 1, 0)
    ```
    **Result for Row 3 ("NEW YORK"):** `1` (It finds the 'N' even though we searched for 'n').

### 16. SUBSTITUTE
*   **Definition:** Replaces existing text with new text in a string. Unlike `REPLACE`, it searches for specific text to replace, not a position.
*   **Syntax:** `SUBSTITUTE(<text>, <old_text>, <new_text>, [<instance_num>])`
*   **Example:** Replace all spaces with a hyphen.
    ```dax
    City_With_Hyphen = SUBSTITUTE(Customers[City], " ", "-")
    ```
    **Result for Row 2:** `"Los-Angeles"`

### 17. TRIM
*   **Definition:** Removes all leading and trailing spaces from a text string and reduces multiple spaces between words to a single space.
*   **Syntax:** `TRIM(<text>)`
*   **Example:** Clean the `FirstName` column.
    ```dax
    FirstName_Clean = TRIM(Customers[FirstName])
    ```
    **Result for Row 1:** `"John"` (The leading space is gone).

### 18. UNICHAR
*   **Definition:** Returns the Unicode character that corresponds to a given number.
*   **Syntax:** `UNICHAR(<number>)`
*   **Example:** Create a string with a line break.
    ```dax
    Address_Line_Break = Customers[City] & UNICHAR(10) & Customers[ZipCode]
    ```
    **Result for Row 1:** A text value showing "New York" on the first line and "10001" on the second (in visuals that support it). `UNICHAR(10)` is the line feed character.

### 19. UNICODE
*   **Definition:** Returns the numeric Unicode code for the first character of a text string.
*   **Syntax:** `UNICODE(<text>)`
*   **Example:** Get the Unicode for the letter 'J'.
    ```dax
    Unicode_J = UNICODE("John")
    ```
    **Result:** `74`

### 20. UPPER
*   **Definition:** Converts all letters in a text string to uppercase.
*   **Syntax:** `UPPER(<text>)`
*   **Example:** Standardize the `LastName` to uppercase.
    ```dax
    LastName_Upper = UPPER(Customers[LastName])
    ```
    **Result for Row 1:** `"SMITH"`

### 21. VALUE
*   **Definition:** Converts a text string that represents a number into an actual numeric data type.
*   **Syntax:** `VALUE(<text>)`
*   **Example:** Convert the `ZipCode` text column to a number so you can perform mathematical operations on it.
    ```dax
    ZipCode_as_Number = VALUE(Customers[ZipCode])
    ```
    **Result:** The column will now be of a numeric type instead of text.

# 7. Date and Time Functions

### **Table-Generating Functions**

#### 1. CALENDAR
*   **Definition:** Returns a table with a single column named "Date" that contains a contiguous set of dates.
*   **Syntax:** `CALENDAR(<start_date>, <end_date>)`
*   **Example:** Create a date table for the year 2023.
    ```dax
    // This creates a new calculated table
    DateTable = CALENDAR(DATE(2023, 1, 1), DATE(2023, 12, 31))
    ```
    **Result:** A table with one column containing all dates from January 1, 2023, to December 31, 2023.

#### 2. CALENDARAUTO
*   **Definition:** Returns a table with a single column named "Date" containing a contiguous set of dates. The date range is automatically determined from the date columns in your entire data model.
*   **Syntax:** `CALENDARAUTO([fiscal_year_end_month])`
*   **Example:** Automatically create a complete date table for your model.
    ```dax
    // This creates a new calculated table
    AutoDateTable = CALENDARAUTO()
    ```
    **Result:** A table with one column of dates spanning from the earliest year to the latest year found anywhere in your model.

---

### **Date and Time Construction & Calculation**

#### 3. DATE
*   **Definition:** Creates a valid date from integer inputs for year, month, and day.
*   **Syntax:** `DATE(<year>, <month>, <day>)`
*   **Example:** Create the date for Christmas 2024.
    ```dax
    Christmas 2024 = DATE(2024, 12, 25)
    ```
    **Result:** `12/25/2024` (as a datetime value).

#### 4. DATEDIFF
*   **Definition:** Calculates the number of intervals (e.g., days, months, years) between two dates.
*   **Syntax:** `DATEDIFF(<start_date>, <end_date>, <interval>)` where interval can be `SECOND`, `MINUTE`, `HOUR`, `DAY`, `WEEK`, `MONTH`, `QUARTER`, `YEAR`.
*   **Example:** Find the number of days a project was active.
    ```dax
    Project Duration Days = DATEDIFF("2023-03-20", "2023-04-05", DAY)
    ```
    **Result:** `16`

#### 5. DAY
*   **Definition:** Returns the day of the month as a number from 1 to 31.
*   **Syntax:** `DAY(<date>)`
*   **Example:** Get the day from the date `October 26, 2023`.
    ```dax
    Day Number = DAY("2023-10-26")
    ```
    **Result:** `26`

#### 6. EDATE
*   **Definition:** Returns the date that is the indicated number of months before or after the start date.
*   **Syntax:** `EDATE(<start_date>, <months>)`
*   **Example:** Find the date 6 months after `January 15, 2023`.
    ```dax
    Six Months Later = EDATE("2023-01-15", 6)
    ```
    **Result:** `7/15/2023`

#### 7. EOMONTH
*   **Definition:** Returns the date of the last day of the month, a specified number of months before or after a start date.
*   **Syntax:** `EOMONTH(<start_date>, <months>)`
*   **Example:** Find the last day of the month, two months from now.
    ```dax
    // Assuming today is October 26, 2023
    EOM Two Months From Now = EOMONTH(TODAY(), 2)
    ```
    **Result:** `12/31/2023`

#### 8. HOUR
*   **Definition:** Returns the hour as a number from 0 (12:00 A.M.) to 23 (11:00 P.M.).
*   **Syntax:** `HOUR(<datetime>)`
*   **Example:** Get the hour from `14:30:15`.
    ```dax
    Hour of Day = HOUR("2023-10-26 14:30:15")
    ```
    **Result:** `14`

#### 9. MINUTE
*   **Definition:** Returns the minute as a number from 0 to 59.
*   **Syntax:** `MINUTE(<datetime>)`
*   **Example:** Get the minute from `14:30:15`.
    ```dax
    Minute of Hour = MINUTE("2023-10-26 14:30:15")
    ```
    **Result:** `30`

#### 10. MONTH
*   **Definition:** Returns the month as a number from 1 (January) to 12 (December).
*   **Syntax:** `MONTH(<date>)`
*   **Example:** Get the month from `October 26, 2023`.
    ```dax
    Month Number = MONTH("2023-10-26")
    ```
    **Result:** `10`

#### 11. NOW
*   **Definition:** Returns the current date and time in the `datetime` format. This is a "volatile" function that updates whenever the report is refreshed or a calculation is triggered.
*   **Syntax:** `NOW()`
*   **Example:**
    ```dax
    Current DateTime = NOW()
    ```
    **Result:** `10/26/2023 2:45:10 PM` (or whatever the current date and time is).

#### 12. SECOND
*   **Definition:** Returns the second as a number from 0 to 59.
*   **Syntax:** `SECOND(<datetime>)`
*   **Example:** Get the second from `14:30:15`.
    ```dax
    Second of Minute = SECOND("2023-10-26 14:30:15")
    ```
    **Result:** `15`

#### 13. TIME
*   **Definition:** Creates a time value from integer inputs for hour, minute, and second.
*   **Syntax:** `TIME(<hour>, <minute>, <second>)`
*   **Example:** Create a time for 2:30 PM.
    ```dax
    Time Value = TIME(14, 30, 0)
    ```
    **Result:** `2:30:00 PM` (as a datetime value where the date part is 0).

#### 14. TIMEVALUE
*   **Definition:** Converts a time in a text format to a `datetime` format.
*   **Syntax:** `TIMEVALUE(<time_text>)`
*   **Example:** Convert the text "8:15 AM" to a time value.
    ```dax
    My Time = TIMEVALUE("8:15 AM")
    ```
    **Result:** `8:15:00 AM`

#### 15. TODAY
*   **Definition:** Returns the current date. The time portion is always 12:00:00 AM. This is also a volatile function.
*   **Syntax:** `TODAY()`
*   **Example:**
    ```dax
    Current Date = TODAY()
    ```
    **Result:** `10/26/2023 12:00:00 AM`

#### 16. UTCNOW
*   **Definition:** Returns the current Coordinated Universal Time (UTC) date and time.
*   **Syntax:** `UTCNOW()`
*   **Example:**
    ```dax
    Current UTC DateTime = UTCNOW()
    ```
    **Result:** The current date and time at the UTC (GMT) time zone.

#### 17. UTCTODAY
*   **Definition:** Returns the current Coordinated Universal Time (UTC) date.
*   **Syntax:** `UTCTODAY()`
*   **Example:**
    ```dax
    Current UTC Date = UTCTODAY()
    ```
    **Result:** The current date at the UTC (GMT) time zone.

#### 18. WEEKDAY
*   **Definition:** Returns a number from 1 to 7 identifying the day of the week.
*   **Syntax:** `WEEKDAY(<date>, [<return_type>])`
    *   `return_type = 1` (Default): Sunday=1 through Saturday=7
    *   `return_type = 2`: Monday=1 through Sunday=7
    *   `return_type = 3`: Monday=0 through Sunday=6
*   **Example:** Find the day of the week for `October 26, 2023` (a Thursday), with Monday as the start of the week.
    ```dax
    Day of Week = WEEKDAY("2023-10-26", 2)
    ```
    **Result:** `4`

#### 19. WEEKNUM
*   **Definition:** Returns the week number in the year (1-54).
*   **Syntax:** `WEEKNUM(<date>, [<return_type>])`
    *   `return_type = 1` (Default): Week begins on Sunday.
    *   `return_type = 2`: Week begins on Monday.
*   **Example:** Find the week number for `January 15, 2023`.
    ```dax
    Week Number = WEEKNUM("2023-01-15")
    ```
    **Result:** `3` (Because Jan 1st was a Sunday, Jan 15th falls in the 3rd week).

#### 20. YEAR
*   **Definition:** Returns the year of a date as a four-digit integer.
*   **Syntax:** `YEAR(<date>)`
*   **Example:** Get the year from `October 26, 2023`.
    ```dax
    Year Number = YEAR("2023-10-26")
    ```
    **Result:** `2023`

#### 21. YEARFRAC
*   **Definition:** Calculates the fraction of a year represented by the number of whole days between two dates.
*   **Syntax:** `YEARFRAC(<start_date>, <end_date>, [<basis>])`
*   **Example:** Find the fraction of the year between two dates.
    ```dax
    Year Fraction = YEARFRAC("2023-01-01", "2023-07-02")
    ```
    **Result:** `0.5` (Represents half a year).

# 8. Information Functions

**Sample Table: `Sales`**

![[Assets/7e29407b673b63efd94c67745dc636bd_MD5.jpeg]]


### **Table & Row Information**

#### 1. CONTAINS
*   **Definition:** Returns TRUE if a specified set of values exists in the specified columns of a table. It checks for the existence of at least one entire row that matches all criteria.
*   **Syntax:** `CONTAINS(<table>, <columnName1>, <value1>, [<columnName2>, <value2>]…)`
*   **Example:** Check if there was ever a sale of a "Pen" with a quantity of 5.
    ```dax
    WasPenSoldWithQty5 = CONTAINS(Sales, Sales[Product], "Pen", Sales[Quantity], 5)
    ```
    **Result:** TRUE, because the second row matches both conditions.

#### 2. CONTAINSROW
*   **Definition:** Returns TRUE if a specified row of values exists within a table. It's similar to `CONTAINS` but uses a row constructor.
*   **Syntax:** `CONTAINSROW(<table>, <row_constructor>)`
*   **Example:** Check if a specific row exists in the Sales table.
    ```dax
    CheckForRow = CONTAINSROW(Sales, ROW("Product", "Laptop", "Quantity", 1))
    ```
    **Result:** TRUE.

### **Filter Context & Selection Information**

#### 3. CUSTOMDATA
*   **Definition:** Retrieves the content of the `CustomData` connection string property. This is an advanced function used primarily for passing parameters into a model, often for Row-Level Security (RLS) in Power BI Embedded or Azure Analysis Services.
*   **Syntax:** `CUSTOMDATA()`
*   **Example:** In an RLS rule, you could filter data based on a region ID passed through the connection string.
    ```dax
    // RLS Rule on a 'Regions' table
    [RegionID] = CUSTOMDATA() 
    ```
    If the application connecting to the model sets the `CustomData` property to "101", the user would only see data for RegionID 101.

#### 4. HASONEFILTER
*   **Definition:** Returns TRUE when the number of directly filtered values on a column is exactly one.
*   **Syntax:** `HASONEFILTER(<columnName>)`
*   **Example:** If you have a slicer for `Sales[Product]` and the user selects *only* "Book", this function returns TRUE. If they select "Book" and "Pen", it returns FALSE.

#### 5. HASONEVALUE
*   **Definition:** Returns TRUE when the context for a column has been filtered down to one single distinct value. This is more common and powerful than `HASONEFILTER` as it also considers indirect (cross-filtering).
*   **Syntax:** `HASONEVALUE(<columnName>)`
*   **Example:** Create a dynamic title for a visual.
    ```dax
    Dynamic Title = IF(HASONEVALUE(Sales[Product]), "Report for " & SELECTEDVALUE(Sales[Product]), "Overall Report")
    ```

#### 6. ISCROSSFILTERED
*   **Definition:** Returns TRUE when a column is being filtered, either directly or indirectly by a filter on another table.
*   **Syntax:** `ISCROSSFILTERED(<columnName>)`
*   **Example:** If you have a `Customers` table related to `Sales` and you filter by a customer, `ISCROSSFILTERED(Sales[Product])` would return TRUE because the filter on `Customers` is affecting `Sales`.

#### 7. ISFILTERED
*   **Definition:** Returns TRUE when a column is being filtered directly.
*   **Syntax:** `ISFILTERED(<columnName>)`
*   **Example:** Used to change behavior when a slicer is active.
    ```dax
    Sales Info = IF(ISFILTERED(Sales[Product]), "Showing specific product sales", "Showing all product sales")
    ```

#### 8. ISINSCOPE
*   **Definition:** Returns TRUE when the specified column is in the current level of a hierarchy in a visual (like a matrix). It's essential for controlling calculations at different levels of granularity (totals, subtotals, etc.).
*   **Syntax:** `ISINSCOPE(<columnName>)`
*   **Example:** Show a value only at the Product level, not in the grand total of a matrix.
    ```dax
    Product Level Only = IF(ISINSCOPE(Sales[Product]), SUM(Sales[Sales Amount]), BLANK())
    ```

#### 9. ISSELECTED
*   **Definition:** This function is a synonym for `ISFILTERED`. It's provided for compatibility with older models.
*   **Syntax:** `ISSELECTED(<columnName>)`

### **Value Type & State Information (The "IS" family)**

#### 10. ISBLANK
*   **Definition:** Checks whether a value is blank and returns TRUE or FALSE.
*   **Syntax:** `ISBLANK(<value>)`
*   **Example:** Check for missing sales amounts.
    ```dax
    Is Sales Amount Missing = ISBLANK(Sales[Sales Amount])
    ```
    **Result:** TRUE for the "Ink" row.

#### 11. ISEMPTY
*   **Definition:** Checks if a table is empty (contains no rows) and returns TRUE or FALSE.
*   **Syntax:** `ISEMPTY(<table>)`
*   **Example:** Check if any sales exist for a non-existent product.
    ```dax
    No Chair Sales = ISEMPTY(FILTER(Sales, Sales[Product] = "Chair"))
    ```
    **Result:** TRUE.

#### 12. ISERROR
*   **Definition:** Checks if a value is an error and returns TRUE or FALSE. Often used with `IFERROR`.
*   **Syntax:** `ISERROR(<value>)`
*   **Example:**
    ```dax
    Is Division Error = ISERROR(1/0)
    ```
    **Result:** TRUE.

#### 13. ISLOGICAL
*   **Definition:** Checks if a value is a logical value (TRUE or FALSE).
*   **Syntax:** `ISLOGICAL(<value>)`
*   **Example:**
    ```dax
    Is Value Logical = ISLOGICAL(Sales[IsReturned])
    ```
    **Result:** TRUE for all rows.

#### 14. ISNONTEXT
*   **Definition:** Checks if a value is not text (i.e., it's a number, date, or blank).
*   **Syntax:** `ISNONTEXT(<value>)`
*   **Example:**
    ```dax
    Is Not Text = ISNONTEXT(Sales[Sales Amount])
    ```
    **Result:** TRUE for all rows.

#### 15. ISNUMBER
*   **Definition:** Checks if a value is a number.
*   **Syntax:** `ISNUMBER(<value>)`
*   **Example:**
    ```dax
    Is Value Numeric = ISNUMBER(Sales[Sales Amount])
    ```
    **Result:** TRUE for Book, Pen, and Laptop. FALSE for Ink (because it's blank).

#### 16. ISODD / 17. ISEVEN
*   **Definition:** Checks if a number is odd or even.
*   **Syntax:** `ISODD(<number>)`, `ISEVEN(<number>)`
*   **Example:** Check if the quantity is an even number.
    ```dax
    Is Quantity Even = ISEVEN(Sales[Quantity])
    ```
    **Result:** TRUE for Book and Ink. FALSE for Pen and Laptop.

#### 18. ISTEXT
*   **Definition:** Checks if a value is text.
*   **Syntax:** `ISTEXT(<value>)`
*   **Example:**
    ```dax
    Is Product Text = ISTEXT(Sales[Product])
    ```
    **Result:** TRUE for all rows.

### **User Information (For RLS)**
These functions are used in the Power BI Service to get information about the current user, primarily for implementing Row-Level Security.

#### 19. USERNAME
*   **Definition:** Returns the domain name and username from the credentials given to the system at connection time. It's now recommended to use `USERPRINCIPALNAME` instead.
*   **Syntax:** `USERNAME()`

#### 20. USEROBJECTID
*   **Definition:** Returns the unique Object ID for the current user in Azure Active Directory (AAD). This is the most robust way to implement RLS because it's unique and won't change even if a user's email (UPN) changes.
*   **Syntax:** `USEROBJECTID()`
*   **Example (RLS Rule):**
    ```dax
    // On an Employee table with an AAD ID column
    [Employee_AAD_ID] = USEROBJECTID()
    ```

#### 21. USERPRINCIPALNAME
*   **Definition:** Returns the User Principal Name (UPN), which is typically the login email address of the current user. This is the most common function for user-based RLS.
*   **Syntax:** `USERPRINCIPALNAME()`
*   **Example (RLS Rule):**
    ```dax
    // On a Salesperson table with an email column
    [EmailAddress] = USERPRINCIPALNAME()
    ```


# 9. Parent-Child Functions

Of course. This set of functions belongs to the **Parent-Child** or **Hierarchy** functions in DAX. They are specifically designed to work with data structured as a self-referencing hierarchy, such as an employee/manager chart, a chart of accounts, or multi-level product categories within a single table.

### The Core Concept: Parent-Child Hierarchies

These functions operate on tables where a relationship exists within the table itself. For example, a table of employees where each employee row has both an `EmployeeID` and a `ManagerID` (which is just another `EmployeeID`).

To make the examples clear, we will use the following `Employees` table for all functions.

**Sample Table: `Employees`**

![[Assets/8309283674de6df8715c55bb5c12f853_MD5.jpeg]]


### 1. PATH
*   **Definition:** This is the foundational parent-child function. It evaluates a recursive relationship and returns a delimited text string showing the full path of identifiers from the top-level parent down to the current row's identifier.
*   **Syntax:** `PATH(<ID_column>, <parent_ID_column>)`
*   **Example:** We will create a new calculated column in the `Employees` table to store the organizational path for each employee.
    ```dax
    // New Calculated Column
    EmployeePath = PATH(Employees[EmployeeID], Employees[ManagerID])
    ```
    **Resulting `Employees` Table:**
| EmployeeID | EmployeeName | ManagerID | **EmployeePath** |
| :--- | :--- | :--- | :--- |
| 1 | Alice (CEO) | | `1` |
| 2 | Bob | 1 | `1|2` |
| 3 | David | 1 | `1|3` |
| 4 | Carol | 2 | `1|2|4` |
| 5 | Eve | 3 | `1|3|5` |
| 6 | Frank | 5 | `1|3|5|6` |

---

### 2. PATHCONTAINS
*   **Definition:** Returns `TRUE` if a specified item (identifier) exists within a given path string. This is useful for checking if one employee is in the management chain of another.
*   **Syntax:** `PATHCONTAINS(<path>, <item>)`
*   **Example:** Create a calculated column to check if an employee reports up to David (EmployeeID = 3) at any level.
    ```dax
    // New Calculated Column
    Reports To David = PATHCONTAINS(Employees[EmployeePath], 3)
    ```
    **Resulting `Employees` Table:**
| EmployeeID | EmployeeName | **EmployeePath** | **Reports To David** |
| :--- | :--- | :--- | :--- |
| 1 | Alice (CEO) | `1` | FALSE |
| 2 | Bob | `1|2` | FALSE |
| 3 | David | `1|3` | TRUE (contains itself) |
| 4 | Carol | `1|2|4` | FALSE |
| 5 | Eve | `1|3|5` | TRUE |
| 6 | Frank | `1|3|5|6` | TRUE |

---

### 3. PATHITEM
*   **Definition:** Extracts a specific identifier from a path string based on its position, counting from left to right (from the top of the hierarchy).
*   **Syntax:** `PATHITEM(<path>, <position>, [<type>])`
    *   `position`: The level you want to retrieve (1 is the top-level parent).
    *   `type`: Optional. `0` (default) for Text, `1` for Integer.
*   **Example:** Create a calculated column to identify the "Level 2" manager in each employee's hierarchy.
    ```dax
    // New Calculated Column
    Level 2 Manager = PATHITEM(Employees[EmployeePath], 2, 1) // 1 means return as Integer
    ```
    **Resulting `Employees` Table:**
| EmployeeID | **EmployeePath** | **Level 2 Manager** |
| :--- | :--- | :--- |
| 1 | `1` | BLANK() (no level 2) |
| 2 | `1|2` | 2 |
| 3 | `1|3` | 3 |
| 4 | `1|2|4` | 2 |
| 5 | `1|3|5` | 3 |
| 6 | `1|3|5|6`| 3 |

---

### 4. PATHITEMREVERSE
*   **Definition:** Extracts a specific identifier from a path string based on its position, but counts from right to left (from the bottom of the hierarchy).
*   **Syntax:** `PATHITEMREVERSE(<path>, <position>, [<type>])`
    *   `position`: The level you want to retrieve (1 is the current item itself).
*   **Example:** Create a calculated column to find the direct manager of each employee. The employee's own ID is at position 1 (from the right), so their direct manager is at position 2.
    ```dax
    // New Calculated Column
    Direct Manager ID = PATHITEMREVERSE(Employees[EmployeePath], 2, 1)
    ```
    **Resulting `Employees` Table:**
| EmployeeID | **EmployeePath** | **Direct Manager ID** | (Matches original `ManagerID`) |
| :--- | :--- | :--- | :--- |
| 1 | `1` | BLANK() (no level 2) | |
| 2 | `1|2` | 1 | 1 |
| 3 | `1|3` | 1 | 1 |
| 4 | `1|2|4` | 2 | 2 |
| 5 | `1|3|5` | 3 | 3 |
| 6 | `1|3|5|6`| 5 | 5 |

---

### 5. PATHLENGTH
*   **Definition:** Returns the number of levels (or items) in a given path string. This is useful for determining an employee's level in the hierarchy.
*   **Syntax:** `PATHLENGTH(<path>)`
*   **Example:** Create a calculated column to determine the hierarchy level of each employee.
    ```dax
    // New Calculated Column
    Hierarchy Level = PATHLENGTH(Employees[EmployeePath])
    ```
    **Resulting `Employees` Table:**
| EmployeeID | EmployeeName | **EmployeePath** | **Hierarchy Level** |
| :--- | :--- | :--- | :--- |
| 1 | Alice (CEO) | `1` | 1 |
| 2 | Bob | `1|2` | 2 |
| 3 | David | `1|3` | 2 |
| 4 | Carol | `1|2|4` | 3 |
| 5 | Eve | `1|3|5` | 3 |
| 6 | Frank | `1|3|5|6`| 4 |


# 10. Math Functions

### 1. ABS
*   **Definition:** Returns the absolute (non-negative) value of a number.
*   **Syntax:** `ABS(<number>)`
*   **Example:**
    ```dax
    Absolute Value = ABS(-42)
    ```
    **Result:** `42`

### 2. CEILING
*   **Definition:** Rounds a number *up*, away from zero, to the nearest multiple of a specified significance.
*   **Syntax:** `CEILING(<number>, <significance>)`
*   **Example:** Round a price up to the nearest quarter.
    ```dax
    Rounded Up Price = CEILING(1.57, 0.25)
    ```
    **Result:** `1.75`

### 3. DIVIDE
*   **Definition:** A safe division function that handles division-by-zero errors. If the denominator is zero or blank, it returns an optional alternate result (or BLANK if not provided).
*   **Syntax:** `DIVIDE(<numerator>, <denominator>, [<alternate_result>])`
*   **Example:** Safely calculate a ratio.
    ```dax
    Profit Margin = DIVIDE(SUM(Sales[Profit]), SUM(Sales[Sales Amount]), 0)
    ```
    **Result:** If the total `Sales Amount` is 0, the measure will return `0` instead of an error.

### 4. EVEN
*   **Definition:** Rounds a number *up* to the nearest even integer. Negative numbers are rounded down (away from zero).
*   **Syntax:** `EVEN(<number>)`
*   **Example:**
    ```dax
    Nearest Even = EVEN(3.1)  // -> 4
    Nearest Even Neg = EVEN(-3.1) // -> -4
    ```
    **Result:** `4` and `-4` respectively.

### 5. EXP
*   **Definition:** Returns Euler's number (e ≈ 2.71828) raised to the power of a given number. It is the inverse of the `LN` (natural logarithm) function.
*   **Syntax:** `EXP(<number>)`
*   **Example:**
    ```dax
    e to the power of 2 = EXP(2)
    ```
    **Result:** `7.389...`

### 6. FACT
*   **Definition:** Returns the factorial of a number (the product of all integers from 1 to that number).
*   **Syntax:** `FACT(<number>)`
*   **Example:**
    ```dax
    Factorial of 5 = FACT(5) // (1 * 2 * 3 * 4 * 5)
    ```
    **Result:** `120`

### 7. FLOOR
*   **Definition:** Rounds a number *down*, toward zero, to the nearest multiple of a specified significance.
*   **Syntax:** `FLOOR(<number>, <significance>)`
*   **Example:** Round a price down to the nearest dollar.
    ```dax
    Rounded Down Price = FLOOR(25.99, 1)
    ```
    **Result:** `25`

### 8. GCD
*   **Definition:** Returns the greatest common divisor of two or more integers.
*   **Syntax:** `GCD(<number1>, <number2>)`
*   **Example:**
    ```dax
    GCD of 54 and 24 = GCD(54, 24)
    ```
    **Result:** `6`

### 9. INT
*   **Definition:** Rounds a number *down* to the nearest integer. It effectively truncates the decimal part.
*   **Syntax:** `INT(<number>)`
*   **Example:**
    ```dax
    Integer Part = INT(8.9)
    ```
    **Result:** `8`

### 10. MROUND
*   **Definition:** Rounds a number to the nearest desired multiple.
*   **Syntax:** `MROUND(<number>, <multiple>)`
*   **Example:** Round a number to the nearest multiple of 5.
    ```dax
    Rounded to 5 = MROUND(13, 5)
    ```
    **Result:** `15` (because 13 is closer to 15 than to 10).

### 11. ODD
*   **Definition:** Rounds a number *up* to the nearest odd integer. Negative numbers are rounded down (away from zero).
*   **Syntax:** `ODD(<number>)`
*   **Example:**
    ```dax
    Nearest Odd = ODD(2.1) // -> 3
    Nearest Odd Neg = ODD(-2.1) // -> -3
    ```
    **Result:** `3` and `-3` respectively.

### 12. POWER
*   **Definition:** Returns the result of a number raised to a given power.
*   **Syntax:** `POWER(<number>, <power>)`
*   **Example:**
    ```dax
    3 to the power of 4 = POWER(3, 4)
    ```
    **Result:** `81`

### 13. QUOTIENT
*   **Definition:** Performs a division and returns only the integer portion of the result, discarding the remainder.
*   **Syntax:** `QUOTIENT(<numerator>, <denominator>)`
*   **Example:**
    ```dax
    Integer Division = QUOTIENT(10, 3)
    ```
    **Result:** `3`

### 14. RAND
*   **Definition:** Returns a random decimal number greater than or equal to 0 and less than 1. This is a "volatile" function that returns a new value every time a calculation is performed.
*   **Syntax:** `RAND()`
*   **Example:**
    ```dax
    Random Decimal = RAND()
    ```
    **Result:** A value like `0.824...`

### 15. RANDBETWEEN
*   **Definition:** Returns a random integer between two numbers you specify (inclusive). This is also a volatile function.
*   **Syntax:** `RANDBETWEEN(<bottom>, <top>)`
*   **Example:**
    ```dax
    Random Dice Roll = RANDBETWEEN(1, 6)
    ```
    **Result:** An integer like `1`, `2`, `3`, `4`, `5`, or `6`.

### 16. ROUND
*   **Definition:** Rounds a number to a specified number of decimal places, following standard rounding rules (≥ 5 rounds up, < 5 rounds down).
*   **Syntax:** `ROUND(<number>, <num_digits>)`
*   **Example:**
    ```dax
    Rounded to 2 decimals = ROUND(3.14159, 2)
    ```
    **Result:** `3.14`

### 17. ROUNDDOWN
*   **Definition:** Always rounds a number *down* (toward zero) to a specified number of decimal places.
*   **Syntax:** `ROUNDDOWN(<number>, <num_digits>)`
*   **Example:**
    ```dax
    Rounded Down = ROUNDDOWN(1.99, 1)
    ```
    **Result:** `1.9`

### 18. ROUNDUP
*   **Definition:** Always rounds a number *up* (away from zero) to a specified number of decimal places.
*   **Syntax:** `ROUNDUP(<number>, <num_digits>)`
*   **Example:**
    ```dax
    Rounded Up = ROUNDUP(1.91, 1)
    ```
    **Result:** `2.0`

### 19. SQRT
*   **Definition:** Returns the square root of a number.
*   **Syntax:** `SQRT(<number>)`
*   **Example:**
    ```dax
    Square Root of 81 = SQRT(81)
    ```
    **Result:** `9`

# 11. Table Manipulation Functions

Of course. This is a very important set of DAX functions known as **Table Functions**. These functions are the core of DAX because they allow you to create, combine, and manipulate entire tables within your formulas. The virtual tables they produce are then used by other functions (like iterators `SUMX` or `FILTER`) to perform powerful calculations.

For these examples, we will use the following simple data model:

**Table: `Sales`**

![[Assets/cb05b260558400880cd7e2da17551eb2_MD5.jpeg]]

**Table: `Products`**

![[Assets/f1ae235a69d5dfba84507b69bf5ffcc2_MD5.jpeg]]


### **Table Manipulation and Creation**

#### 1. ADDCOLUMNS
*   **Definition:** Adds one or more calculated columns to a given table.
*   **Syntax:** `ADDCOLUMNS(<table>, <name>, <expression>, [<name2>, <expression2>]…)`
*   **Example:** Create a new virtual table from `Sales` with an added `Sales Tax` column.
    ```dax
    Sales with Tax = ADDCOLUMNS(Sales, "Sales Tax", [Sales Amount] * 0.08)
    ```
    **Result:** A four-column table from `Sales` plus a new fifth column named `Sales Tax`.

#### 2. ADDMISSINGITEMS
*   **Definition:** Adds rows with blank values to a table for items that have data in one column but not another. This ensures visuals don't hide items that had no sales in a period, for example.
*   **Syntax:** `ADDMISSINGITEMS([<showAll_columnName>], <table>, [<groupBy_columnName>], ...)`
*   **Example:** In a matrix showing `Sales[Region]` and `Products[Product]`, if "Pen" had no sales in the "South" region, it might not appear. This function can force it to show up with a blank value.

#### 3. CROSSJOIN
*   **Definition:** Returns the Cartesian product of all rows from all specified tables, creating a table that contains every possible combination of rows.
*   **Syntax:** `CROSSJOIN(<table>, <table>, ...)`
*   **Example:** Create a table with every possible combination of `Region` and `Product`.
    ```dax
    All Combinations = CROSSJOIN(DISTINCT(Sales[Region]), DISTINCT(Sales[Product]))
    ```
    **Result:** A table with 6 rows (2 regions × 3 products).

#### 4. DATATABLE
*   **Definition:** Allows you to declare an inline table of data within a DAX formula.
*   **Syntax:** `DATATABLE(<colName1>, <dataType1>, <colName2>, <dataType2>, ..., {{<val1>, <val2>}, ...})`
*   **Example:** Create a small, two-column table for exchange rates.
    ```dax
    Exchange Rates = DATATABLE("Currency", STRING, "Rate", DOUBLE, {{"USD", 1.0}, {"EUR", 0.92}})
    ```

#### 5. DISTINCT (Table Function)
*   **Definition:** Returns a one-column table containing the unique values from a column, or a multi-column table containing unique combinations of values from a table.
*   **Syntax:** `DISTINCT(<table> or <column>)`
*   **Example:** Get a list of all regions that had sales.
    ```dax
    Regions with Sales = DISTINCT(Sales[Region])
    ```
    **Result:** A one-column table with two rows: "North" and "South".

#### 6. EXCEPT
*   **Definition:** A set operator that returns the rows of the first table that do not appear in the second table.
*   **Syntax:** `EXCEPT(<table1>, <table2>)`
*   **Example:** Find all products that are not in the 'Electronics' category.
    ```dax
    Non_Electronics = EXCEPT(DISTINCT(Products[Product]), FILTER(Products, Products[Category] = "Electronics"))
    ```
    **Result:** A table with "Book" and "Pen".

#### 7. FILTERS
*   **Definition:** Returns a table of the values that are currently being used to directly filter a specified column.
*   **Syntax:** `FILTERS(<columnName>)`
*   **Example:** Used in a measure to see which regions are selected in a slicer. `COUNTROWS(FILTERS(Sales[Region]))` would return the number of regions selected.

#### 8. GENERATE / 9. GENERATEALL
*   **Definition:** `GENERATE` returns a table by evaluating the second table expression for each row of the first table. `GENERATEALL` is similar but includes rows from the first table even if the second expression returns an empty table.
*   **Syntax:** `GENERATE(<table>, <table_expression>)`
*   **Example:**
    ```dax
    // This creates a table that joins product categories to sales regions
    CategoryRegions = GENERATE(DISTINCT(Products[Category]), DISTINCT(Sales[Region]))
    ```

#### 10. GENERATESERIES
*   **Definition:** Returns a single-column table containing a series of numbers in a given range with a specified step/increment.
*   **Syntax:** `GENERATESERIES(<startValue>, <endValue>, [<incrementValue>])`
*   **Example:** Create a table of even numbers from 2 to 10.
    ```dax
    Even Numbers = GENERATESERIES(2, 10, 2)
    ```
    **Result:** A table with rows: 2, 4, 6, 8, 10.

#### 11. GROUPBY
*   **Definition:** Groups rows from a table and allows for aggregations, similar to `SUMMARIZE`. It uses iterator functions (`CURRENTGROUP()`) for its aggregations.
*   **Syntax:** `GROUPBY(<table>, [<groupBy_columnName>], ..., <name>, <expression>)`
*   **Example:**
    ```dax
    Sales by Region = GROUPBY(Sales, Sales[Region], "Total Sales", SUMX(CURRENTGROUP(), [Sales Amount]))
    ```

#### 12. INTERSECT
*   **Definition:** A set operator that returns the rows that exist in both of the specified tables.
*   **Syntax:** `INTERSECT(<table1>, <table2>)`
*   **Example:** Find which products sold in *both* the North and South regions.
    ```dax
    Products in Both Regions = 
    INTERSECT(
        FILTER(Sales, Sales[Region] = "North")[Product],
        FILTER(Sales, Sales[Region] = "South")[Product]
    )
    ```
    **Result:** A table with one row: "Book".

#### 13. ISEMPTY
*   **Definition:** An information function that checks if a table expression results in an empty table (zero rows).
*   **Syntax:** `ISEMPTY(<table>)`
*   **Example:** Check if there were any sales over 2000.
    ```dax
    No Large Sales = ISEMPTY(FILTER(Sales, Sales[Sales Amount] > 2000))
    ```
    **Result:** TRUE.

#### 14. NATURALINNERJOIN / 15. NATURALLEFTOUTERJOIN
*   **Definition:** These functions perform traditional SQL-style joins between two tables based on common column names, without needing a pre-existing relationship.
*   **Syntax:** `NATURALINNERJOIN(<table>, <table>)`
*   **Example:**
    ```dax
    SalesWithCategory = NATURALINNERJOIN(Sales, Products)
    ```
    **Result:** A joined table. `NATURALINNERJOIN` would only include products present in both tables. `NATURALLEFTOUTERJOIN` would include all rows from the left table (`Sales`) and matching data from the right (`Products`).

#### 16. ROW
*   **Definition:** Creates a table with a single row.
*   **Syntax:** `ROW(<name>, <expression>, [<name2>, <expression2>]…)`
*   **Example:**
    ```dax
    SingleRowTable = ROW("Product", "Chair", "Sales", 250)
    ```

#### 17. SELECTCOLUMNS
*   **Definition:** Creates a new table by selecting columns from an existing table. You can also rename columns and create new calculated columns.
*   **Syntax:** `SELECTCOLUMNS(<table>, <name>, <expression>, ...)`
*   **Example:** Create a new table with just the product and sales amount.
    ```dax
    ProductSales = SELECTCOLUMNS(Sales, "Product Name", Sales[Product], "Revenue", Sales[Sales Amount])
    ```

#### 18. SUBSTITUTEWITHINDEX
*   **Definition:** A highly advanced function used for creating relationship keys. It returns a table with an added index column that can replace the original columns, which is useful when the combination of columns needs to be used in a relationship.

#### 19. SUMMARIZE / 20. SUMMARIZECOLUMNS
*   **Definition:** The primary functions for creating summary tables (grouping and aggregating data). `SUMMARIZECOLUMNS` is the modern, more efficient, and recommended function.
*   **Syntax (Modern):** `SUMMARIZECOLUMNS(<groupBy_columnName>, ..., [<filterTable>], ..., <name>, <expression>)`
*   **Example:** Create a summary table of sales by region and product category.
    ```dax
    Sales by Region & Category = 
    SUMMARIZECOLUMNS(
        Sales[Region],
        Products[Category],
        "Total Sales", SUM(Sales[Sales Amount])
    )
    ```

#### 21. TOPN
*   **Definition:** Returns the top N rows from a table based on the evaluation of an expression in descending (or ascending) order.
*   **Syntax:** `TOPN(<N_value>, <table>, [<orderBy_expression>], [<order>], ...)`
*   **Example:** Find the top 2 sales transactions.
    ```dax
    Top 2 Sales = TOPN(2, Sales, [Sales Amount], DESC)
    ```
    **Result:** A table containing the rows for the Laptop and the South region's Book sale.

#### 22. TREATAS
*   **Definition:** Applies the set of values from one table as filters to columns from an unrelated table. It effectively creates a "virtual relationship" for the duration of a calculation.
*   **Syntax:** `TREATAS(<table>, <column1>, <column2>, ...)`
*   **Example:** Calculate sales for a dynamically created list of products.
    ```dax
    // A virtual table of products we care about
    VAR ProductsToSum = {"Book", "Pen"}
    // Use TREATAS to apply this list as a filter to the Sales[Product] column
    RETURN CALCULATE(SUM(Sales[Sales Amount]), TREATAS(ProductsToSum, Sales[Product]))
    ```

#### 23. UNION
*   **Definition:** A set operator that combines the rows from two or more tables that have the same number of columns.
*   **Syntax:** `UNION(<table>, <table>, ...)`
*   **Example:**
    ```dax
    Table1 = ROW("City", "New York")
    Table2 = ROW("City", "London")
    CombinedCities = UNION(Table1, Table2)
    ```
    **Result:** A table with two rows: "New York" and "London".

#### 24. VALUES
*   **Definition:** Returns a one-column table containing the distinct values from a column. Crucially, if used on a column from a related table, it respects the relationship and will only show values relevant to the current filter context.
*   **Syntax:** `VALUES(<tableOrColumnName>)`
*   **Example:** If you filter your report for the "North" region, `VALUES(Sales[Product])` will return a table with only "Book" and "Pen". This makes it ideal for use in measures.

# 12. Relationship Functions



**Table: `Products`** (The "one" side)

![[Assets/d899af15f85b37eff1cd2ff1297be5ae_MD5.jpeg]]

**Table: `Sales`** (The "many" side)

![[Assets/8169e206934f6d9987e4e4da26f6560a_MD5.jpeg]]
**Table: `Date`**

![[Assets/a8e2be436b208ab7cdb4c9fc2b9d6699_MD5.jpeg]]

**Relationships:**
1.  `Products[ProductKey]` <--- `Sales[ProductKey]` (One-to-many, active, single-direction filter from `Products` to `Sales`)
2.  `Date[Date]` <--- `Sales[OrderDate]` (One-to-many, **active**)
3.  `Date[Date]` <--- `Sales[ShipDate]` (One-to-many, **inactive**, shown as a dotted line in Power BI)

---

### 1. RELATED
*   **Definition:** Retrieves a value from the "one" side of a one-to-many relationship. It allows you to "look up" a value from a related dimension table. This function is primarily used in **calculated columns** on the "many" side table.
*   **Syntax:** `RELATED(<column>)`
*   **Example:** To create a new column in the `Sales` table that shows the `Category` for each sale.
    ```dax
    // This is a new CALCULATED COLUMN in the 'Sales' table
    Product Category = RELATED(Products[Category])
    ```
    **How it works:** For each row in the `Sales` table, `RELATED` follows the active relationship to the `Products` table, finds the single matching row based on `ProductKey`, and returns the value from the `Category` column of that row.
    **Resulting `Sales` Table:**
    | ProductKey | SalesAmount | **Product Category** |
    | :--- | :--- | :--- |
    | 101 | 150 | Stationery |
    | 102 | 20 | Stationery |
    | 101 | 120 | Stationery |
    | 103 | 1200 | Electronics |

---

### 2. RELATEDTABLE
*   **Definition:** The inverse of `RELATED`. It retrieves a table of all related rows from the "many" side of a relationship. Since it returns a table, it is almost always used inside an iterator function like `SUMX`, `COUNTROWS`, etc. This function is used on the "one" side table.
*   **Syntax:** `RELATEDTABLE(<table>)`
*   **Example:** To create a new column in the `Products` table that counts the number of sales transactions for each product.
    ```dax
    // This is a new CALCULATED COLUMN in the 'Products' table
    Transaction Count = COUNTROWS(RELATEDTABLE(Sales))
    ```
    **How it works:** For each row in the `Products` table, `RELATEDTABLE(Sales)` returns a virtual table containing all the rows from the `Sales` table that match the current `ProductKey`. `COUNTROWS` then counts the rows in that virtual table.
    **Resulting `Products` Table:**
    | ProductKey | ProductName | **Transaction Count** |
    | :--- | :--- | :--- |
    | 101 | Book | 2 |
    | 102 | Pen | 1 |
    | 103 | Laptop | 1 |

---

### 3. USERELATIONSHIP
*   **Definition:** Activates an existing, *inactive* relationship for the duration of a calculation. It does not return a value itself; it is used as a filter argument inside the `CALCULATE` function.
*   **Syntax:** `USERELATIONSHIP(<column1>, <column2>)`
*   **Example:** Our default sales measure will be based on `OrderDate` because that relationship is active. To create a new measure that calculates sales based on the `ShipDate`, we must activate the inactive relationship.
    ```dax
    // This is a MEASURE
    Sales by Ship Date = 
    CALCULATE(
        SUM(Sales[SalesAmount]),
        USERELATIONSHIP('Date'[Date], Sales[ShipDate])
    )
    ```
    **How it works:** The `CALCULATE` function evaluates the sum of sales. The `USERELATIONSHIP` argument tells `CALCULATE` to ignore the active relationship to `Sales[OrderDate]` and instead use the inactive relationship to `Sales[ShipDate]` for this one calculation. Now, if you put this measure in a visual with `Date[Month]`, it will aggregate sales based on when they were shipped, not when they were ordered.

---

### 4. CROSSFILTER
*   **Definition:** Modifies the cross-filter direction of a relationship (from one-way to both, or vice-versa) for the duration of a calculation. Like `USERELATIONSHIP`, it is used as a filter argument inside `CALCULATE`.
*   **Syntax:** `CROSSFILTER(<left_columnName>, <right_columnName>, <direction>)`
    *   **Direction can be:** `OneWay`, `Both`, `None`.
*   **Example:** To count the number of distinct products that had sales in a given year. With a standard one-way filter from `Products` to `Sales`, filtering by `Sales[OrderDate]` won't filter the `Products` table.
    ```dax
    // This is a MEASURE
    Count of Products Sold = 
    CALCULATE(
        DISTINCTCOUNT(Products[ProductKey]),
        CROSSFILTER(Sales[ProductKey], Products[ProductKey], Both)
    )
    ```
    **How it works:**
    *   A simple `DISTINCTCOUNT(Products[ProductKey])` would always return 3, regardless of the year selected, because the filter context from the `Sales` table cannot flow "uphill" to the `Products` table.
    *   `CROSSFILTER(..., Both)` tells `CALCULATE` to temporarily treat the relationship as bi-directional. Now, if you filter your report to the year 2023, the filter context from the `Sales` table can travel "up" to the `Products` table, and `DISTINCTCOUNT` will correctly count only the products that had sales in 2023.