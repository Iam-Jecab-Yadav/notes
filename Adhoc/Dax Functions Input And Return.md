
**Note:** Parameter names like `<table>`, `<column>`, `<expression>`, `<value>`, `<date>`, etc., represent the type of input required. Optional parameters are often enclosed in square brackets `[]`.

---

### **Aggregation Functions**

These functions perform calculations like sum, average, count, etc., typically over a column.

1. **SUM(`<column>`)**
    - **Parameters:** A column containing the numbers to sum.
    - **Return Value:** A decimal number representing the sum of all numbers in the column.
2. **AVERAGE(`<column>`)**
    - **Parameters:** The column containing the numbers for which to compute the average.
    - **Return Value:** A decimal number representing the arithmetic mean of the numbers in the column.
3. **MIN(`<column>`)** or **MIN(`<scalar_expression1>`, `<scalar_expression2>`)**
    - **Parameters:** A column in which to find the minimum value, or two scalar expressions to compare.
    - **Return Value:** The smallest numeric value in the column or between the two expressions. Ignores logical values and text.
4. **MAX(`<column>`)** or **MAX(`<scalar_expression1>`, `<scalar_expression2>`)**
    - **Parameters:** A column in which to find the maximum value, or two scalar expressions to compare.
    - **Return Value:** The largest numeric value in the column or between the two expressions. Ignores logical values and text.
5. **COUNT(`<column>`)**
    - **Parameters:** The column containing the values to count.
    - **Return Value:** An integer representing the number of rows in the specified column that contain numbers.
6. **COUNTA(`<column>`)**
    - **Parameters:** The column containing the values to count.
    - **Return Value:** An integer representing the number of rows in the specified column that are not empty (counts numbers, text, logical values, errors, but not blanks).
7. **COUNTROWS(`[<table>]`)**
    - **Parameters:** (Optional) The table whose rows will be counted, or an expression returning a table. If omitted, it counts rows in the base table of the current context.
    - **Return Value:** An integer representing the number of rows in the table.
8. **DISTINCTCOUNT(`<column>`)**
    - **Parameters:** The column from which to count distinct values.
    - **Return Value:** An integer representing the number of unique non-blank values in the column.
9. **SUMX(`<table>`, `<expression>`)**
    - **Parameters:** The table over which the expression will be evaluated; The expression to be evaluated for each row of the table.
    - **Return Value:** A decimal number representing the sum of the expression evaluated for each row in the table.
10. **AVERAGEX(`<table>`, `<expression>`)**
    - **Parameters:** The table over which the expression will be evaluated; The expression to be evaluated for each row of the table.
    - **Return Value:** A decimal number representing the average of the expression evaluated for each row in the table.
11. **COUNTX(`<table>`, `<expression>`)**
    - **Parameters:** The table over which the expression will be evaluated; The expression to be evaluated for each row of the table.
    - **Return Value:** An integer representing the count of rows for which the expression evaluates to a non-blank result.
12. **MINX(`<table>`, `<expression>`, `[<variant>]`)**
    - **Parameters:** The table over which the expression will be evaluated; The expression to be evaluated for each row; (Optional) Specifies if expression evaluates as number or text (variant not commonly used).
    - **Return Value:** The minimum value resulting from evaluating the expression for each row.
13. **MAXX(`<table>`, `<expression>`, `[<variant>]`)**
    - **Parameters:** The table over which the expression will be evaluated; The expression to be evaluated for each row; (Optional) Specifies if expression evaluates as number or text (variant not commonly used).
    - **Return Value:** The maximum value resulting from evaluating the expression for each row.
14. **MEDIAN(`<column>`)**
    - **Parameters:** The column containing the numbers for which to calculate the median.
    - **Return Value:** A decimal number representing the median (middle value) of the numbers in the column.
15. **MEDIANX(`<table>`, `<expression>`)**
    - **Parameters:** The table containing the rows for which the expression will be evaluated; The expression to be evaluated for each row of the table.
    - **Return Value:** A1 decimal number representing the median of the expression evaluated for each row.
16. **PRODUCT(`<column>`)**
    - **Parameters:** The column that contains the numbers for which the product is computed.
    - **Return Value:** A decimal number representing the product of the numbers.
17. **PRODUCTX(`<table>`, `<expression>`)**
    - **Parameters:** The table containing the rows for which the expression will be evaluated; The expression to be evaluated for each row of the table.
    - **Return Value:** A2 decimal number representing the product of an expression evaluated for each row in a table.

---

### **Filter Functions**

These functions manipulate the filter context or return tables based on filters.

1. **CALCULATE(`<expression>`, `[<filter1>]`, `[<filter2>]`, ...)**
    - **Parameters:** The expression to be evaluated (often an aggregation); One or more boolean filter expressions or filter modifier functions (like ALL, KEEPFILTERS, etc.).
    - **Return Value:** A scalar value representing the result of the expression evaluated in the modified filter context.
2. **FILTER(`<table>`, `<filter_expression>`)**
    - **Parameters:** The table to be filtered (or an expression returning a table); A boolean expression to be evaluated for each row of the table.
    - **Return Value:** A table containing only the rows for which the filter expression evaluates to TRUE.
3. **ALL(`[<table> | <column>]`, `[<column>]`, ...)**
    - **Parameters:** (Optional) A table or one or more columns from which to remove filters. If no argument, removes all filters from the entire model in the current context.
    - **Return Value:** A table (if table argument) or a list of values (if column argument) with all filters removed. Used primarily as a filter modifier within CALCULATE.
4. **ALLEXCEPT(`<table>`, `<column1>`, `[<column2>]`, ...)**
    - **Parameters:** The table from which to remove filters; One or more columns whose filters should be preserved.
    - **Return Value:** A table with all filters removed except for the filters on the specified columns. Used primarily as a filter modifier within CALCULATE.
5. **ALLSELECTED(`[<table> | <column>]`)**
    - **Parameters:** (Optional) A table or column.
    - **Return Value:** Removes context filters from columns and rows in the current query, while retaining all other context filters or explicit filters.3 Used primarily as a filter modifier within CALCULATE.
6. **VALUES(`<TableNameOrColumnName>`)**
    - **Parameters:** A table name or a column name.
    - **Return Value:** When a column name is given, returns a single-column table of unique values (includes BLANK if present due to referential integrity). When a table name is given, returns the table with duplicate rows preserved (plus a blank row if referential integrity issues exist).
7. **DISTINCT(`<column>` or `<table>`)**
    - **Parameters:** A column or a table expression.
    - **Return Value:** When a column name is given, returns a single-column table of unique values (does not include the blank row generated by referential integrity violations unless BLANK is a value in the column itself). When a table expression is given, returns a table with duplicate rows removed.
8. **RELATED(`<column>`)**
    - **Parameters:** A column from a related table (on the 'one' side of a one-to-many relationship).
    - **Return Value:** The related value from the specified column for the current row. Requires an active relationship.
9. **RELATEDTABLE(`<table>`)**
    - **Parameters:** A table name (on the 'many' side of a one-to-many relationship).
    - **Return Value:** A table containing all rows related to the current row from the specified table.
10. **LOOKUPVALUE(`<result_columnName>`, `<search_columnName>`, `<search_value>`, `[<search_columnName2>, <search_value2>]`, ..., `[<alternateResult>]`)**
    - **Parameters:** The column containing the value to return; The column containing the search value; The value to search for; (Optional) Additional search columns/values; (Optional) Value returned if no match or multiple matches found.
    - **Return Value:** The value from `result_columnName` for the row that meets all search criteria. Returns `alternateResult` or BLANK if zero or more than one row matches. Does not require a relationship.
11. **KEEPFILTERS(`<expression>`)**
    - **Parameters:** An expression (typically a filter argument within CALCULATE).
    - **Return Value:** Modifies how filters are applied within CALCULATE, preserving existing context filters instead of overriding them. Returns the value of the expression.
12. **REMOVEFILTERS(`[<table> | <column>]`, `[<column>]`, ...)**
    - **Parameters:** (Optional) A table or one or more columns from which to remove filters. Equivalent to `ALL` when used as a CALCULATE modifier.
    - **Return Value:** Clears filters from the specified tables or columns. Used as a CALCULATE modifier.
13. **SELECTEDVALUE(`<columnName>`, `[<alternateResult>]`)**
    - **Parameters:** The column for which to check if only one value is selected in the current context; (Optional) The value to return if zero or more than one value is selected.
    - **Return Value:** The single distinct value of the column if only one value is filtered in the current context; otherwise, returns `alternateResult` or BLANK.

---

### **Time Intelligence Functions**

These functions perform calculations over time periods and require a well-formed Date table marked as such.

1. **DATEADD(`<dates>`, `<number_of_intervals>`, `<interval>`)**
    - **Parameters:** A column containing dates; The number of intervals to shift; The interval unit (DAY, MONTH, QUARTER, YEAR).
    - **Return Value:** A table containing a single column of dates shifted forward or backward in time.
2. **DATESBETWEEN(`<dates>`, `<start_date>`, `<end_date>`)**
    - **Parameters:** A column containing dates; The start date (scalar date value); The end date (scalar date value).
    - **Return Value:** A table containing a single column of dates between the specified start and end dates, inclusive.
3. **DATESINPERIOD(`<dates>`, `<start_date>`, `<number_of_intervals>`, `<interval>`)**
    - **Parameters:** A column containing dates; The date marking the end of the period; The number of intervals to include; The interval unit (DAY, MONTH, QUARTER, YEAR).
    - **Return Value:** A table containing a single column of dates within the specified period.
4. **DATESYTD(`<dates>`, `[<year_end_date>]`)**
    - **Parameters:** A column containing dates; (Optional) A literal string specifying the year-end date (e.g., "6/30").
    - **Return Value:** A table containing a single column of dates for the Year-To-Date in the current context.
5. **DATESQTD(`<dates>`, `[<year_end_date>]`)**
    - **Parameters:** A column containing dates; (Optional) Year-end date string.
    - **Return Value:** A table containing dates for the Quarter-To-Date.
6. **DATESMTD(`<dates>`, `[<year_end_date>]`)**
    - **Parameters:** A column containing dates; (Optional) Year-end date string.
    - **Return Value:** A table containing dates for the Month-To-Date.
7. **SAMEPERIODLASTYEAR(`<dates>`)**
    - **Parameters:** A column containing dates.
    - **Return Value:** A table containing a single column of dates shifted back one year from the dates in the current context.
8. **PREVIOUSDAY/MONTH/QUARTER/YEAR(`<dates>`, `[<number_of_intervals>]`, `[<year_end_date>]`)**
    - **Parameters:** A column containing dates; (Optional) Number of intervals back (default 1); (Optional) Year-end date string.
    - **Return Value:** A table containing dates for the single previous period (day, month, quarter, year).
9. **NEXTDAY/MONTH/QUARTER/YEAR(`<dates>`, `[<number_of_intervals>]`, `[<year_end_date>]`)**
    - **Parameters:** A column containing dates; (Optional) Number of intervals forward (default 1); (Optional) Year-end date string.
    - **Return Value:** A table containing dates for the single next period.
10. **TOTALYTD/QTD/MTD(`<expression>`, `<dates>`, `[<filter>]`, `[<year_end_date>]`)**
    - **Parameters:** The expression to evaluate (e.g., SUM(Sales[Amount])); The date column; (Optional) A filter expression; (Optional) Year-end date string.
    - **Return Value:** A scalar value representing the expression evaluated for the relevant period-to-date.
11. **ENDOFYEAR/QUARTER/MONTH(`<dates>`, `[<year_end_date>]`)**
    - **Parameters:** A column containing dates; (Optional) Year-end date string.
    - **Return Value:** A table containing the last date(s) of the year/quarter/month in the current context.
12. **STARTOFYEAR/QUARTER/MONTH(`<dates>`, `[<year_end_date>]`)**
    - **Parameters:** A column containing dates; (Optional) Year-end date string.
    - **Return Value:** A table containing the first date(s) of the year/quarter/month in the current context.
13. **PARALLELPERIOD(`<dates>`, `<number_of_intervals>`, `<interval>`)**
    - **Parameters:** A column containing dates; The number of intervals to shift (positive or negative); The interval unit (MONTH, QUARTER, YEAR).
    - **Return Value:** A table containing dates representing a period parallel to the dates in the current context, shifted by the specified intervals.
14. **LASTDATE(`<dates>`)**
    - **Parameters:** A column containing dates.
    - **Return Value:** A table containing a single column and single row with the latest date in the current context.
15. **FIRSTDATE(`<dates>`)**
    - **Parameters:** A column containing dates.
    - **Return Value:** A table containing a single column and single row with the earliest date in the current context.
16. **CALENDAR(`<start_date>`, `<end_date>`)**
    - **Parameters:** Start date (scalar date value); End date (scalar date value).
    - **Return Value:** A table with a single column named "Date" containing a contiguous set of dates.
17. **CALENDARAUTO(`[<fiscal_year_end_month>]`)**
    - **Parameters:** (Optional) An integer from 1 to 12 representing the last month of the fiscal year.
    - **Return Value:** A table with a single column named "Date" containing a contiguous set of dates automatically determined from the data model.
18. **CLOSINGBALANCEMONTH/QUARTER/YEAR(`<expression>`, `<dates>`, `[<filter>]`)**
    - **Parameters:** The expression to evaluate; The date column; (Optional) A filter expression.
    - **Return Value:** Evaluates the expression at the last date of the month/quarter/year in the current context.
19. **OPENINGBALANCEMONTH/QUARTER/YEAR(`<expression>`, `<dates>`, `[<filter>]`, `[<year_end_date>]`)**
    - **Parameters:** The expression to evaluate; The date column; (Optional) A filter expression; (Optional) Year-end date string.
    - **Return Value:** Evaluates the expression at the last date of the period _prior_ to the first date of the month/quarter/year in the current context.

---

### **Logical Functions**

These functions evaluate conditions and return TRUE/FALSE or conditional results.

1. **IF(`<logical_test>`, `<value_if_true>`, `[<value_if_false>]`)**
    - **Parameters:** An expression that evaluates to TRUE or FALSE; The value to return if TRUE; (Optional) The value to return if FALSE (defaults to BLANK).
    - **Return Value:** `value_if_true` or `value_if_false` based on the logical test.
2. **AND(`<logical1>`, `<logical2>`)**
    - **Parameters:** Two logical expressions.
    - **Return Value:** TRUE if both arguments are TRUE; otherwise, FALSE.
3. **OR(`<logical1>`, `<logical2>`)**
    - **Parameters:** Two logical expressions.
    - **Return Value:** TRUE if at least one argument is TRUE; otherwise, FALSE.
4. **NOT(`<logical>`)**
    - **Parameters:** A logical expression.
    - **Return Value:** Reverses the logical value: TRUE becomes FALSE, FALSE becomes TRUE.
5. **SWITCH(`<expression>`, `<value1>`, `<result1>`, `[<value2>, <result2>]`, ..., `[<else>]`)**
    - **Parameters:** An expression to evaluate; A series of value/result pairs; (Optional) A default result if no value matches.
    - **Return Value:** The result corresponding to the first matching value, or the `else` result (or BLANK) if no match.
6. **IFERROR(`<value>`, `<value_if_error>`)**
    - **Parameters:** The expression to evaluate; The value to return if the first expression results in an error.
    - **Return Value:** The result of the first expression, or `value_if_error` if the first expression generates an error.
7. **TRUE()**
    - **Parameters:** None.
    - **Return Value:** The logical value TRUE.
8. **FALSE()**
    - **Parameters:** None.
    - **Return Value:** The logical value FALSE.

---

### **Text Functions**

These functions manipulate or analyze text strings.

1. **CONCATENATE(`<text1>`, `<text2>`)**
    - **Parameters:** The first text string or column; The second text string or column.
    - **Return Value:** A text string resulting from joining the two input strings.
2. **CONCATENATEX(`<table>`, `<expression>`, `[<delimiter>]`)**
    - **Parameters:** The table containing rows to iterate over; The text expression to evaluate for each row; (Optional) The delimiter to insert between concatenated results.
    - **Return Value:** A text string formed by concatenating the expression results for each row, optionally separated by a delimiter.
3. **LEFT(`<text>`, `[<num_chars>]`)**
    - **Parameters:** The text string or column; (Optional) The number of characters to extract from the left (default is 1).
    - **Return Value:** A text string containing the specified number of leftmost characters.
4. **RIGHT(`<text>`, `[<num_chars>]`)**
    - **Parameters:** The text string or column; (Optional) The number of characters to extract from the right (default is 1).
    - **Return Value:** A text string containing the specified number of rightmost characters.
5. **MID(`<text>`, `<start_num>`, `<num_chars>`)**
    - **Parameters:** The text string or column; The starting position (1-based); The number of characters to extract.
    - **Return Value:** A text string containing the specified number of characters from the middle of the text.
6. **LEN(`<text>`)**
    - **Parameters:** The text string or column.
    - **Return Value:** An integer representing the number of characters in the text string.
7. **FIND(`<find_text>`, `<within_text>`, `[<start_num>]`, `[<NotFoundValue>]`)**
    - **Parameters:** The text to find; The text containing the text to find; (Optional) Starting position for search (default 1); (Optional) Value to return if text not found.
    - **Return Value:** An integer representing the starting position of the found text (case-sensitive). Returns error or `NotFoundValue` if not found.
8. **SEARCH(`<find_text>`, `<within_text>`, `[<start_num>]`, `[<NotFoundValue>]`)**
    - **Parameters:** The text to find; The text containing the text to find; (Optional) Starting position for search (default 1); (Optional) Value to return if text not found.
    - **Return Value:** An integer representing the starting position of the found text (case-insensitive). Returns error or `NotFoundValue` if not found.
9. **REPLACE(`<old_text>`, `<start_num>`, `<num_chars>`, `<new_text>`)**
    - **Parameters:** The original text; The starting position; The number of characters to replace; The new text to insert.
    - **Return Value:** A text string with the specified part replaced.
10. **SUBSTITUTE(`<text>`, `<old_text>`, `<new_text>`, `[<instance_num>]`)**
    - **Parameters:** The original text; The text to be replaced; The replacement text; (Optional) Which occurrence to replace (if omitted, all occurrences are replaced).
    - **Return Value:** A text string with occurrences of `old_text` replaced by `new_text`.
11. **UPPER(`<text>`)**
    - **Parameters:** The text string or column to convert.
    - **Return Value:** A text string converted to uppercase.
12. **LOWER(`<text>`)**
    - **Parameters:** The text string or column to convert.
    - **Return Value:** A text string converted to lowercase.
13. **TRIM(`<text>`)**
    - **Parameters:** The text string or column to trim.
    - **Return Value:** A text string with leading and trailing spaces removed.
14. **FORMAT(`<value>`, `<format_string>`)**
    - **Parameters:** The value (numeric, date, etc.) to format; A standard or custom format string.
    - **Return Value:** A text string representing the value formatted according to the format string.
15. **VALUE(`<text>`)**
    - **Parameters:** A text string that represents a number.
    - **Return Value:** A numeric value converted from the text string.

---

### **Math and Trig Functions**

These functions perform mathematical and trigonometric calculations.

1. **ABS(`<number>`)**
    - **Parameters:** A number or numeric expression.
    - **Return Value:** The absolute (non-negative) value of the number.
2. **SQRT(`<number>`)**
    - **Parameters:** A non-negative number or numeric expression.
    - **Return Value:** The square root of the number.
3. **POWER(`<number>`, `<power>`)**
    - **Parameters:** The base number; The exponent.
    - **Return Value:** The number raised to the specified power.
4. **ROUND(`<number>`, `<num_digits>`)**
    - **Parameters:** The number to round; The number of decimal places to round to.
    - **Return Value:** The number rounded to the specified number of digits.
5. **INT(`<number>`)**
    - **Parameters:** The number to round down.
    - **Return Value:** The integer part of the number, rounded down to the nearest integer.
6. **DIVIDE(`<numerator>`, `<denominator>`, `[<alternate_result>]`)**
    - **Parameters:** The numerator; The denominator; (Optional) The value to return in case of division by zero (default is BLANK).
    - **Return Value:** The result of the division, or the alternate result if division by zero occurs. Safer than using the `/` operator.
7. **MOD(`<number>`, `<divisor>`)**
    - **Parameters:** The number to divide; The divisor.
    - **Return Value:** The remainder after division.
8. **PI()**
    - **Parameters:** None.
    - **Return Value:** The mathematical constant Pi (π≈3.14159).
9. **RAND()**
    - **Parameters:** None.
    - **Return Value:** A random number greater than or equal to 0 and less than 1. (Volatile function).
10. **SIGN(`<number>`)**
    - **Parameters:** A number or numeric expression.
    - **Return Value:** 1 if the number is positive, 0 if zero, -1 if negative.

---

### **Information Functions**

These functions provide information about values, data types, or filter context.

1. **ISBLANK(`<value>`)**
    - **Parameters:** The value or expression to check.
    - **Return Value:** TRUE if the value is BLANK; otherwise, FALSE.
2. **ISNUMBER(`<value>`)**
    - **Parameters:** The value or expression to check.
    - **Return Value:** TRUE if the value is numeric; otherwise, FALSE.
3. **ISTEXT(`<value>`)**
    - **Parameters:** The value or expression to check.
    - **Return Value:** TRUE if the value is text; otherwise, FALSE.
4. **ISLOGICAL(`<value>`)**
    - **Parameters:** The value or expression to check.
    - **Return Value:** TRUE if the value is a logical value (TRUE/FALSE); otherwise, FALSE.
5. **ISERROR(`<value>`)**
    - **Parameters:** The value or expression to check.
    - **Return Value:** TRUE if the value is any error value; otherwise, FALSE.
6. **ISFILTERED(`<TableNameOrColumnName>`)**
    - **Parameters:** A table name or column name.
    - **Return Value:** TRUE if the specified table or column is being directly filtered in the current context; otherwise, FALSE.
7. **ISCROSSFILTERED(`<columnName>`)**
    - **Parameters:** A column name.
    - **Return Value:** TRUE if the specified column is being filtered by a filter applied to another column in the same or related table (cross-filtered); otherwise, FALSE.
8. **HASONEVALUE(`<columnName>`)**
    - **Parameters:** A column name.
    - **Return Value:** TRUE if the column has exactly one distinct value in the current filter context; otherwise, FALSE.
9. **HASONEFILTER(`<columnName>`)**
    - **Parameters:** A column name.
    - **Return Value:** TRUE if the column has exactly one filter applied directly to it; otherwise, FALSE.
10. **USERNAME()**
    - **Parameters:** None.
    - **Return Value:** A string containing the domain name and username of the current user (domain\user). Deprecated in favor of USERPRINCIPALNAME().
11. **USERPRINCIPALNAME()**
    - **Parameters:** None.
    - **Return Value:** A string containing the User Principal Name (UPN), typically the email address used for logging into Power BI service or the user account in Analysis Services.

---

### **Parent-Child Functions**

Used for navigating hierarchical data structured within a single table.

1. **PATH(`<ID_columnName>`, `<parent_columnName>`)**
    - **Parameters:** The column containing the item identifier; The column containing the parent identifier.
    - **Return Value:** A delimited text string representing the path from the top-level parent to the current item ID.
2. **PATHCONTAINS(`<path>`, `<item>`)**
    - **Parameters:** A text string generated by PATH(); The item identifier to search for within the path.
    - **Return Value:** TRUE if the specified item exists within the specified path; otherwise, FALSE.
3. **PATHITEM(`<path>`, `<position>`, `[<type>]`)**
    - **Parameters:** A text string generated by PATH(); The position from the left (1-based) whose item should be returned; (Optional) 1 for integer return type, 0 or omitted for text.
    - **Return Value:** The item identifier at the specified position within the path.
4. **PATHLENGTH(`<path>`)**
    - **Parameters:** A text string generated by PATH().
    - **Return Value:** An integer representing the number of levels (items) in the specified path.

---

### **Table Manipulation Functions**

These functions return or modify entire tables.

1. **ADDCOLUMNS(`<table>`, `<name>`, `<expression>`, `[<name2>, <expression2>]`, ...)**
    - **Parameters:** The table to add columns to; The name of the new column; The DAX expression defining the column's values; (Optional) Additional name/expression pairs.
    - **Return Value:** A table with the original columns plus the newly added calculated columns.
2. **SELECTCOLUMNS(`<table>`, `<name>`, `<scalar_expression>`, `[<name2>, <scalar_expression2>]`, ...)**
    - **Parameters:** The table to select columns from; The name for the new column; A scalar expression defining the column's values; (Optional) Additional name/expression pairs.
    - **Return Value:** A new table containing only the specified calculated columns.
3. **SUMMARIZE(`<table>`, `<groupBy_columnName1>`, `[<groupBy_columnName2>]`, ..., `[<name>, <expression>]`, ...)**
    - **Parameters:** The table to summarize; One or more columns to group by; (Optional) Names and expressions for aggregation columns.
    - **Return Value:** A summary table containing the group-by columns and the aggregated results. (Note: SUMMARIZECOLUMNS is generally preferred for performance).
4. **SUMMARIZECOLUMNS(`<groupBy_columnName1>`, `[<groupBy_columnName2>]`, ..., `[<filterTable1>]`, ..., `<name>`, `<expression>`, ...)**
    - **Parameters:** One or more columns to group by; (Optional) Filter table expressions; Names and DAX expressions for aggregation columns.
    - **Return Value:** A summary table based on the specified groupings, filters, and aggregations. More efficient than SUMMARIZE.
5. **UNION(`<table>`, `<table>`, `[<table>]`, ...)**
    - **Parameters:** Two or more tables with matching numbers of columns and compatible data types.
    - **Return Value:** A table containing all rows from each input table (duplicates are preserved).
6. **INTERSECT(`<left_table>`, `<right_table>`)**
    - **Parameters:** Two tables with matching numbers of columns and compatible data types.
    - **Return Value:** A table containing only the rows that exist in both input tables (duplicates removed).
7. **EXCEPT(`<left_table>`, `<right_table>`)**
    - **Parameters:** Two tables with matching numbers of columns and compatible data types.
    - **Return Value:** A table containing the rows from the left table that do not exist in the right table (duplicates removed).
8. **CROSSJOIN(`<table>`, `<table>`, ...)**
    - **Parameters:** Two or more tables.
    - **Return Value:** A table containing the Cartesian product of all rows from all input tables. Use with caution due to potentially large size.
9. **GENERATESERIES(`<startValue>`, `<endValue>`, `[<incrementValue>]`)**
    - **Parameters:** The starting value of the sequence; The ending value; (Optional) The increment value (default is 1).
    - **Return Value:** A single-column table named "Value" containing a series of numbers from start to end, incremented by the specified step.
10. **ROW(`<name>`, `<expression>`, `[<name2>, <expression2>]`, ...)**
    - **Parameters:** A name for the column; A DAX expression resulting in a scalar value; (Optional) Additional name/expression pairs.
    - **Return Value:** A table with a single row and columns defined by the name/expression pairs.
11. **DATATABLE(`<columnName1>`, `<dataType1>`, `<columnName2>`, `<dataType2>`, ..., `{{<value1_1>, <value1_2>, ...}, {<value2_1>, <value2_2>, ...}, ...}`)**
    - **Parameters:** Column names and their data types (STRING, INTEGER, DOUBLE, DATETIME, CURRENCY, BOOLEAN); A nested set of curly braces containing the data rows.
    - **Return Value:** An inline table defined by the specified columns, data types, and values.

---

### **Other Functions**

1. **BLANK()**
    - **Parameters:** None.
    - **Return Value:** Represents a DAX Blank value, similar to SQL NULL.
2. **USERELATIONSHIP(`<columnName1>`, `<columnName2>`)**
    - **Parameters:** The column on the 'many' side of the relationship; The column on the 'one' side of the relationship.
    - **Return Value:** Does not return a value directly but specifies an inactive relationship to be used for a specific calculation, typically within a CALCULATE function.

---
