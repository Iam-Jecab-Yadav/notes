
---

### Foundational Patterns (The Absolute Must-Knows)

These are the building blocks for almost everything else you'll do in DAX.

#### 1. The Base Aggregation Pattern
This is the simplest pattern. It's how you create your core measures.

*   **Problem:** You need to calculate a total, an average, or a count of a column.
*   **DAX Functions:** `SUM`, `AVERAGE`, `COUNT`, `DISTINCTCOUNT`, `MIN`, `MAX`
*   **Pattern:**
    ```dax
    Measure Name = AGGREGATION_FUNCTION(TableName[ColumnName])
    ```
*   **Example:**
    ```dax
    Total Sales = SUM(Sales[SalesAmount])
    ```
    ```dax
    Unique Customers = DISTINCTCOUNT(Sales[CustomerID])
    ```

#### 2. The Master Pattern: `CALCULATE`
`CALCULATE` is the most important function in DAX. It modifies the "filter context," which means it allows you to change the filters being applied to your calculation.

*   **Problem:** You need to calculate something but with a specific filter applied, or by changing an existing filter.
*   **DAX Function:** `CALCULATE`
*   **Pattern:**
    ```dax
    Measure Name = CALCULATE([Base Measure], Filter1, Filter2, ...)
    ```
*   **Example 1: Calculating Sales for a specific category.**
    ```dax
    Red Product Sales = CALCULATE([Total Sales], 'Product'[Color] = "Red")
    ```
*   **Example 2: Calculating Sales while removing all filters from the Product table (for % of total).**
    ```dax
    All Product Sales = CALCULATE([Total Sales], ALL('Product'))
    ```

---

### Intermediate Patterns (The Daily Workhorses)

You'll use these patterns in almost every report you build.

#### 3. The Time Intelligence Pattern
This is a whole family of patterns for comparing data over time (YTD, YoY, etc.).

*   **Prerequisite:** You **must** have a dedicated Date Table in your model, and it must be marked as a date table.
*   **Problem:** Compare performance over different time periods.
*   **DAX Functions:** `TOTALYTD`, `SAMEPERIODLASTYEAR`, `DATEADD`, `DATESINPERIOD`
*   **Example 1: Year-to-Date (YTD) Sales.**
    ```dax
    Sales YTD = TOTALYTD([Total Sales], 'Date'[Date])
    ```
*   **Example 2: Sales from the Previous Year (PY).**
    ```dax
    Sales PY = CALCULATE([Total Sales], SAMEPERIODLASTYEAR('Date'[Date]))
    ```
*   **Example 3: Year-over-Year (YoY) Growth Percentage.** (This pattern combines other measures).
    ```dax
    Sales YoY % = 
    VAR CurrentSales = [Total Sales]
    VAR PreviousYearSales = [Sales PY]
    RETURN
        DIVIDE(CurrentSales - PreviousYearSales, PreviousYearSales)
    ```

#### 4. The Iterator (`X` Function) Pattern
Iterators (`SUMX`, `AVERAGEX`, `RANKX`, etc.) perform a calculation for each row in a table and then aggregate the results.

*   **Problem:** You need to perform a row-level calculation first, like `Price * Quantity`, before summing it up.
*   **DAX Functions:** `SUMX`, `AVERAGEX`, `MAXX`, `MINX`, `COUNTX`
*   **Pattern:**
    ```dax
    Measure Name = ITERATOR_FUNCTION(TableName, Expression_to_calculate_per_row)
    ```
*   **Example:** Your `Sales` table has `OrderQuantity` and `UnitPrice` but no `TotalAmount` column.
    ```dax
    Total Sales (SUMX) = 
    SUMX(
        Sales, 
        Sales[OrderQuantity] * Sales[UnitPrice]
    )
    ```

#### 5. The Ranking Pattern
This is used to rank items (products, salespeople, etc.) based on a measure.

*   **Problem:** You want to see the Top N products by sales or rank every salesperson.
*   **DAX Function:** `RANKX`
*   **Pattern:**
    ```dax
    Measure Name = RANKX(ALL(TableToRank[ColumnToRank]), [MeasureToRankBy])
    ```
*   **Example: Ranking products by their total sales.** The `ALL('Product'[Product Name])` removes the filter from the visual so you can rank all products against each other.
    ```dax
    Product Sales Rank = 
    RANKX(
        ALL('Product'[Product Name]), 
        [Total Sales]
    )
    ```

#### 6. The "Percent of Total" Pattern
A very common business request to see how much a category contributes to the whole.

*   **Problem:** What percentage of total sales comes from the "Bikes" category?
*   **DAX Functions:** `DIVIDE`, `CALCULATE`, `ALL` or `ALLSELECTED`
*   **Pattern:**
    ```dax
    % of Total = DIVIDE([Base Measure], CALCULATE([Base Measure], ALL(Table[Column])))
    ```
*   **Example: Percent of Total Sales for the visible category.**
    ```dax
    % of All Product Sales = 
    DIVIDE(
        [Total Sales], 
        CALCULATE([Total Sales], ALL('Product'))
    )
    ```
    *Pro-Tip:* Use `ALLSELECTED` instead of `ALL` to calculate the percentage of a sub-total (i.e., respecting slicers outside the visual).

---

### Advanced Patterns (Solving Tricky Problems)

These patterns solve more complex scenarios and show a deeper understanding of DAX.

#### 7. The Semi-Additive Pattern
This applies to measures that can be summed across some dimensions but not others. The classic example is inventory or account balances. You sum balances across accounts, but over time, you want the *last* balance, not the sum of all daily balances.

*   **Problem:** Calculate the closing stock balance at the end of a period.
*   **DAX Functions:** `LASTDATE`, `LASTNONBLANK`, `CLOSINGBALANCEMONTH`
*   **Pattern:**
    ```dax
    Closing Balance = CALCULATE([Base Measure], LASTDATE('Date'[Date]))
    ```
*   **Example: Get the latest stock count.**
    ```dax
    Closing Stock Level = 
    CALCULATE(
        SUM(Inventory[UnitsOnHand]),
        LASTDATE('Date'[Date])
    )
    ```

#### 8. The Disconnected Table ("What-If") Pattern
This powerful technique lets you create dynamic "What-If" scenarios using slicers that are not connected to your main data model.

*   **Problem:** You want a slicer to see how sales would look with a 5%, 10%, or 15% increase.
*   **Setup:**
    1.  Create a new table (e.g., using "Enter Data") for your parameter. Let's call it `Percentage Increase` with a column `[Percent]` having values like 0.05, 0.10, 0.15.
    2.  This table has **no relationship** to any other table.
    3.  Create a slicer using the `Percentage Increase[Percent]` column.
*   **DAX Functions:** `SELECTEDVALUE`
*   **Pattern:**
    ```dax
    // Step 1: Capture the slicer selection
    Selected Increase % = SELECTEDVALUE('Percentage Increase'[Percent], 0) // 0 is the default

    // Step 2: Apply it to your measure
    Forecasted Sales = [Total Sales] * (1 + [Selected Increase %])
    ```

### Key DAX Best Practices

*   **Use Measures, Not Calculated Columns:** If you can create a measure, do it. Calculated columns are stored in memory and are not dynamic to user selections in the same way. Use them only when you need to slice/dice by the result.
*   **Use `DIVIDE`:** Always use `DIVIDE(numerator, denominator)` instead of the `/` operator to gracefully handle division-by-zero errors without your visuals breaking.
*   **Use Variables (`VAR`):** For complex formulas, use variables to break down the logic. It makes the code easier to read, debug, and often improves performance because a calculation is stored and reused.
*   **Format Your Code:** Use a tool like DAX Formatter or simply use `Shift + Enter` in the formula bar to make your code readable.
