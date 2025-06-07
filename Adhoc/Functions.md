

**Important Notes:**

- **Syntax:** Placeholders like `<column>`, `<expression>`, `<table>`, `<value>`, etc., should be replaced with actual table/column names or DAX expressions. Optional arguments are often enclosed in `[...]`.
- **Context:** The behavior of many DAX functions depends heavily on the _evaluation context_ (row context and filter context), which is a core concept in DAX.

---

**1. Aggregation Functions**

These functions perform calculations like sum, average, count over a column.

1. **SUM**
    - **Syntax:** `SUM(<column>)`
    - **Description:** Adds all the numbers in a column.
2. **AVERAGE**
    - **Syntax:** `AVERAGE(<column>)`
    - **Description:** Calculates the arithmetic mean of the values in a column. Ignores non-numeric values and blanks.
3. **MIN**
    - **Syntax:** `MIN(<column>)` or `MIN(<scalar1>, <scalar2>)`
    - **Description:** Returns the smallest numeric value in a column, or the smaller of two scalar expressions. Can also compare dates or text strings.
4. **MAX**
    - **Syntax:** `MAX(<column>)` or `MAX(<scalar1>, <scalar2>)`
    - **Description:** Returns the largest numeric value in a column, or the larger of two scalar expressions. Can also compare dates or text strings.
5. **COUNT**
    - **Syntax:** `COUNT(<column>)`
    - **Description:** Counts the number of cells in a column that contain numbers.
6. **COUNTA**
    - **Syntax:** `COUNTA(<column>)`
    - **Description:** Counts the number of non-blank cells in a column (numbers, text, dates, Booleans).
7. **COUNTROWS**
    - **Syntax:** `COUNTROWS([<table>])`
    - **Description:** Counts the number of rows in the specified table, or the current table if omitted, considering the current filter context.
8. **DISTINCTCOUNT**
    - **Syntax:** `DISTINCTCOUNT(<column>)`
    - **Description:** Counts the number of unique (distinct) values in a column.
9. **DISTINCTCOUNTNOBLANK**
    - **Syntax:** `DISTINCTCOUNTNOBLANK(<column>)`
    - **Description:** Counts the number of unique (distinct) non-blank values in a column.

**2. Iterator ('X') Aggregation Functions**

These functions iterate row by row over a table, perform an expression, and then aggregate the results.

1. **SUMX**
    - **Syntax:** `SUMX(<table>, <expression>)`
    - **Description:** Evaluates an expression for each row of a table and then sums up the results.
2. **AVERAGEX**
    - **Syntax:** `AVERAGEX(<table>, <expression>)`
    - **Description:** Evaluates an expression for each row of a table and then calculates the average of the results.
3. **MINX**
    - **Syntax:** `MINX(<table>, <expression>)`
    - **Description:** Evaluates an expression for each row of a table and returns the minimum value.
4. **MAXX**
    - **Syntax:** `MAXX(<table>, <expression>)`
    - **Description:** Evaluates an expression for each row of a table and returns the maximum value.
5. **COUNTX**
    - **Syntax:** `COUNTX(<table>, <expression>)`
    - **Description:** Evaluates an expression for each row of a table and counts the number of non-blank results.
6. **RANKX**
    - **Syntax:** `RANKX(<table>, <expression>[, <value>[, <order>[, <ties>]]])`
    - **Description:** Returns the ranking of a number for each row in a table within the context of the entire table evaluated based on the expression.

**3. Filter Functions**

These functions modify the filter context or return tables based on filters.

1. **CALCULATE**
    - **Syntax:** `CALCULATE(<expression>[, <filter1> [, <filter2> [, ...]]])`
    - **Description:** _The most important DAX function._ Evaluates an expression in a modified filter context. The filters overwrite any existing filters on the same columns.
2. **FILTER**
    - **Syntax:** `FILTER(<table>, <filter_expression>)`
    - **Description:** Returns a table that represents a subset of another table, based on a filter condition evaluated row by row. Often used within `CALCULATE` or iterator functions.
3. **ALL**
    - **Syntax:** `ALL( [<table> | <column>[, <column>[, ...]]] )`
    - **Description:** Returns all rows in a table or all values in one or more columns, ignoring any filters that might have been applied. Used as a filter modifier in `CALCULATE`.
4. **ALLEXCEPT**
    - **Syntax:** `ALLEXCEPT(<table>, <column>[, <column>[, ...]])`
    - **Description:** Removes all context filters in the table except filters that have been applied to the specified columns. Used as a filter modifier in `CALCULATE`.
5. **ALLSELECTED**
    - **Syntax:** `ALLSELECTED( [<table> | <column>[, <column>[, ...]]] )`
    - **Description:** Removes context filters from columns and rows in the current query while retaining all other context filters or explicit filters. Useful for calculating percentages of totals visible in the current selection.
    - The DAX function `ALLSELECTED` returns all the rows in a table or all the values in a column, while ignoring any **filters that might have been applied inside the query (visual-level filters)**, but keeping **filters that come from outside the query (like slicers and other filter contexts)**.
6. **KEEPFILTERS**
    - **Syntax:** `KEEPFILTERS(<expression>)`
    - **Description:** Modifies how filters are applied while evaluating a `CALCULATE` or `CALCULATETABLE` function. It intersects the filter arguments with the existing filter context instead of overwriting.
7. **REMOVEFILTERS**
    - **Syntax:** `REMOVEFILTERS([<table> | <column>[, <column>[, ...]]])`
    - **Description:** Clears filters from the specified tables or columns. Functionally similar to `ALL` when used as a `CALCULATE` modifier.
8. **VALUES**
    - **Syntax:** `VALUES(<table_or_column>)`
    - **Description:** Returns a one-column table containing the distinct values from the specified column, considering the current filter context. If a table name is provided, returns the distinct rows. Includes the BLANK value if present.
9. **DISTINCT**
    - **Syntax:** `DISTINCT(<column>)` or `DISTINCT(<table>)`
    - **Description:** Returns a one-column table containing the distinct values from the specified column, or distinct rows from a table, considering the current filter context. Does _not_ include the BLANK value unless it's part of the data.
10. **SELECTEDVALUE**
    - **Syntax:** `SELECTEDVALUE(<columnName>[, <alternateResult>])`
    - **Description:** Returns the value when the context for columnName has been filtered down to one distinct value only. Otherwise returns the alternate result2 (or BLANK). Useful for getting user selections from slicers.

**4. Time Intelligence Functions**

These require a well-formed 'Date' table marked as such in the data model.

1. **DATESYTD**
    - **Syntax:** `DATESYTD(<dates>[, <year_end_date>])`
    - **Description:** Returns a table containing a column of dates for the year-to-date, in the current context.
2. **DATESQTD**
    - **Syntax:** `DATESQTD(<dates>)`
    - **Description:** Returns a table containing a column of dates for the quarter-to-date, in the current context.
3. **DATESMTD**
    - **Syntax:** `DATESMTD(<dates>)`
    - **Description:** Returns a table containing a column of dates for the month-to-date, in the current context.
4. **TOTALYTD**
    - **Syntax:** `TOTALYTD(<expression>, <dates>[, <filter>][, <year_end_date>])`
    - **Description:** Evaluates the year-to-date value of the expression in the current context. Shortcut for `CALCULATE(<expression>, DATESYTD(<dates>[, <year_end_date>]))`.
5. **TOTALQTD**
    - **Syntax:** `TOTALQTD(<expression>, <dates>[, <filter>])`
    - **Description:** Evaluates the quarter-to-date value of the expression in the current context. Shortcut for `CALCULATE(<expression>, DATESQTD(<dates>))`.
6. **TOTALMTD**
    - **Syntax:** `TOTALMTD(<expression>, <dates>[, <filter>])`
    - **Description:** Evaluates the month-to-date value of the expression in the current context. Shortcut for `CALCULATE(<expression>, DATESMTD(<dates>))`.
7. **SAMEPERIODLASTYEAR**
    - **Syntax:** `SAMEPERIODLASTYEAR(<dates>)`
    - **Description:** Returns a table that contains a column of dates shifted one year back in time from the dates in the specified dates column, in the current context.
8. **PREVIOUSYEAR**
    - **Syntax:** `PREVIOUSYEAR(<dates>[, <year_end_date>])`
    - **Description:** Returns a table containing all dates from the previous year, based on the last date in the input column.
9. **PREVIOUSQUARTER**
    - **Syntax:** `PREVIOUSQUARTER(<dates>)`
    - **Description:** Returns a table containing all dates from the previous quarter, based on the last date in the input column.
10. **PREVIOUSMONTH**
    - **Syntax:** `PREVIOUSMONTH(<dates>)`
    - **Description:** Returns a table containing all dates from the previous month, based on the last date in the input column.
11. **DATEADD**
    - **Syntax:** `DATEADD(<dates>, <number_of_intervals>, <interval>)`
    - **Description:** Returns a table containing a column of dates, shifted either forward or backward in time by the specified number of intervals from the dates in the current context.4 Interval can be DAY, MONTH, QUARTER, YEAR.
12. **DATESBETWEEN**
    - **Syntax:** `DATESBETWEEN(<dates>, <start_date>, <end_date>)`
    - **Description:** Returns a table that contains a column of dates that begins with the start_date and continues until the end_date.
13. **DATESINPERIOD**
    - **Syntax:** `DATESINPERIOD(<dates>, <start_date>, <number_of_intervals>, <interval>)`
    - **Description:** Returns a table containing dates from a given period starting from start_date and continuing for the specified number/type of intervals.
14. **PARALLELPERIOD**
    - **Syntax:** `PARALLELPERIOD(<dates>, <number_of_intervals>, <interval>)`
    - **Description:** Returns a table containing dates that represents a period parallel to the dates in the specified column, shifted back or forward by the number/type of intervals. Differs subtly from DATEADD in context handling.
15. **FIRSTDATE**
    - **Syntax:** `FIRSTDATE(<dates>)`
    - **Description:** Returns the first date in the current filter context for the specified column of dates.
16. **LASTDATE**
    - **Syntax:** `LASTDATE(<dates>)`
    - **Description:** Returns the last date in the current filter context for the specified column of dates.
17. **STARTOFMONTH / STARTOFQUARTER / STARTOFYEAR**
    - **Syntax:** `STARTOFMONTH(<dates>)` etc.
    - **Description:** Returns the first date of the month/quarter/year in the current context.
18. **ENDOFMONTH / ENDOFQUARTER / ENDOFYEAR**
    - **Syntax:** `ENDOFMONTH(<dates>)` etc.
    - **Description:** Returns the last date of the month/quarter/year in the current context.
19. **CALENDAR**
    - **Syntax:** `CALENDAR(<start_date>, <end_date>)`
    - **Description:** Returns a table with a single column named "Date" containing a contiguous set of dates from start_date to end_date.
20. **CALENDARAUTO**
    - **Syntax:** `CALENDARAUTO([<fiscal_year_end_month>])`
    - **Description:** Returns a table with a single column named "Date" containing a contiguous set of dates calculated automatically from the data model.

**5. Logical Functions**

Used for conditional logic.

1. **IF**
    - **Syntax:** `IF(<logical_test>, <value_if_true>[, <value_if_false>])`
    - **Description:** Checks a condition, returns one value if TRUE, and optionally another value if FALSE (defaults to BLANK if omitted).
2. **AND**
    - **Syntax:** `AND(<logical1>, <logical2>)`
    - **Description:** Checks whether both arguments are TRUE, and returns TRUE if both are TRUE. Otherwise returns FALSE.
3. **OR**
    - **Syntax:** `OR(<logical1>, <logical2>)`
    - **Description:** Checks whether one of the arguments is TRUE to return TRUE. Returns FALSE only if both arguments are FALSE.
4. **NOT**
    - **Syntax:** `NOT(<logical>)`
    - **Description:** Reverses the logical value of its argument.
5. **SWITCH**
    - **Syntax:** `SWITCH(<expression>, <value1>, <result1>[, <value2>, <result2>]...[, <else>])`
    - **Description:** Evaluates an expression against a list of values and returns one of multiple possible result expressions. More efficient than nested IFs for multiple conditions.
6. **IFERROR**
    - **Syntax:** `IFERROR(<value>, <value_if_error>)`
    - **Description:** Evaluates an expression and returns a specified value if the expression returns an error; otherwise returns the value of the expression5 itself.
7. **ISBLANK**
    - **Syntax:** `ISBLANK(<value>)`
    - **Description:** Checks whether a value is blank, and returns TRUE or FALSE.

**6. Information Functions**

Provide information about data types or context.

1. **ISNUMBER**
    - **Syntax:** `ISNUMBER(<value>)`
    - **Description:** Returns TRUE if the value is numeric, otherwise FALSE.
2. **ISTEXT**
    - **Syntax:** `ISTEXT(<value>)`
    - **Description:** Returns TRUE if the value is text, otherwise FALSE.
3. **ISLOGICAL**
    - **Syntax:** `ISLOGICAL(<value>)`
    - **Description:** Returns TRUE if the value is a logical value (TRUE/FALSE), otherwise FALSE.
4. **ISERROR**
    - **Syntax:** `ISERROR(<value>)`
    - **Description:** Returns TRUE if the value is any error value, otherwise FALSE.
5. **USERNAME**
    - **Syntax:** `USERNAME()`
    - **Description:** Returns the domain name and username from the credentials given to the system at connection time. (Use `USERPRINCIPALNAME()` for Power BI Service UPN).
6. **UTCNOW / NOW**
    - **Syntax:** `UTCNOW()` / `NOW()`
    - **Description:** Returns the current date and time in UTC format (`UTCNOW`) or based on system settings (`NOW`). Note: In measures, these only update on data refresh/recalculation, not continuously.
7. **HASONEVALUE**
    - **Syntax:** `HASONEVALUE(<columnName>)`
    - **Description:** Returns TRUE when the context for columnName has been filtered down to one distinct value only. Essentially checks if `COUNTROWS(VALUES(<columnName>)) = 1`.

**7. Text Functions**

Manipulate text strings.

1. **CONCATENATE**
    - **Syntax:** `CONCATENATE(<text1>, <text2>)`
    - **Description:** Joins two text strings into one text string. (The `&` operator is often preferred: `<text1> & <text2>`).
2. **LEFT / RIGHT**
    - **Syntax:** `LEFT(<text>, <num_chars>)` / `RIGHT(<text>, <num_chars>)`
    - **Description:** Returns the specified number of characters from the start (LEFT) or end (RIGHT) of a text string.
3. **MID**
    - **Syntax:** `MID(<text>, <start_num>, <num_chars>)`
    - **Description:** Returns a string of characters from the middle of a text string, given a starting position and length.
4. **LEN**
    - **Syntax:** `LEN(<text>)`
    - **Description:** Returns the number of characters in a text string.
5. **FIND**
    - **Syntax:** `FIND(<find_text>, <within_text>[, <start_num>][, <NotFoundValue>])`
    - **Description:** Locates one text string within another text string, and returns the starting position. Case-sensitive.
6. **SEARCH**
    - **Syntax:** `SEARCH(<find_text>, <within_text>[, <start_num>][, <NotFoundValue>])`
    - **Description:** Locates one text string within another text string, and returns the starting position. Not case-sensitive.
7. **REPLACE**
    - **Syntax:** `REPLACE(<old_text>, <start_num>, <num_chars>, <new_text>)`
    - **Description:** Replaces part of a text string, based on the number of characters you specify, with a different text string.
8. **SUBSTITUTE**
    - **Syntax:** `SUBSTITUTE(<text>, <old_text>, <new_text>[, <instance_num>])`
    - **Description:** Replaces existing text with new text in a text string.6 Used for replacing specific occurrences of text.
9. **UPPER / LOWER**
    - **Syntax:** `UPPER(<text>)` / `LOWER(<text>)`
    - **Description:** Converts a text string to all uppercase or all lowercase letters.
10. **FORMAT**
    - **Syntax:** `FORMAT(<value>, <format_string>)`
    - **Description:** Converts a value (numeric, date/time) to text in the specified format string (e.g., "Currency", "mm/dd/yyyy", "#,##0").
11. **TRIM**
    - **Syntax:** `TRIM(<text>)`
    - **Description:** Removes all spaces from a text string except for single spaces between words.
12. **VALUE**
    - **Syntax:** `VALUE(<text>)`
    - **Description:** Converts a text string that represents a number into a numeric data type.

**8. Relationship Functions**

Leverage relationships between tables.

1. **RELATED**
    - **Syntax:** `RELATED(<column>)`
    - **Description:** Returns a related value from the "one" side of a one-to-many relationship. Used in calculated columns or row-context iterations.
2. **RELATEDTABLE**
    - **Syntax:** `RELATEDTABLE(<table>)`
    - **Description:** Returns a table of related rows from the "many" side of a relationship. Evaluates the table expression in a context modified by the current row context.
3. **USERELATIONSHIP**
    - **Syntax:** `USERELATIONSHIP(<column1>, <column2>)`
    - **Description:** Specifies an inactive relationship to be used for the duration of a `CALCULATE` or `CALCULATETABLE` computation. Does not return a value; used as a filter argument.
4. **CROSSFILTER**
    - **Syntax:** `CROSSFILTER(<column1>, <column2>, <direction>)`
    - **Description:** Specifies the cross-filtering direction (Both, OneWay, None) to be used in a calculation for a relationship that exists between two columns. Used as a filter argument in `CALCULATE`.

**9. Table Manipulation Functions**

Return or modify entire tables. Used extensively in defining calculated tables or as inputs to other functions.

1. **ADDCOLUMNS**
    - **Syntax:** `ADDCOLUMNS(<table>, <name>, <expression>[, <name>, <expression>]...)`
    - **Description:** Adds calculated columns to the given table or table expression.
2. **SELECTCOLUMNS**
    - **Syntax:** `SELECTCOLUMNS(<table>, <name>, <expression>[, <name>, <expression>]...)`
    - **Description:** Adds calculated columns to a _new_ table based on the input table, essentially selecting/creating specific columns.
3. **SUMMARIZE**
    - **Syntax:** `SUMMARIZE(<table>, <groupBy_columnName>[, <groupBy_columnName>]...[, <name>, <expression>]...)`
    - **Description:** Returns a summary table for the requested totals over a set of groups. Similar to SQL `GROUP BY`.
4. **UNION**
    - **Syntax:** `UNION(<table1>, <table2>[, <table3>]...)`
    - **Description:** Creates a union (appends rows) of tables that have the same number of columns. Duplicates are kept by default.
5. **INTERSECT**
    - **Syntax:** `INTERSECT(<table1>, <table2>)`
    - **Description:** Returns the rows of the left-side table which appear in the right-side table. Tables must have same number of columns. Duplicates are matched.
6. **EXCEPT**
    - **Syntax:** `EXCEPT(<table1>, <table2>)`
    - **Description:** Returns the rows of the left-side table which do not appear in the right-side table. Tables must have same number of columns. Duplicates are matched.
7. **NATURALINNERJOIN / NATURALLEFTOUTERJOIN**
    - **Syntax:** `NATURALINNERJOIN(<table>, <table>)` / `NATURALLEFTOUTERJOIN(<table>, <table>)`
    - **Description:** Joins two tables using common columns (same name and data type). `INNER` keeps only matching rows; `LEFT OUTER` keeps all rows from the left table and matching rows from the right.
8. **GENERATE / GENERATESERIES**
    - **Syntax:** `GENERATE(<table>, <table>)` / `GENERATESERIES(<startValue>, <endValue>[, <incrementValue>])`
    - **Description:** `GENERATE` applies the second table expression for each row of the first table expression (cross join based on row context). `GENERATESERIES` returns a single-column table containing a sequence of numbers.
9. **CALCULATETABLE**
    - **Syntax:** `CALCULATETABLE(<expression>[, <filter1> [, <filter2> [, ...]]])`
    - **Description:** Evaluates a table expression in a modified filter context. Similar to `CALCULATE` but returns a table instead of a scalar value.
10. **ROW**
    - **Syntax:** `ROW(<name>, <expression>[, <name>, <expression>]...)`
    - **Description:** Returns a single-row table with specified column names and expressions.
11. **DATATABLE**
    - **Syntax:** `DATATABLE(<colName1>, <dataType1>, <colName2>, <dataType2>..., {{<value1_1>, <value1_2>...}, {<value2_1>, <value2_2>...}...})`
    - **Description:** Allows you to define a table directly within your DAX code by specifying column names, data types, and the row data.

**10. Math and Statistical Functions**

Basic mathematical operations.

1. **DIVIDE**
    - **Syntax:** `DIVIDE(<numerator>, <denominator>[, <alternate_result>])`
    - **Description:** Performs division but provides a safe way to handle division by zero errors by returning an alternate result (defaults to BLANK).
2. **ROUND / ROUNDUP / ROUNDDOWN**
    - **Syntax:** `ROUND(<number>, <num_digits>)` / `ROUNDUP(...)` / `ROUNDDOWN(...)`
    - **Description:** Rounds a number to a specified number of digits (standard rounding, always up, or always down).
3. **INT**
    - **Syntax:** `INT(<number>)`
    - **Description:** Rounds a number down to the nearest integer.
4. **ABS**
    - **Syntax:** `ABS(<number>)`
    - **Description:** Returns the absolute value of a number.

**11. Date and Time Functions (Non-Time Intelligence)**

Basic extraction from date/time values.

1. **YEAR / MONTH / DAY**
    - **Syntax:** `YEAR(<date>)` / `MONTH(<date>)` / `DAY(<date>)`
    - **Description:** Extracts the year, month (1-12), or day (1-31) number from a date.
2. **HOUR / MINUTE / SECOND**
    - **Syntax:** `HOUR(<datetime>)` / `MINUTE(<datetime>)` / `SECOND(<datetime>)`
    - **Description:** Extracts the hour (0-23), minute (0-59), or second (0-59) number from a datetime value.
3. **WEEKDAY**
    - **Syntax:** `WEEKDAY(<date>[, <return_type>])`
    - **Description:** Returns a number from 1 to 7 identifying the day of the week of a date.
4. **WEEKNUM**
    - **Syntax:** `WEEKNUM(<date>[, <return_type>])`
    - **Description:** Returns the week number in the year (1-54).
5. **DATE**
    - **Syntax:** `DATE(<year>, <month>, <day>)`
    - **Description:** Creates a date value from separate year, month, and day numbers.
6. **TIME**
    - **Syntax:** `TIME(<hour>, <minute>, <second>)`
    - **Description:** Creates a time value from separate hour, minute, and second numbers.
7. **EOMONTH**
    - **Syntax:** `EOMONTH(<start_date>, <months>)`
    - **Description:** Returns the date, in datetime format, of the last day of the month before or after a specified number of months.7
8. **EDATE**
    - **Syntax:** `EDATE(<start_date>, <months>)`
    - **Description:** Returns the date that is the indicated number of months before or after the start date.

---
