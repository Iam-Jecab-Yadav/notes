
**Basic Structure:**

The most fundamental DAX query starts with the `EVALUATE` keyword followed by an expression that returns a table.

Code snippet

```
EVALUATE
<table_expression>
```

**Examples:**

- **Returning all rows from a table:**
    
    Code snippet
    
    ```
    EVALUATE
    Sales
    ```
    
    This query will return all the rows and columns from the table named "Sales".
    
- **Selecting specific columns:**
    
    Code snippet
    
    ```
    EVALUATE
    SELECTCOLUMNS(
        Sales,
        "Product Name", Sales[ProductName],
        "Total Revenue", Sales[Revenue]
    )
    ```
    
    This query uses the `SELECTCOLUMNS` function to create a new table with only the "ProductName" and "Revenue" columns from the "Sales" table, renaming them as "Product Name" and "Total Revenue" respectively.
    
- **Filtering data:**
    
    Code snippet
    
    ```
    EVALUATE
    FILTER(
        Sales,
        Sales[Region] = "North"
    )
    ```
    
    This query uses the `FILTER` function to return only the rows from the "Sales" table where the "Region" column is equal to "North".
    
- **Using measures:**
    
    Code snippet
    
    ```
    EVALUATE
    ROW(
        "Total Sales Amount", [Total Sales]
    )
    ```
    
    Assuming you have a measure named "[Total Sales]", this query will return a table with a single row and a column named "Total Sales Amount" containing the value of that measure.
    
- **Grouping and summarizing data:**
    
    Code snippet
    
    ```
    EVALUATE
    SUMMARIZECOLUMNS(
        Sales[Category],
        "Total Revenue", SUM(Sales[Revenue])
    )
    ```
    
    This query uses `SUMMARIZECOLUMNS` to group the "Sales" table by the "Category" column and calculates the sum of the "Revenue" for each category, naming the resulting column "Total Revenue".
    
- **Defining and using measures within the query:**
    
    Code snippet
    
    ```
    DEFINE
        MEASURE Sales[Average Revenue] = DIVIDE(SUM(Sales[Revenue]), COUNTROWS(Sales))
    EVALUATE
    ROW(
        "Average Revenue", [Average Revenue]
    )
    ```
    
    Here, we use the `DEFINE MEASURE` keyword to define a measure named "[Average Revenue]" within the query. Then, we use it in the `EVALUATE` statement.
    

**4. Executing Queries:**

- Once you've written your DAX query in the DAX Query View window, look for an **"Execute"** button or a similar icon (often a play button or a lightning bolt).
- Clicking this button will run your query against the connected Power BI model.
- The results of the query will be displayed in a separate pane within the DAX Query View tool, typically in a tabular format.

**Key Considerations:**

- **Table and Column Names:** Make sure you use the correct names for your tables and columns as they exist in your Power BI model.
- **Measure Names:** When referencing measures, enclose them in square brackets (e.g., `[Total Sales]`).
- **DAX Syntax:** DAX has its own specific syntax and functions. Refer to the official Microsoft DAX documentation for a comprehensive understanding of available functions and their usage.