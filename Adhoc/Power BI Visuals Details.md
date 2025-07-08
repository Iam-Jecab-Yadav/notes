

### **A. Bar and Column Charts**
These are fundamental for comparing values across different categories.

#### 1. Stacked Bar / Stacked Column Chart
*   **Description:** These charts display the relationship of individual parts to a whole. A column chart orients bars vertically, while a bar chart orients them horizontally. They show the total value for a category, broken down by a sub-category (legend).
*   **Fields/Wells:**
    *   **Y-axis** (Column) / **X-axis** (Bar): The primary categorical data (e.g., Regions, Time Periods).
    *   **X-axis** (Column) / **Y-axis** (Bar): The numerical value (e.g., Sales, Quantity).
    *   **Legend:** The sub-category to stack within each bar (e.g., Product Category).
    *   **Small multiples:** Splits the visual into multiple versions, one for each category in this field.
    *   **Tooltips:** Additional data to show on hover.
*   **Example:** Showing total sales per year (Axis), with each year's bar stacked by product category (Legend).
*   **Use Cases:**
    *   Comparing total values across categories while also showing the composition of that total.
    *   Understanding the contribution of different segments to a total.
*   **When to Avoid:**
    *   When you need to precisely compare the values of the individual segments across categories. It's hard to compare the "Furniture" segment in 2022 vs. 2023 if it's not at the bottom of the stack. Use a **Clustered Chart** instead.
    *   When you have too many legend items, making the stacks unreadable.

#### 2. Clustered Bar / Clustered Column Chart
*   **Description:** These charts compare values across categories by placing bars for sub-categories side-by-side. This makes direct comparison of sub-categories easier than in a stacked chart.
*   **Fields/Wells:** Same as Stacked Charts.
*   **Example:** Comparing sales of "Laptops" vs. "Desktops" vs. "Tablets" (Legend) across different store locations (Axis).
*   **Use Cases:**
    *   Directly comparing sub-categories against each other within a primary category.
    *   When the comparison of the sub-components is more important than the total.
*   **When to Avoid:**
    *   When the total of the sub-categories is a meaningful metric you want to display. Use a **Stacked Chart** or a **Combo Chart**.
    *   When you have many legend items, which creates too many clustered bars and makes the chart cluttered.

#### 3. 100% Stacked Bar / 100% Stacked Column Chart
*   **Description:** This chart shows the relative percentage of multiple data series in stacked bars, where the total of each stacked bar always equals 100%.
*   **Fields/Wells:** Same as Stacked Charts.
*   **Example:** Showing the market share percentage of different brands (Legend) within various countries (Axis).
*   **Use Cases:**
    *   Comparing the percentage contribution or distribution across categories.
    *   When the relative proportion is more important than the absolute total value.
*   **When to Avoid:**
    *   When the absolute total values are important for comparison. This chart hides the totals. For instance, a region with $1M in sales and one with $10k in sales would both show as a 100% bar.

#### 4. Ribbon Chart
*   **Description:** A unique visual that is similar to a stacked column chart but with connecting "ribbons" between the sections. The ribbons show how the rank or order of the sub-categories changes across the main category axis.
*   **Fields/Wells:** Same as Stacked Charts.
*   **Example:** Tracking the sales rank of different salespeople (Legend) over each quarter (Axis). The widest ribbon at the top for a given quarter belongs to the top-ranked salesperson.
*   **Use Cases:**
    *   Visualizing how the ranking of different categories changes over time or across another category.
    *   Quickly identifying which category is consistently leading or falling behind.
*   **When to Avoid:**
    *   When rank is not important. A standard stacked or clustered chart is simpler and more effective for just showing values.
    *   If there are too many legend items, making the ribbons chaotic and hard to follow.

---

### **B. Line and Area Charts**
These are ideal for showing trends and changes over a continuous scale, usually time.

#### 5. Line Chart
*   **Description:** Displays a series of data points connected by straight lines. Excellent for visualizing trends in data over continuous intervals or time spans.
*   **Fields/Wells:**
    *   **X-axis:** The continuous dimension, typically a date/time field.
    *   **Y-axis:** The numerical value to be plotted.
    *   **Secondary y-axis:** A second numerical value with a different scale.
    *   **Legend:** Creates a separate line for each item in this category.
    *   **Small multiples:** Creates multiple charts for different categories.
    *   **Tooltips:** Additional data to show on hover.
*   **Example:** Showing daily website traffic (Y-axis) over the last month (X-axis).
*   **Use Cases:**
    *   Tracking changes over time (e.g., stock prices, temperature, monthly sales).
    *   Comparing trends for multiple series (using the Legend field).
*   **When to Avoid:**
    *   When the X-axis is not continuous or ordered (e.g., comparing sales across different product categories). Use a **Bar/Column Chart** instead.

#### 6. Area Chart / Stacked Area Chart
*   **Description:** An Area Chart is a line chart with the area below the line filled in, emphasizing the magnitude of change (volume). A Stacked Area Chart is like a stacked bar chart over a continuous axis, showing how the parts of a whole change over time.
*   **Fields/Wells:** Same as Line Chart.
*   **Example:**
    *   **Area Chart:** Showing total sales volume over time.
    *   **Stacked Area Chart:** Showing total website traffic over time (Y-axis), broken down by traffic source (Legend) like "Organic," "Paid," and "Direct."
*   **Use Cases:**
    *   Illustrating the change in volume over time.
    *   (Stacked) Showing the trend of a total and the contribution of its parts over time.
*   **When to Avoid:**
    *   (Stacked) When you need to clearly see the trend of individual parts that are not on the baseline. The values are cumulative, so only the bottom series is easy to interpret. Use a **Line Chart** with multiple lines for clarity on individual trends.

#### 7. Line and Stacked/Clustered Column Chart (Combo Chart)
*   **Description:** This visual combines a column chart and a line chart. It's perfect for comparing two different measures, one represented by columns and one by a line.
*   **Fields/Wells:**
    *   **Shared axis:** The categorical data (e.g., Time, Region).
    *   **Column y-axis:** The numerical value for the bars.
    *   **Line y-axis:** The numerical value for the line.
    *   **Column legend:** Breaks down the columns into stacks or clusters.
    *   **Line legend:** Creates multiple lines.
*   **Example:** Showing total sales per month as columns (Column Y-axis) and the profit margin percentage as a line (Line Y-axis) for the same period (Shared axis).
*   **Use Cases:**
    *   Visualizing two measures with different scales (e.g., count and percentage).
    *   Showing the correlation between two different metrics over the same dimension.
*   **When to Avoid:**
    *   When the two measures don't have a meaningful relationship. The visual implies a correlation, so it can be misleading if one doesn't exist.
    *   When a simple line or bar chart would tell the story more clearly.

---

### **C. Pie, Donut & Treemap Charts**
These visuals show parts of a whole.

#### 8. Pie Chart / Donut Chart
*   **Description:** Classic charts for showing proportions. A Donut chart is a Pie chart with a hole in the middle, which can be used to display a total value (using a Card visual). They represent a single series of data.
*   **Fields/Wells:**
    *   **Legend:** The categories that will form the slices.
    *   **Values:** The numerical value that determines the size of each slice.
    *   **Details:** Adds another level of breakdown within the slices (for drill-down).
*   **Example:** Showing the percentage breakdown of a company's marketing budget by channel (e.g., Social Media, TV, Print).
*   **Use Cases:**
    *   Illustrating the proportional breakdown of a total.
    *   When you have a few categories (ideally 5 or fewer) that add up to a meaningful 100%.
*   **When to Avoid:**
    *   **Strongly avoid** when you have many categories. It becomes impossible to compare slice sizes accurately. Use a **Bar Chart**.
    *   When comparing parts of a whole across different groups (e.g., market share in USA vs. Germany). Use a **100% Stacked Bar Chart**.
    *   When precise comparison is needed. Humans are bad at judging angles; we are much better at judging lengths.

#### 9. Treemap
*   **Description:** Displays hierarchical data as a set of nested rectangles. The size of each rectangle represents a value, and the color can represent a second value or category.
*   **Fields/Wells:**
    *   **Category:** The categories that form the primary rectangles.
    *   **Details:** A sub-category to nest within the main rectangles.
    *   **Values:** The numerical measure that determines the size of each rectangle.
*   **Example:** Visualizing sales by product category (Category), then sub-category (Details). The size of each box represents total sales.
*   **Use Cases:**
    *   Displaying large amounts of hierarchical data where part-to-whole relationships are key.
    *   Quickly spotting the largest contributors in a complex hierarchy.
*   **When to Avoid:**
    *   When the range of values is small, making the rectangle sizes too similar to distinguish.
    *   When a precise comparison of non-adjacent rectangles is needed. A **Bar Chart** is better for precise comparison.

---

### **D. Maps**

#### 10. Map (Bubble Map)
*   **Description:** Displays categorical and quantitative data with spatial locations. Data points are shown as bubbles on a map, where the size of the bubble represents a value.
*   **Fields/Wells:**
    *   **Location:** Geographic data (e.g., City, State, Country, Latitude/Longitude).
    *   **Legend:** Categorizes the bubbles by color.
    *   **Bubble size:** A numerical field that controls the size of each bubble.
*   **Example:** Showing the number of stores (Bubble size) in various cities (Location).
*   **Use Cases:**
    *   Visualizing values associated with specific geographic points.
*   **When to Avoid:**
    *   When you need to show data for defined regions (like states or countries). Use a **Filled Map**.

#### 11. Filled Map (Choropleth)
*   **Description:** This map uses shading, tinting, or patterns to display how a value differs across geographic areas or regions.
*   **Fields/Wells:**
    *   **Location:** Geographic regions (e.g., Country, State, County).
    *   **Legend:** Can be used to categorize the locations.
    *   **Color saturation:** The numerical value that determines the intensity of the color for each region.
*   **Example:** Showing the population density or average income (Color saturation) for each state in the USA (Location).
*   **Use Cases:**
    *   Comparing a metric across well-defined geographic regions.
    *   Displaying voting patterns, demographic data, or sales territories.
*   **When to Avoid:**
    *   When your data is for specific points (e.g., individual store locations). Use a **Map**.
    *   When regions are vastly different in size, which can be misleading (e.g., a large, sparsely populated state may dominate visually).

#### 12. Azure Map
*   **Description:** A more advanced and robust map visual with multiple data layers (bubbles, bar charts on the map, filled regions), real-time traffic, and other rich features. It combines the functionality of the basic Map and Filled Map and adds much more.
*   **Fields/Wells:** Very extensive, with specific wells for:
    *   **Location, Latitude, Longitude**
    *   **Size** (for bubbles)
    *   **Color** (for legends)
    *   **Tooltips**
    *   Separate wells for adding **Bar Chart layers**, **Filled Map layers**, etc.
*   **Example:** Showing store locations as bubbles (sized by sales), with the states they are in shaded by population density, and an optional real-time traffic overlay.
*   **Use Cases:**
    *   Complex geospatial analysis requiring multiple data layers.
    *   When you need more formatting control and features than the basic maps offer.
*   **When to Avoid:**
    *   For very simple map requirements, where a basic Map or Filled Map is sufficient and loads faster.

#### 13. Shape Map
*   **Description:** Compares regions on a map by using color, but it can use custom maps, not just standard geographical ones (e.g., a floor plan of a building, a diagram of a machine).
*   **Fields/Wells:**
    *   **Location:** A field that matches the names of the regions in your custom map file (a TopoJSON file).
    *   **Color saturation:** The numerical value that controls the color of each shape.
*   **Example:** Showing foot traffic (Color saturation) in different zones of a shopping mall (Location), using a custom map of the mall's layout.
*   **Use Cases:**
    *   Visualizing data on non-standard, custom layouts.
    *   Creating diagrams for factory floors, seating charts, or custom sales regions.
*   **When to Avoid:**
    *   When you need a standard world or country map. **Azure Map** or **Filled Map** are better.
    *   Requires a correctly formatted TopoJSON file, which can be a barrier.

---

### **E. Cards & KPIs**

#### 14. Card
*   **Description:** A simple visual for displaying a single, important number, such as total sales, a user count, or a key metric.
*   **Fields/Wells:**
    *   **Fields:** The single numerical value to be displayed.
*   **Example:** A card showing "Total Revenue: $10.5M".
*   **Use Cases:**
    *   Highlighting the most important numbers on a dashboard.
    *   Providing at-a-glance summary figures.
*   **When to Avoid:**
    *   When you need to show a trend or comparison. This visual provides no context on its own.

#### 15. Multi-row Card
*   **Description:** Displays one or more data points, one per row. It's like a very simple, key-value table.
*   **Fields/Wells:**
    *   **Fields:** Add multiple categorical and numerical fields to be displayed as rows.
*   **Example:** Displaying details for a selected customer: Name, City, Total Purchases, Last Order Date.
*   **Use Cases:**
    *   Showing several related metrics together without the overhead of a full table.
    *   Creating a profile or summary view for a selected item.
*   **When to Avoid:**
    *   When you need to compare or sort values. Use a **Table**.

#### 16. KPI (Key Performance Indicator)
*   **Description:** A visual designed specifically to show the progress towards a measurable goal. It displays a value, its target, the status (e.g., ahead/behind), and a trend line.
*   **Fields/Wells:**
    *   **Value:** The actual measure (e.g., Current Year Sales).
    *   **Trend axis:** A dimension that provides the trend, usually a date field.
    *   **Target:** The goal value (e.g., Sales Target).
*   **Example:** Showing current quarter revenue of $2.5M (Value) against a target of $2.4M (Target), with a small line chart showing the revenue trend over the past 12 months (Trend axis). The background will be green to indicate the goal has been met.
*   **Use Cases:**
    *   Executive and performance dashboards.
    *   Tracking progress against specific business targets.
*   **When to Avoid:**
    *   When you don't have a clear, defined target. A simple **Card** or **Gauge** might be better.

#### 17. Gauge
*   **Description:** A radial gauge chart that shows a single value and its progress toward a goal/KPI. It looks like a speedometer.
*   **Fields/Wells:**
    *   **Value:** The current value.
    *   **Minimum value:** The start of the gauge's arc.
    *   **Maximum value:** The end of the gauge's arc.
    *   **Target value:** A line indicating the goal.
*   **Example:** Tracking current server CPU utilization (Value) on a scale of 0% (Minimum) to 100% (Maximum), with a target threshold of 80% (Target).
*   **Use Cases:**
    *   Displaying a single metric's health or status within a range.
    *   Dashboards where a "speedometer" metaphor is intuitive (e.g., capacity, completion %).
*   **When to Avoid:**
    *   Takes up a lot of space for a single data point. A **KPI** or even a **Card** with conditional formatting can be more space-efficient.

---

### **F. Tables & Matrices**

#### 18. Table
*   **Description:** A standard grid containing related data in a logical series of rows and columns. It's the Power BI equivalent of a simple, flat table.
*   **Fields/Wells:**
    *   **Columns:** Drag and drop all the fields you want to appear as columns.
*   **Example:** A list of all sales transactions with columns for Order ID, Customer Name, Product, Quantity, and Price.
*   **Use Cases:**
    *   Displaying detailed data and precise values.
    *   When users need to look up individual records.
    *   Can include conditional formatting to highlight values (e.g., data bars, color scales).
*   **When to Avoid:**
    *   When trying to show trends or patterns. Charts are much better for visual analysis.
    *   When you need to group and aggregate data in a pivot-style view. Use a **Matrix**.

#### 19. Matrix
*   **Description:** Similar to a PivotTable in Excel. A Matrix supports a stepped layout and allows you to group data by rows and columns, with aggregated values at the intersections.
*   **Fields/Wells:**
    *   **Rows:** One or more fields to create a row hierarchy (e.g., Category, then Sub-Category).
    *   **Columns:** One or more fields to create a column hierarchy (e.g., Year, then Quarter).
    *   **Values:** The numerical measures to be aggregated.
*   **Example:** Showing sales (Values) with Product Categories as rows (Rows) and Years as columns (Columns). You can drill down into the categories to see sub-categories.
*   **Use Cases:**
    *   Displaying data across multiple dimensions (pivoting).
    *   When you have hierarchical data and want to allow users to drill up and down.
    *   Summarizing large amounts of data into a more meaningful table.
*   **When to Avoid:**
    *   For a simple, flat list of records. A **Table** is simpler.

---

### **G. AI & Advanced Visuals**

#### 20. Decomposition Tree
*   **Description:** An artificial intelligence (AI) visual that allows you to visualize data across multiple dimensions. It's an interactive tool for ad-hoc exploration and conducting root cause analysis.
*   **Fields/Wells:**
    *   **Analyze:** The primary metric you want to break down (e.g., Total Sales).
    *   **Explain by:** A list of dimensions you want to use to break down the metric (e.g., Region, Product, Salesperson).
*   **Example:** Start with "Total Sales." Click the '+' to break it down by "Region." Find the highest-selling region, then click its '+' to break it down further by "Product Category" to see what drives sales in that specific region.
*   **Use Cases:**
    *   Interactive root cause analysis.
    *   Allowing users to explore data and find insights on their own without pre-defined hierarchies.
*   **When to Avoid:**
    *   For static reporting where you want to present a specific, non-interactive view. Its strength is in exploration.

#### 21. Key Influencers
*   **Description:** Another AI visual that helps you understand the factors that drive a metric you're interested in. It analyzes your data and ranks the factors that matter.
*   **Fields/Wells:**
    *   **Analyze:** The metric you want to understand (e.g., Customer Rating). It can be categorical ("High" vs "Low") or numerical.
    *   **Explain by:** The fields that might be influencing the metric (e.g., Product Category, Country, Discount Applied).
*   **Example:** Analyzing what influences a customer's rating to be "High." The visual might show that "Discount Applied = Yes" and "Product Category = Laptops" are the top influencers.
*   **Use Cases:**
    *   Identifying the key drivers behind a business outcome.
    *   Segment analysis to see what factors are most important for a specific segment.
*   **When to Avoid:**
    *   When you have simple data with obvious relationships.
    *   Requires a sufficient amount of data with variation for the algorithm to find meaningful patterns.

#### 22. Q&A
*   **Description:** This visual allows users to ask questions about their data using natural language and get answers in the form of an automatically-generated visual.
*   **Fields/Wells:** There are no direct wells; it operates on the entire data model. You can customize it by adding synonyms and reviewing questions.
*   **Example:** A user types "total sales by country as a map" into the Q&A box, and Power BI generates a filled map visual showing the result.
*   **Use Cases:**
    *   Empowering non-technical users to explore data without learning the Power BI interface.
    *   Quickly creating visuals on the fly during a presentation.
*   **When to Avoid:**
    *   When your data model is poorly named or complex, as it can lead to confusing or incorrect results.
    *   In highly curated dashboards where you want to control exactly what the user sees.

#### 23. Smart Narrative
*   **Description:** This AI visual automatically generates a text summary of the key takeaways from your visuals and reports. It provides insights in plain language.
*   **Fields/Wells:** It has no wells. It analyzes other visuals on the page or can be customized to analyze specific data points.
*   **Example:** Next to a line chart of sales over time, the Smart Narrative might generate: "Sales saw an upward trend, increasing by 34% between Q1 and Q4. The highest point was in December at $4.2M."
*   **Use Cases:**
    *   Adding context and explanations to dashboards.
    *   Auto-generating report summaries.
    *   Ensuring accessibility for users who prefer text over charts.
*   **When to Avoid:**
    *   On highly dense dashboards where space is at a premium.
    *   If the insights it generates are too simplistic for the target audience.

---

### **H. Other Visuals**

#### 24. Slicer
*   **Description:** A slicer is a type of on-canvas visual filter. It provides an interactive way for users to filter the other visuals on a report page.
*   **Fields/Wells:**
    *   **Field:** The categorical or numerical/date field you want to use for filtering.
*   **Example:** A slicer with a list of all years in the data. When a user clicks "2023," all other visuals on the page filter to show only 2023 data. Can be a list, dropdown, or a slider for dates/numbers.
*   **Use Cases:**
    *   Essential for creating interactive and user-friendly reports.
    *   Allowing users to easily segment and explore the data.
*   **When to Avoid:**
    *   In static reports meant for printing (though still useful for the author).
    *   Over-using them can clutter the report page and confuse users. The Filters pane is an alternative for complex filtering needs.

#### 25. Waterfall Chart
*   **Description:** Shows a running total as values are added or subtracted. It's excellent for understanding how an initial value is affected by a series of positive and negative changes.
*   **Fields/Wells:**
    *   **Category:** The categories that cause the increases or decreases.
    *   **Breakdown:** Can be used to see the contributors within each category bar.
    *   **Y-axis:** The numerical value representing the change.
*   **Example:** Showing how a company's net income is calculated. Start with Gross Revenue (initial value), then show subtractions for COGS, Operating Expenses, and Taxes to arrive at the final Net Income.
*   **Use Cases:**
    *   Visualizing financial statements like profit and loss.
    *   Analyzing changes in a metric over time (e.g., starting headcount, new hires, terminations, ending headcount).
*   **When to Avoid:**
    *   When you don't have a sequence of positive and negative values that contribute to a final total.

#### 26. Funnel Chart
*   **Description:** Visualizes a linear process that has sequential, connected stages. It helps in identifying potential bottlenecks in a process.
*   **Fields/Wells:**
    *   **Category:** The stages of the process.
    *   **Values:** The number of items at each stage.
*   **Example:** A sales pipeline showing Leads -> Qualified Leads -> Proposals Sent -> Contracts Signed. The chart shows the drop-off at each stage.
*   **Use Cases:**
    *   Analyzing sales and marketing funnels.
    *   Tracking workflows and identifying process inefficiencies.
*   **When to Avoid:**
    *   When the stages are not sequential or part of a single process.

#### 27. Scatter Chart
*   **Description:** Used to show the relationship between two numerical values. A third optional numeric value can be used to control the bubble size, making it a Bubble Chart.
*   **Fields/Wells:**
    *   **X-axis:** The first numerical value.
    *   **Y-axis:** The second numerical value.
    *   **Legend:** Categorizes the dots by color.
    *   **Size:** A third numerical value to control the dot/bubble size.
    *   **Play axis:** A date/time field to animate the chart and see how the relationship evolves over time.
*   **Example:** Plotting Products with "Units Sold" (X-axis) vs. "Profit Margin" (Y-axis), with "Revenue" controlling the bubble size (Size). This can help identify high-volume, high-margin products.
*   **Use Cases:**
    *   Identifying correlations, clusters, and outliers in data.
    *   Scientific data plotting and statistical analysis.
*   **When to Avoid:**
    *   When comparing a single measure across categories. A **Bar Chart** is better.
    *   When trying to show a trend over time. A **Line Chart** is clearer.

#### 28. R script visual / Python visual
*   **Description:** These visuals allow you to run R or Python scripts directly within Power BI to create visuals that are not natively available (e.g., advanced statistical plots like violin plots, complex heatmaps).
*   **Fields/Wells:**
    *   **Values:** Add the data fields from your model that you want to be available in the script's `dataset` dataframe.
*   **Example:** Using a Python script with the `seaborn` library to create a pair plot for statistical analysis of multiple variables.
*   **Use Cases:**
    *   Creating highly customized or specialized academic/statistical visuals.
    *   Performing complex data transformations before plotting.
*   **When to Avoid:**
    *   When a native visual can do the job. Script visuals are less performant, not interactive in the same way, and require knowledge of R/Python.
    *   They are not supported in all publishing/sharing scenarios (e.g., Publish to Web).

#### 29. Power Apps visual / Power Automate visual
*   **Description:** These are integration visuals.
    *   **Power Apps:** Allows you to embed a fully functional Power App inside your Power BI report. This enables data write-back scenarios.
    *   **Power Automate:** Allows you to trigger a Power Automate flow directly from your report.
*   **Fields/Wells:**
    *   **Power Apps Data/Power Automate Data:** Add the data fields from your report that you want to pass to the app or flow.
*   **Example:**
    *   **Power Apps:** A report shows a list of inventory items. Next to it, a Power App lets the user update the stock count or place a re-order for the selected item, writing that data back to the source.
    *   **Power Automate:** A button on the report that, when clicked, triggers a flow to email the current filtered view of the report to a manager.
*   **Use Cases:**
    *   Enabling action and data write-back from within a report.
    *   Integrating your BI with business processes and workflows.
*   **When to Avoid:**
    *   For purely analytical, read-only reports. These visuals add complexity and are for taking action.