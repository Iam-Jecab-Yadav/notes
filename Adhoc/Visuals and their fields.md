
**General Field Wells Common Across Many Visuals:**

Before diving into specific chart types, let's understand some field wells that are often repeated:

- **Values:** (Often Y-Axis in charts) This is where you put the _numerical data_ you want to visualize. These are typically your **measures** (calculations like Sum, Average, Count, etc.) or numerical columns from your data. _Example: Sales Amount, Number of Orders, Website Visits._
- **Category/Axis:** (Often X-Axis in charts) This is usually where you put _categorical data_ to group or segment your values. These are typically **dimensions** (text-based columns like Product Name, Date, Region, Customer Segment). _Example: Product Category, Order Date, Region, Customer Segment._
- **Legend:** This field is used to further break down your data by another category, creating different series or groups within your visual, often differentiated by color. It adds another dimension of categorization. _Example: If your Axis is Product Category and Legend is Region, you'll see bars for each Product Category, but further divided and colored by Region._
- **Tooltips:** These are the informational boxes that appear when you hover over data points in your visual. You can add fields here to show extra details when someone interacts with the chart. You can add both measures and dimensions to tooltips. _Example: Adding 'Profit' to the tooltip of a Sales by Product Category chart allows users to see profit alongside sales when they hover._
- **Small multiples:** (Sometimes called "Trellis") This field allows you to create a series of identical visuals, each filtered by a unique value from the field you place here. This is great for comparing performance across different categories side-by-side. _Example: Creating small multiples by 'Region' for a Sales by Product Category chart will show a separate chart for each Region, making regional comparisons easy._
- **Filters:** (Visual-level, Page-level, Report-level filters - though not field _wells_ within the visual itself, they are crucial for controlling what data is displayed). You can filter any visual based on any field in your dataset.

**Specific visual types:**

**1. Bar and Column Charts** (Clustered, Stacked, 100% Stacked)

- **Use Case:** Comparing values across categories, showing trends over time (if category is time-based). Column charts are vertical bars, Bar charts are horizontal bars.
- **Field Wells:**
    - **Y-axis (Column Chart) / X-axis (Bar Chart): Values** - The numerical value you want to visualize (e.g., Sales, Units Sold). _Example: Sum of 'Sales Amount'_
    - **X-axis (Column Chart) / Y-axis (Bar Chart): Category** - The categories to compare (e.g., Product Category, Region, Date). _Example: 'Product Category'_
    - **Legend (Optional):** Further categorize the data within each bar/column (e.g., Segment by 'Region' within each 'Product Category'). _Example: 'Region'_
    - **Tooltips (Optional):** Additional details on hover (e.g., Profit, Order Count). _Example: 'Profit', 'Number of Orders'_
    - **Small multiples (Optional):** Create separate charts for each category (e.g., Small multiples by 'Year' to see yearly trends of Sales by Product Category). _Example: 'Year'_

**Example 1: Sales by Product Category**

- **Visual Type:** Clustered Column Chart
- **Y-axis (Values):** `Sum of Sales Amount` (Measure)
- **X-axis (Category):** `Product Category` (Dimension)
- **No Legend, Tooltips: `Profit`**

_This will show columns for each Product Category, with the height of each column representing the total Sales Amount for that category. Hovering will show Profit as well._

**Example 2: Sales by Product Category, Segmented by Region**

- **Visual Type:** Stacked Column Chart
- **Y-axis (Values):** `Sum of Sales Amount` (Measure)
- **X-axis (Category):** `Product Category` (Dimension)
- **Legend:** `Region` (Dimension)
- **Tooltips: `Profit`**

_This will show columns for each Product Category, but each column will be stacked and colored by Region, showing the Sales contribution of each Region within each Product Category._

**2. Line Charts** (Line, Area, Stacked Area)

- **Use Case:** Showing trends and changes over time or continuous categories. Emphasizes the flow and progression of data.
- **Field Wells:**
    - **Y-axis (Values):** The numerical value to track (e.g., Website Visits, Stock Price). _Example: 'Website Visits'_
    - **X-axis (Axis):** Typically a time-based field or continuous category (e.g., Date, Month, Year, Continuous Price Range). _Example: 'Order Date'_
    - **Legend (Optional):** Create multiple lines for different categories (e.g., Separate lines for different Product Categories showing Website Visits over time). _Example: 'Product Category'_
    - **Tooltips (Optional):** Additional details on hover (e.g., Conversion Rate, Average Order Value). _Example: 'Conversion Rate', 'Average Order Value'_
    - **Small multiples (Optional):** Separate line charts for different categories (e.g., Small multiples by 'Region' to compare regional website visit trends). _Example: 'Region'_

**Example 1: Website Visits Over Time**

- **Visual Type:** Line Chart
- **Y-axis (Values):** `Sum of Website Visits` (Measure)
- **X-axis (Axis):** `Order Date` (Date Dimension - usually set to 'Date Hierarchy' for drill-down)
- **No Legend, Tooltips: `Average Session Duration`**

_This will show a line chart with dates on the X-axis and Website Visits on the Y-axis, showing how visits change over time. Hovering will show the Average Session Duration._

**Example 2: Website Visits Over Time, by Device Type**

- **Visual Type:** Line Chart
- **Y-axis (Values):** `Sum of Website Visits` (Measure)
- **X-axis (Axis):** `Order Date` (Date Dimension)
- **Legend:** `Device Type` (Dimension)
- **Tooltips: `Average Session Duration`**

_This will show multiple lines, one for each Device Type (e.g., Desktop, Mobile, Tablet), each showing the trend of Website Visits over time for that device._

**3. Pie and Donut Charts**

- **Use Case:** Showing parts of a whole, displaying proportions and percentages. Best for a limited number of categories.
- **Field Wells:**
    - **Values:** The numerical value representing the size of each slice (e.g., Sales Amount, Count of Customers). _Example: 'Sales Amount'_
    - **Legend:** The category that defines each slice (e.g., Product Category, Region). _Example: 'Product Category'_
    - **Details (Optional):** Add extra categorical fields for further drill-down or context (less commonly used directly in pie/donut, often for interaction like drill-through).
    - **Tooltips (Optional):** Additional details (e.g., Percentage of Total, Actual Count). _Example: 'Percentage of Total Sales', 'Number of Orders'_

**Example 1: Sales Distribution by Product Category**

- **Visual Type:** Pie Chart
- **Values:** `Sum of Sales Amount` (Measure)
- **Legend:** `Product Category` (Dimension)
- **Tooltips: `Percentage of Total Sales`**

_This will show a pie chart where each slice represents a Product Category, and the size of the slice is proportional to the Sales Amount for that category. Hovering will show the percentage of total sales._

**4. Scatter Charts and Bubble Charts**

- **Use Case:** Showing the relationship between two numerical values. Bubble charts add a third numerical dimension represented by bubble size.
- **Field Wells:**
    - **X-axis (X-Axis):** First numerical value (e.g., Advertising Spend, Website Traffic). _Example: 'Advertising Spend'_
    - **Y-axis (Y-Axis):** Second numerical value (e.g., Sales Revenue, Conversion Rate). _Example: 'Sales Revenue'_
    - **Legend (Optional):** Categorize the data points by color (e.g., Segment by 'Product Category'). _Example: 'Product Category'_
    - **Size (Bubble Charts only):** A third numerical value to control the size of the bubbles (e.g., Profit, Order Quantity). _Example: 'Profit'_
    - **Details (Optional):** Add categorical fields to provide more context to each data point (e.g., 'Customer Name' to identify individual customers). _Example: 'Customer Name'_
    - **Tooltips (Optional):** All relevant values and categories.

**Example 1: Relationship between Advertising Spend and Sales Revenue**

- **Visual Type:** Scatter Chart
- **X-axis (X-Axis):** `Advertising Spend` (Measure)
- **Y-axis (Y-Axis):** `Sales Revenue` (Measure)
- **No Legend, Tooltips: `Product Name`**

_This will show a scatter plot where each point represents a product. The position of the point is determined by Advertising Spend (X-axis) and Sales Revenue (Y-axis). Hovering will show Product Name._

**Example 2: Relationship between Advertising Spend and Sales Revenue, with Profit as Bubble Size**

- **Visual Type:** Bubble Chart
- **X-axis (X-Axis):** `Advertising Spend` (Measure)
- **Y-axis (Y-Axis):** `Sales Revenue` (Measure)
- **Size:** `Profit` (Measure)
- **Legend: `Product Category`** (Dimension)
- **Tooltips: `Product Name`**

_This is similar to the scatter chart, but now the size of each bubble represents Profit. Bubbles are also colored by Product Category._

**5. Treemap**

- **Use Case:** Showing hierarchical data and proportions in a space-filling manner. Good for visualizing parts of a whole in a nested categorical structure.
- **Field Wells:**
    - **Category:** The main category that defines the top level of the hierarchy (e.g., Product Category). _Example: 'Product Category'_
    - **Values:** The numerical value that determines the size of the rectangles (e.g., Sales Amount). _Example: 'Sales Amount'_
    - **Details (Optional):** Add further levels of hierarchy or details to the rectangles (e.g., 'Sub-Category' nested within 'Product Category'). _Example: 'Sub-Category'_
    - **Tooltips (Optional):** Additional details (e.g., Percentage of Parent, Actual Count). _Example: 'Percentage of Parent Category'_

**Example 1: Sales Breakdown by Product Category and Sub-Category**

- **Visual Type:** Treemap
- **Category:** `Product Category` (Dimension)
- **Values:** `Sum of Sales Amount` (Measure)
- **Details:** `Sub-Category` (Dimension)
- **Tooltips: `Percentage of Parent Category Sales`**

_This will show a treemap where the largest rectangles represent Product Categories with the highest Sales. Within each Product Category rectangle, you'll see smaller rectangles for Sub-Categories, sized by their sales contribution within that Product Category._

**6. Map Visuals** (Map, Filled Map, ArcGIS Maps)

- **Use Case:** Visualizing geographical data, showing data distribution across locations.
- **Field Wells:**
    - **Location:** Geographical field (e.g., Country, State/Province, City, Postal Code). Power BI will try to identify the geographic role of this field. _Example: 'Country', 'State'_
    - **Latitude & Longitude (Optional but Recommended for Accuracy):** If your location names are ambiguous, using Latitude and Longitude fields will significantly improve map accuracy.
    - **Size (Optional):** A numerical value to determine the size of bubbles on the map (e.g., Sales Amount, Population). _Example: 'Sales Amount'_
    - **Color Saturation (Optional):** A numerical value to color-code regions or bubbles based on intensity (e.g., Profit Margin). _Example: 'Profit Margin'_
    - **Legend (Optional):** Categorize locations by color (e.g., Segment by 'Region'). _Example: 'Region'_
    - **Tooltips (Optional):** Relevant location details and measures.

**Example 1: Sales by Country**

- **Visual Type:** Filled Map
- **Location:** `Country` (Geographic Dimension)
- **Color Saturation:** `Sum of Sales Amount` (Measure)
- **Tooltips: `Country Name`, `Sum of Sales Amount`**

_This will show a map of the world, with countries colored according to their total Sales Amount. Countries with higher sales will have a more intense color._

**7. Gauge and KPI Charts**

- **Use Case:** Displaying progress towards a goal, showing key performance indicators at a glance.
    
- **Gauge Field Wells:**
    
    - **Values:** The current value (e.g., Current Month Sales). _Example: 'Current Month Sales'_
    - **Target value (Optional):** The goal to achieve (e.g., Sales Target). _Example: 'Sales Target'_
    - **Minimum value (Optional):** The starting point of the gauge (usually 0 or a relevant minimum).
    - **Maximum value (Optional):** The maximum scale of the gauge (often the target or a reasonable upper bound).
    - **Category (Optional):** Create multiple gauges for different categories (e.g., separate gauges for each 'Region'). _Example: 'Region'_
- **KPI Field Wells:**
    
    - **Indicator:** The value to track (e.g., Sales Amount). _Example: 'Sales Amount'_
    - **Trend axis:** Typically a time field to show trend over time (e.g., Month). _Example: 'Month'_
    - **Target goals (Optional):** The target to compare against (e.g., Sales Target). _Example: 'Sales Target'_

**Example 1: Sales Performance Gauge**

- **Visual Type:** Gauge
- **Values:** `Current Month Sales` (Measure)
- **Target Value:** `Sales Target` (Measure)
- **No Category**

_This will show a gauge indicating the current month's sales progress towards the Sales Target._

**Example 2: Sales KPI Trend**

- **Visual Type:** KPI
- **Indicator:** `Sales Amount` (Measure)
- **Trend axis:** `Month` (Date Dimension)
- **Target goals:** `Sales Target` (Measure)

_This will show a KPI indicator showing the Sales Amount for the latest month, comparing it to the Sales Target, and displaying a trend line of Sales over months._

**8. Card Visuals (Single Number Cards and Multi-Row Cards)**

- **Use Case:** Displaying key single values or summaries prominently.
- **Field Wells:**
    - **Fields:** The value(s) you want to display. You can drag measures or columns here. For single number cards, you'll typically use one measure. For multi-row cards, you can add multiple measures and categories.
    - **Category (Multi-row cards only):** Group the cards by a category.

**Example 1: Total Sales Single Number Card**

- **Visual Type:** Card
- **Fields:** `Total Sales Amount` (Measure)

_This will simply display the single number representing the Total Sales Amount._

**Example 2: Key Metrics Multi-Row Card by Region**

- **Visual Type:** Multi-row Card
- **Fields:** `Total Sales Amount`, `Average Order Value`, `Number of Orders` (Measures)
- **Category:** `Region` (Dimension)

_This will create a set of cards, one for each Region. Each card will display Total Sales, Average Order Value, and Number of Orders for that specific Region._

**9. Table and Matrix Visuals**

- **Use Case:** Displaying raw data in a tabular format, often for detailed analysis and examination of specific values. Matrix visuals are used for cross-tabulation (like pivot tables).
    
- **Table Field Wells:**
    
    - **Columns:** Fields to display as columns in the table. You can drag both dimensions and measures here.
- **Matrix Field Wells:**
    
    - **Rows:** Categories to display as rows.
    - **Columns:** Categories to display as columns (creating the cross-tabulation).
    - **Values:** Numerical values to display in the intersection of rows and columns.

**Example 1: Product Sales Table**

- **Visual Type:** Table
- **Columns:** `Product Name`, `Product Category`, `Sales Amount`, `Profit`, `Order Date` (Dimensions and Measures)

_This will create a table showing each product with its category, sales, profit, and order date._

**Example 2: Sales Matrix by Product Category and Region**

- **Visual Type:** Matrix
- **Rows:** `Product Category` (Dimension)
- **Columns:** `Region` (Dimension)
- **Values:** `Sum of Sales Amount` (Measure)

_This will create a matrix showing Product Categories as rows, Regions as columns, and the Sales Amount for each Product Category in each Region in the cells._

**10. Slicer**

- **Use Case:** Filtering other visuals on the page interactively.
- **Field Wells:**
    - **Field:** The field you want to use for filtering. You can drag dimensions or sometimes measures (for numeric range slicers) here.

**Example 1: Product Category Slicer**

- **Visual Type:** Slicer
- **Field:** `Product Category` (Dimension)

_This will create a slicer with a list of Product Categories. Selecting a category in the slicer will filter all other visuals on the page to show data only for that selected Product Category._

**Tips for Remembering Field Wells:**

- **Think about the purpose of the visual:** What story are you trying to tell? What kind of data is best suited for this visual type?
- **Start with the basics:** Almost every chart needs a _category_ (to group by) and a _value_ (to measure). That's your X and Y axis in many cases.
- **Visualize in your head:** Imagine the chart being drawn. What would be on the horizontal axis? Vertical axis? What would different colors represent?
- **Experiment:** The best way to learn is to try! Drag and drop different fields into the field wells and see what happens. Power BI is very forgiving. You can always undo.
- **Use Power BI's Help Tips:** Hover over the field wells in Power BI. It often provides tooltips explaining what kind of data goes there.
- **Refer to documentation:** Microsoft's Power BI documentation is excellent. Search for "Power BI Visualizations" to find detailed articles on each visual type.
- **Practice, Practice, Practice:** The more you build reports, the more intuitive this will become.

Don't get discouraged if you don't remember everything at once. Keep practicing, refer back to this list or documentation, and you'll master the field wells in Power BI visuals in no time!