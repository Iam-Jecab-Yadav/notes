
### What is Power BI?
**Business Intelligence Tool:** Power BI is a suite of tools from Microsoft designed for **data visualization and business intelligence**. It helps you analyze data and share insights.
**Self-Service BI:** It's built to be user-friendly, allowing business users (not just IT) to create reports and dashboards without extensive technical skills.
**Connects to Data Sources:** Power BI can pull data from a wide variety of sources (databases, spreadsheets, cloud services, web APIs, etc.).
**Transforms and Models Data:** You can clean, shape, and model your data within Power BI to make it ready for analysis and visualization.
**Visualizations and Reports:** Power BI allows you to create interactive charts, graphs, maps, and reports to understand your data visually.
**Dashboards:** You can consolidate key visualizations and reports into dashboards for a high-level overview of your data.
**Sharing and Collaboration:** Power BI facilitates sharing reports and dashboards with others and collaborating on data analysis.

### Workflow
1. **Get Data:** Connect to your data sources using Power BI Desktop.
2. **Transform Data (Power Query):** Clean, shape, and transform your data using Power Query Editor.
3. **Model Data:** Create relationships between tables and add calculations (DAX measures and calculated columns).
4. **Visualize Data (Reports):** Design reports with interactive visualizations to analyze and present your data.
5. **Publish to Power BI Service:** Publish your `.pbix` report file to the Power BI Service.
6. **Create Dashboards (Power BI Service):** Pin visualizations from reports to create dashboards.
7. **Share and Collaborate (Power BI Service):** Share reports and dashboards with colleagues and collaborate within workspaces.
8. **Consume Reports and Dashboards:** View and interact with reports and dashboards in the Power BI Service and mobile apps.
9. **Schedule Data Refresh (Power BI Service):** Set up data refresh schedules to keep your reports up-to-date.


![[Assets/486c1247b737fb500ed62ad85da4506f_MD5.jpeg]]


### UI Layout
1. **The Ribbon (Top Bar)** - Provides access to all major commands and features organized into tabs. It's similar to the ribbon in Microsoft Office applications.
	1. **File:** Managing files (New, Open, Save, Save As, Import, Export, Options and settings).
	2. **Home:** Common tasks like Get Data, Refresh, New Visual, Text Box, Buttons, Shapes, Insert (Image), Publish.
	3. **Insert:** Specifically for adding pages, visuals, text boxes, buttons, shapes, images.
	4. **Modeling:** Tools for creating and managing data models, calculations (New Measure, New Column, New Table), Relationships, Manage Roles.
	5. **View:** Customizing the Power BI Desktop view (Page View, Show Panes, Themes, Gridlines, Snap to grid, Lock objects, Performance analyzer, Sync slicers, Mobile layout).
	6. **Help:** Access to documentation, learning resources, support, samples, and community forums.
	7. **Format (Contextual):** Appears dynamically when you select a visual, page, or shape. Provides formatting options specific to the selected element. _This is a contextual tab and won't always be visible._
	8. **Visual Tools (Contextual):** Appears dynamically when you select a visual. Provides specific tools for interacting with and analyzing the selected visual. _This is a contextual tab and won't always be visible._
2. **Panes** - Panes are dock able windows on the left and right sides of the canvas that provide access to different functionalities.
	1. **Left Panes**
		1. **Report View (Default):** The canvas where you build your visualizations and lay out your report pages. This is the central area you'll spend most of your time in.
		2. **Data View:** Displays the data tables in your model. You can view data, apply filters, and understand the data structure.
		3. **Model View:** Provides a visual representation of your data model, showing tables and their relationships. You can manage relationships, create new ones, and understand the model's structure.
	2. **Right Panes (Typically docked on the right side)**
		1. **Visualizations Pane:** Contains the gallery of available visual types (charts, tables, maps, etc.). You drag visuals from here onto the Report View canvas to start building.
		2. **Fields Pane:** Lists the tables and columns from your data model. You drag fields from here onto visuals to populate them with data.
		3. **Filters Pane:** Allows you to apply filters to the entire report page, individual visuals, or at the visual-level filters. You can control what data is displayed in your report.
		4. **Format Pane (Contextual):** Appears when you select a visual or other report element. Provides granular formatting options to customize the appearance of your visuals (colors, fonts, titles, axes, etc.).
3. **Report Canvas (Center)**- This is the **design surface** where you build your reports. You drag visuals from the Visualizations pane onto this canvas and arrange them as you want your report to look.
	1. **Pages Tab** - Allows you to manage report pages. You can add new pages (using the "+" icon), rename pages, reorder pages, and navigate between pages. Reports can be multi-page documents.
4. **Status Bar (Bottom)** - Displays status messages, progress indicators, and quick access to certain features. You might see messages about data loading, calculations, etc., here.






### Visualization
#### Types of Visualization
1. **Basic Charts (Comparison & Distribution):**
	1. **Bar Chart & Column Chart:** These are fundamental for comparing values across different categories.
		1. **Bar Chart:** Horizontal bars, often used for comparing categories with longer labels or when you have many categories.
		2. **Column Chart:** Vertical columns, also for comparing categories, commonly used for time series data or when categories are shorter.
		3. **Stacked Bar/Column Chart:** Show parts of a whole within each category, allowing comparison of both total values and contributions of subcategories.
		4. **100% Stacked Bar/Column Chart:** Emphasize the percentage contribution of subcategories to the whole, rather than absolute values.
	2. **Pie Chart & Donut Chart:** Show parts of a whole, representing proportions of different categories to the total.
		1. **Pie Chart:** A circular chart divided into slices, each representing a proportion. Best for a small number of categories.
		2. **Donut Chart:** Similar to a pie chart but with a hole in the center. Can be visually appealing but functionally very similar to pie charts. Sometimes the center is used to display a total.
	3. **Line Chart & Area Chart:** Used to display trends and changes over time or across a continuous scale.
		1. **Line Chart:** Connects data points with lines, showing trends and patterns in data over time or a continuous variable.
		2. **Area Chart:** Similar to a line chart, but the area below the line is filled in. Emphasizes the volume or magnitude of the trend and can be useful for showing cumulative totals or contributions.
		3. **Stacked Area Chart:** Shows the contribution of different categories to the overall trend over time, similar to stacked bar/column charts but for time series.
	4. **Scatter Chart:** Displays the relationship between two numerical variables. Helpful for identifying correlations, clusters, and outliers.
		1. **Bubble Chart:** An extension of the scatter chart where the size of the bubbles represents a third numerical variable.
	5. **Treemap:** Displays hierarchical data as nested rectangles. The size of each rectangle represents the value of the corresponding category. Good for showing proportions within a hierarchy and identifying dominant categories.
	6. **Funnel Chart:** Visualizes a linear process that has sequential connected stages, such as a sales process. Shows values decreasing progressively from one stage to the next.
	7. **Waterfall Chart:** Shows the cumulative effect of sequential positive and negative values. Useful for understanding the starting point, increases, decreases, and the final result.
2. **Geographic Visuals (Maps):**
	1. **Map (Bubble Map):** Displays data on a geographic map using bubbles. The size of the bubble represents the magnitude of a data point at a specific location.
	2. **Filled Map (Choropleth Map):** Colors geographical areas (like countries or states) based on a data value. Different shades represent different data ranges.
	3. **Shape Map:** Allows you to use custom geographic boundaries (beyond standard maps) and color them based on data values.
3. **Key Performance Indicator (KPI) & Single Number Visuals:**
	1. **Card (Number Card):** Displays a single, important numerical value, often with a label. Great for highlighting key metrics.
	2. **Multi-Row Card:** Displays one or more data points, one per row. Useful when you want to show several related key metrics.
	3. **KPI (Key Performance Indicator):** Visually communicates progress toward a measurable goal. Shows the current value, goal value, and status (variance).
	4. **Gauge Chart:** Displays a single value relative to a minimum and maximum range on a circular gauge. Shows performance within a range and often compared to a target.
4. **Table and Matrix:**
	1. **Table:** Displays data in a tabular format with rows and columns. Good for showing detailed data and allowing users to sort and filter.
	2. **Matrix:** Similar to a table, but allows for more complex data summarization across two dimensions (rows and columns). Supports drill-down capabilities to explore hierarchical data.
5. **Combo Charts:**
	1. **Combo Chart (Line and Clustered Column Chart, Line and Stacked Column Chart):** Combines two chart types (usually a line chart and a column chart) in a single visual. Useful for showing relationships between different data series with different scales or types.
6. **R and Python Visuals (Requires Scripting):**
	1. **R Visuals:** Allows you to create visuals using R scripts directly in Power BI, leveraging the vast library of R visualization packages.
	2. **Python Visuals:** Similarly, enables the use of Python scripts and libraries (like Matplotlib, Seaborn) for creating custom visuals.
7. **Custom Visuals (From AppSource or Developed In-House):**
	1. **Power BI AppSource:** A marketplace for pre-built custom visuals developed by Microsoft and the community. Expands the visual options beyond the built-in visuals.
	2. **Custom Visual Development:** You can develop your own custom visuals using the Power BI visuals SDK to create highly specific or branded visualizations.

[[Visuals and their fields]]


######  When to use given chart
- **Comparison Charts (Comparing Values Across Categories or Time)**
	- **Column Chart (Vertical Bar Chart) -** Displays categorical data with vertical bars. Compares values across different categories.
		- **When to Use:**
			- **Comparing values of distinct categories:** Sales by product category, website visits by source, survey responses by demographic.
			- **Showing rankings or order:** Top-selling products, countries with highest GDP.
			- When you have relatively few categories (5-7 or less for optimal readability).
		- **When to Avoid**
			- **Too many categories:** Becomes cluttered and difficult to read. Use a bar chart or other alternatives.
			- Showing trends over continuous time (use a line chart instead).
	- **Bar Chart (Horizontal Bar Chart):** Similar to a column chart but with horizontal bars. Excellent for category labels that are long or when you have many categories.
		- **When to Use**
			- When category labels are long and might get truncated in a column chart.
			- When you have a moderate number of categories (more than column chart is ideal for, but still manageable).
			- Ranking and comparing values, especially when readability of category labels is paramount.
		- **When to Avoid**
			- Showing trends over time.
			- Too many categories (becomes less effective if you have dozens). Consider a table or alternative summary visual.
	- **Line Chart:** Displays trends and changes in data over a continuous period, usually time. Connects data points with lines.
		- **When to Use:**
			- **Showing trends over time:** Sales trends over months, website traffic over days, stock prices over years.
			- **Comparing trends of multiple series over time:** Comparing sales of different product lines over the last quarter.
			- Highlighting patterns and fluctuations in data over a continuous variable.
		- **When to Avoid**
			- Comparing distinct categories without a time component (use column or bar chart).
			- Categorical data that isn't sequential.
	- **Area Chart:** Similar to a line chart, but the area below the line is filled with color. Emphasizes the magnitude of change over time, and can be useful for showing cumulative totals.
		- **When to Use**
			- Showing trends over time while emphasizing volume or magnitude.
			- Illustrating cumulative totals over time (especially stacked area charts).
			- Comparing trends of multiple series and highlighting the total magnitude of each series (stacked area chart).
		- **When to Avoid**
			- When precise value comparisons are crucial (lines are better for precise readings).
			- Too many series in a stacked area chart can become cluttered and difficult to interpret.
	- **Combo Chart (Column and Line Chart):** Combines columns and lines within a single chart, often used to visualize two different but related datasets with different scales.
		- **When to Use** 
			- **Visualizing two different types of data on the same chart with different scales.** For example, showing sales revenue (columns) and profit margin (line) over time.
			- Highlighting relationships between two different metrics.
			- When you want to show both categorical comparisons and trends over time within one visual.
		- **When to Avoid**
			- When the two datasets are unrelated and create confusion rather than clarity.
			- **If the scales of the two datasets are drastically different, it might distort visual perception.** Ensure scales are chosen thoughtfully.
- **Part-to-Whole Charts (Showing Proportions and Composition)**
	- **Pie Chart:** A circular chart divided into slices, where each slice represents a proportion of the whole.
		- **When to Use:**
			- **Showing the parts of a whole when you have a _small_ number of categories (ideally 3-5).** Market share by company, budget allocation by department, customer distribution by segment.
			- Emphasizing the proportion of each category to the total.
			- For audiences who are less data-savvy, as pie charts are easily recognizable.
		- **When to Avoid**
			- **Too many categories:** Pie charts become very difficult to read with many slices. Consider a bar chart or tree map.
			- **Comparing exact sizes of slices:** It's hard for the human eye to accurately compare areas in a pie chart. Bar charts are better for precise comparisons.
			- When you need to show trends over time.
			- When you have categories with very similar proportions, making it hard to distinguish slices.
	- **Donut Chart:** Similar to a pie chart, but with a hole in the center. Can be visually more appealing and allows space to display summary information in the center.
		- **When to Use**
			- Same use cases as pie charts, but can be considered slightly more modern visually.
			- When you want to display a total or summary statistic in the center of the chart.
		- **When to Avoid**
			- Same limitations as pie charts (too many categories, difficult comparisons, etc.).
	- **Tree Map:** Displays hierarchical data as nested rectangles. The size of each rectangle represents the proportion of the whole.
		- **When to Use** 
			- **Showing hierarchical data as proportions of a whole.** Sales by region and then by product category within each region.
			- When you have a larger number of categories than ideal for pie or donut charts.
			- When you need to quickly identify the largest and smallest segments within a hierarchy.
			- Effective for showing relative size differences across categories within a hierarchy.
		- **When to Avoid**
			- **Comparing precise proportions:** Difficult to visually judge exact size differences between rectangles, especially for similar sizes.
			- Negative values (tree maps are designed for positive proportions).
	- **Funnel Chart** Visualizes a process that has stages, typically showing a decreasing flow from stage to stage, often used for sales processes or pipeline analysis.
		- **When to Use**
			- Visualizing a process with sequential stages (like a sales funnel, application process, etc.).
			- Showing the decrease in values at each stage of a process.
			- Identifying drop-off rates or bottlenecks in a process.
			- Presenting conversion rates at each stage.
		- **When to Avoid**
			- Data that is not sequential or doesn't represent a process with stages.
			- When the data doesn't naturally narrow down at each stage (funnel shape expected).
- **Distribution and Relationship Charts (Understanding Data Spread, Correlations, and Relationships)**
	- **Scatter Chart -**  Plots data points on a two-dimensional graph using two numerical axes (X and Y). Shows the relationship or correlation between two variables.
		- **When to Use:**
			- **Exploring the relationship between two numerical variables:** Relationship between advertising spend and sales revenue, height and weight, temperature and ice cream sales.
			- Identifying correlations (positive, negative, or no correlation).
			- Detecting clusters, outliers, and patterns in data distribution.
		- **When to Avoid**
			- Categorical data (use bar or column charts for comparing categories).
			- When you are primarily interested in comparing values across categories rather than exploring relationships between variables.
	- **Bubble Chart** Similar to a scatter chart, but adds a third dimension by using the size of the bubbles to represent a third numerical variable.
		- **When to Use**
			- Visualizing three numerical variables simultaneously.
			- Comparing data points based on three different metrics.
			- Highlighting data points that are significant in three dimensions.
			- Effective for presenting market analysis, portfolio performance, etc., where you need to see size, position, and category all at once.
		- **When to Avoid:**
			- **Too many bubbles can make the chart cluttered and difficult to read.**
			- When comparing precise bubble sizes is crucial (it can be challenging to visually judge area differences accurately).
			- If the third variable is not meaningful or doesn't add valuable insight.
	- **Heatmap -** Uses color to represent the magnitude of a variable across two categories. Often displayed in a matrix format.
		- **When to Use**
			- **Visualizing the magnitude of a value for the intersection of two categorical variables.** For example, website traffic by day of week and hour of day, sales performance by region and product category.
			- Identifying patterns, concentrations, and outliers in a matrix of data.
			- Showing correlations or relationships between two categorical variables through color intensity.
		- **When to Avoid**
			- When you have more than two categorical dimensions (becomes too complex).
			- If precise numerical values are needed (heatmaps are more for visual pattern recognition).
	- **Histogram -** Displays the distribution of numerical data. It groups data into bins (intervals) and shows the frequency (count) of data points falling into each bin using columns.
		- **When to Use**
			- Understanding the distribution of a single numerical variable.
			- Identifying the frequency of values within different ranges.
			- Checking for normality or skewness in data distribution
			- Analyzing the shape of the data (e.g., bell-shaped, uniform, skewed).
		- **When to Avoid**
			- Categorical data (use bar or column charts for categories).
			- When you need to compare different datasets or groups (consider using overlaid histograms or other comparative distribution plots).
- **Geographic Charts (Spatial Data Visualization)** 
	- **Map (Filled Map, Shape Map, Azure Maps)** Visualizes data geographically on a map. Uses color to represent values associated with geographic regions (countries, states, cities, etc.).
		- **When to Use:**
			- **Visualizing geographically distributed data.** Sales by region, customer locations, population density, election results by state.
			- Highlighting geographic patterns and variations in data.
			- When location is a key dimension of your data and insights.
		- **When to Avoid**
			- Data that is not geographically relevant.
			- Overcrowding with too many data points on a map, making it cluttered.
			- When geographic boundaries are not meaningful for the insights you want to convey.
- **Table and Matrix Charts (Detailed Data Presentation)**
	- **Table** Presents data in a tabular format with rows and columns. Provides precise values and detailed data.
		- **When to Use:**
			- When you need to present raw data in a detailed and precise format.
			- For showing a large amount of data in a structured way.
			- When users need to look up specific values and compare them precisely.
			- As a supporting visual to provide detail behind summary charts.
		- **When to Avoid**
			- When you want to highlight trends or patterns visually (charts are better for this).
			- For very large datasets, tables can become overwhelming. Consider summarization or filtering.
	- **Matrix** A more advanced table that can display data in a pivot table format, allowing you to summarize and drill down into data based on multiple dimensions (rows, columns, and values).
		- **When to Use:**
			- Analyzing and summarizing data across multiple categories.
			- Drilling down into hierarchical data structures.
			- Performing cross-tabulations and showing aggregated values.
			- When you need to explore data from different perspectives and levels of detail.
		- **When to Avoid**
			- For simple data presentation where a table is sufficient.
			- If the matrix becomes too complex and hard to interpret due to too many dimensions.
- **Card and KPI Visuals (Highlighting Key Metrics)**
	- **Card** Displays a single, important numerical value or text prominently. Used to highlight key performance indicators (KPIs) or summary statistics.
		- **When to Use:**
			- **Highlighting a single, crucial metric.** Total sales revenue, website conversion rate, customer satisfaction score.
			- Drawing attention to important summary statistics at the top of a dashboard.
			- Providing quick insights and at-a-glance information.
		- **When to Avoid**
			- Showing relationships or comparisons (use other chart types).
			- Presenting detailed data.
	- **KPI (Key Performance Indicator) Visual:** Specifically designed to track progress towards a goal. Typically shows a value, a target, and a status indicator (trend and if the target is being met).
		- **When to Use:**
			- **Tracking progress against a defined target or goal.** Sales target achievement, website traffic goals, project completion rate targets.
			- Monitoring performance and identifying if KPIs are on track, lagging, or exceeding targets.
			- Adding context and meaning to single metrics by showing target and status.
		- **When to Avoid**
			- When there's no defined target or goal associated with the metric.
			- If you just want to display a simple value without the target and status context (use a Card).
	- **Gauge Chart** Displays a single value in a speedometer-like format. Shows the current value in relation to a scale, often with minimum, maximum, and target values.
		- **When to Use:**
			- Showing progress towards a goal or target on a scale.
			- Visualizing performance within a defined range (e.g., temperature, progress percentage).
			- Highlighting whether a value is within acceptable limits or thresholds.
		- **When to Avoid**
			- Comparing multiple categories (use bar or column charts).
			- Showing trends over time (use line or area charts).
			- Can sometimes be less precise and space-efficient compared to other progress indicators like progress bars or simple numbers with trend arrows.
- AI-Powered Visuals (Intelligent Insights)
	- Decomposition Tree
	- Key Influencers
	- Q&A Visual
	- Smart Narrative
- Paginated Report Visuals (Specific to Power BI Report Builder and Paginated Reports)
	- Tablelix
	- Charts
	- Gauges
	- Maps
	- Sparklines and Data Bars
	- Indicators


#### Formatting visuals

1. **General Formatting Options** - These are high-level settings that apply broadly to the visual.
	1. **Change Visual Type -**  Allows you to quickly switch to a different type of visual without losing your data setup (e.g., change a bar chart to a column chart). 
	2. **General -** 
		1. **Position -** 
			1. **X Position:** Numerical input to precisely control the horizontal placement of the visual on the canvas.
			2. **Y Position:** Numerical input to precisely control the vertical placement.
			3. **Width:** Numerical input to set the exact width of the visual.
			4. **Height:** Numerical input to set the exact height of the visual.
		2. **Size:** (Often duplicates Width/Height from Position section)
			1. **Width:** Adjust visual width.
			2. **Height:** Adjust visual height.
		3. **Padding -**
			1. **Inner Padding:** Controls the space between the visual's border and its internal elements (title, axes, plot area, etc.). Increasing padding can create more visual breathing room.
		4. **Background:**
			1. **Background:** Toggle to enable/disable the background.
			2. **Color:** Choose a background color using the color picker.
			3. **Transparency:** Adjust the transparency of the background (0% is opaque, 100% is fully transparent).
		5. **Border -**
			1. **Border:** Toggle to enable/disable a border around the visual.
			2. **Color:** Choose the border color.
			3. **Transparency:** Adjust border transparency.
			4. **Rounded corners:** Control the roundness of the border corners (in pixels).
		6. **Shadow -**
			1. **Shadow:** Toggle to enable/disable a shadow effect.
			2. **Type:** Choose from different shadow styles (e.g., Offset bottom right, Inside).
			3. **Color:** Select the shadow color.
			4. **Transparency:** Control shadow transparency.
			5. **Outer Offset:** Adjust the distance and angle of the shadow from the visual (Direction, Distance).
			6. **Inner Offset:** (For "Inside" shadow type) Adjust the inner shadow properties.
		7. **Title -**
			1. **Title:** Toggle to enable/disable the visual title.
			2. **Title text:** Enter the text for the title. You can use DAX measures here for dynamic titles!
			3. **Font family:** Select the font for the title text.
			4. **Font size:** Adjust the title font size (in points).
			5. **Font color:** Choose the title text color.
			6. **Text alignment:** Align the title text (Left, Center, Right).
			7. **Background color:** Set a background color for the title area.
			8. **Transparency:** Control title background transparency.
			9. **Subtitle:** Toggle to add a subtitle below the main title.
				1. **Subtitle text:** Enter subtitle text. (Similar formatting options as the main title for font, size, color, alignment).
		8. **Header icons -**
			1. **Header icons:** Toggle to enable/disable header icons.
			2. **Background**
				1. **Background:** Toggle header icon background.
				2. **Color:** Header icon background color.
				3. **Transparency:** Header icon background transparency.
			3. **Border:**
				1. **Border:** Toggle header icon border.
				2. **Color:** Header icon border color.
			4. **Icons**:
				1. **Color:** Color of the icons themselves.
				2. **Hover color:** Color of the icons when you hover over them.
			5. **Transparency:** Overall transparency of the header icons area.
			6. **Padding:** Space around the icons within the header.
		9. **Tooltips**
			1. **Tooltips:** Toggle to enable/disable tooltips on data points.
			2. **Report page:** Allows using a custom report page as a tooltip (powerful for rich tooltips!).
			3. **Default tooltips:** If not using report page tooltips, you customize default tooltips
				1. **Color:** Tooltip background color.
				2. **Transparency:** Tooltip background transparency.
				3. **Text color:** Color of text within the tooltip.
				4. **Font family:** Font for tooltip text.
				5. **Font size:** Tooltip text font size.
		10. **Alt text:** (Accessibility feature)
			1. **Alt text:** Provide a description of the visual for screen readers, improving accessibility for users with visual impairments.
		11. **Lock aspect ratio:** (Often for image visuals)
			1. **Lock aspect ratio:** Maintain the original proportions of the visual when resizing.
		12. **Maintain layer order:** (For visuals that overlap)
			1. **Maintain layer order:** Controls the stacking order of visuals.
	3. **Visual-Specific Formatting Options -** These categories are tailored to the _specific type_ of visual you've chosen (e.g., Bar Chart, Line Chart, Pie Chart, Matrix, Map, etc.). They control elements unique to each visual type.
		1. **X-Axis:** (For visuals with an X-axis like bar charts, line charts, scatter plots)
			1. **X-Axis:** Toggle to enable/disable the X-axis.
			2. **Axis title:**
				1. **Title:** Toggle to enable/disable the X-axis title.
				2. **Title text:** Customize the X-axis title.
				3. **Font color, Font size, Font family, Text alignment:** Formatting for the title text (similar to visual title).
			3. **Values:** (Formatting for the axis labels/values)
				1. **Font color, Font size, Font family:** Text formatting for axis labels.
				2. **Display units:** Choose how values are displayed (e.g., Thousands, Millions, Auto).
				3. **Value decimal places:** Control the number of decimal places shown in axis labels.
				4. **Text angle:** Rotate axis labels for better readability if they are long and overlapping.
				5. **Position:** Place the axis labels "Next to axis" or "Far from axis".
				6. **Show title only when space allows:** Option to hide the axis title if there isn't enough space to display it.
			4. **Gridlines**:
				1. **Gridlines:** Toggle to enable/disable vertical gridlines (if applicable to the visual type).
				2. **Color, Stroke width, Line style:** Customize gridline appearance.
				3. **Stroke dash type:** Choose dash pattern for gridlines (Solid, Dashed, Dotted, etc.).
			5. **Range**
				1. **Start:** Manually set the starting value of the X-axis.
				2. **End:** Manually set the ending value of the X-axis.
				3. **Axis type:** Choose between "Categorical" (for discrete categories) or "Continuous" (for numerical ranges or dates).
				4. **Scale type:** Linear or Logarithmic scale.
				5. **Invert range:** Reverse the direction of the X-axis.
		2. **Y-Axis:** (For visuals with a Y-axis)
			1. **Y-Axis:** Toggle to enable/disable the Y-axis.
			2. **Axis title:** (Similar options to X-axis title for customization)
			3. **Values:** (Similar options to X-axis values for formatting)
			4. **Gridlines:** (Similar options to X-axis gridlines, but controls _horizontal_ gridlines)
			5. **Range:** (Similar options to X-axis range for setting start, end, scale type, etc.)
			6. **Secondary Y-axis:** (For visuals that support a secondary Y-axis – often used for combo charts or visuals with different scales) – Options similar to the primary Y-axis are available for the secondary axis.
			7. **Show secondary:** Toggle to show/hide the secondary Y-axis.
			8. **Axis title, Values, Gridlines, Range:** Formatting options for the secondary Y-axis.
		3. **Legend**:
			1. **Legend:** Toggle to enable/disable the legend.
			2. **Position:** Choose where the legend appears (Top, Bottom, Left, Right, Top center, Bottom center, Left center, Right center).
			3. **Legend title**
				1. **Title:** Toggle to enable/disable the legend title.
				2. **Title text:** Customize the legend title.
				3. **Font color, Font size, Font family, Text alignment:** Formatting for the legend title.
			4. **Text:** (Formatting for the legend labels)
				1. **Font color, Font size, Font family:** Text formatting for legend labels.
			5. **Markers**
				1. **Shape:** Choose the shape of the markers in the legend (e.g., Circle, Square).
				2. **Stroke color, Stroke width:** Customize marker border.
				3. **Marker size:** Adjust the size of the markers.
				4. **Transparency:** Control marker transparency.
				5. **Show marker:** Toggle marker visibility in the legend.
			6. **Reverse order:** Display legend items in reverse order.
		4. **Data labels:** (For showing values directly on data points)
			1. **Data labels:** Toggle to enable/disable data labels.
			2. **Options**:
				1. **Position:** Where data labels appear relative to the data point (Auto, Inside end, Outside end, Inside center, etc. – options vary by visual type).
				2. **Orientation:** Horizontal or Vertical data labels.
				3. **Show background:** Add a background behind the data labels
					1. **Background color, Transparency:** Customize data label background.
				4. **Border:** Add a border around data labels
					1. **Border color:** Customize data label border.
				5. **Values:** (Formatting for data label text)
					1. **Font color, Font size, Font family:** Text formatting for data labels.
					2. **Display units, Value decimal places:** Control how data label values are formatted.
					3. **Text wrap:** Wrap long data labels to multiple lines.
				6. **Series labels:** (For visuals with series like line charts or clustered bar charts, you can label the series directly)
					1. **Series labels:** Toggle series labels.
					2. **Position, Orientation, Show background, Border:** Options similar to data label options.
					3. **Values:** Font, display units, etc. formatting similar to data labels values.
		5. **Shapes:** (Controls the visual representation of data points – bars, columns, lines, markers, slices, etc.)
			1. **Color**
				1. **Default series color:** Set a base color for all data series.
				2. **Show all:** (Often present) - Enables customizing colors for individual categories or series. Click "Show all" and you'll see options to set colors for specific categories/series.
				3. **Conditional formatting:** (Often accessed here or through "Data colors") Apply rules to dynamically change data point colors based on data values.
			2. **Customize series:** (Sometimes named differently depending on the visual) – This section allows you to further customize shapes _per series or category_. Options might include:
				1. **Show bar labels:** (For bar charts - adds labels at the end of bars).
				2. **Outline:** Add outlines to shapes
					1. **Outline color, Outline width:** Customize shape outlines.
				3. **Stroke width:** Adjust the thickness of lines in line charts.
				4. **Show marker:** (Line and Scatter charts) Toggle markers on/off.
				5. **Marker shape, Marker size, Marker color:** Customize markers.
				6. **Data colors:** (Can sometimes be within "Shapes" or a separate "Data colors" category) – This is often where you can set specific colors for each category or series. You might see a list of categories and color pickers to assign colors.
		6. **Plot area background:**
			1. **Plot area background:** Add a background color or image _specifically to the plot area_ (the area where the data is visualized, excluding axes, titles, legend, etc.).
			2. **Color:** Plot area background color.
			3. **Transparency:** Plot area background transparency.
			4. **Image:** Add an image as the plot area background.
				1. **Browse:** Upload an image file.
				2. **Transparency, Fit type:** Control how the image is displayed within the plot area.
		7. **Data colors:** (Sometimes a top-level category, sometimes within "Shapes")
			1. **Default series color:** Base color for all series if no custom colors are set.
			2. **Conditional formatting:** (If not in "Shapes") – Apply data-driven rules to change data point colors.
			3. **Color by categories/series:** A list of your categories or series, with color pickers next to each, allowing you to assign specific colors.
		8. **Slicer settings:** (For slicer visuals)
			1. **Header:** (Slicer title)
			2. **Items:** (Formatting for the slicer values/buttons)
			3. **Slicer header:** (Formatting for the slicer's "Category" label)
		9. **Card:** (For card visuals)
			1. **Value:** (Formatting for the main value displayed)
			2. **Category label:** (Formatting for the label below the value)
			3. **Callout value:** (Another way to refer to the main value formatting)
		10. **Map visual specific options:** (For Map and Filled Map visuals)
			1. **Map styles:** Choose base map styles (Road, Aerial, Dark, Light, Grayscale).
			2. **Bubbles:** (For bubble maps) - Control bubble size, color.
			3. **Category labels:** (For maps with categories) - Formatting for category labels.
			4. **Data colors:** Color settings for map regions or bubbles.
			5. **Zoom controls:** Enable/disable zoom buttons on the map.
			6. **Search:** Enable/disable map search functionality.
		11. **Gauge visual specific options:** (For Gauge visuals)
			1. **Gauge axis:** Range settings, colors for minimum, maximum, target, etc.
			2. **Data colors:** Colors for the fill, target, etc.
			3. **Target labels:** Formatting for target value labels.
			4. **Value labels:** Formatting for current value labels.
		12. **Table/Matrix visual specific options:**
			1. **Style presets:** Quick styles for the entire table/matrix (e.g., "Minimal," "Bold headers," "Alternating rows").
			2. **Grid:** Options for vertical and horizontal gridlines, colors, thickness.
			3. **Column headers:** Formatting for column header text, background.
			4. **Row headers:** Formatting for row header text, background.
			5. **Values:** Formatting for the data values within the table/matrix.
			6. **Totals:** Formatting for total rows/columns.
			7. **Specific column formatting:** You can often format individual columns differently (e.g., apply data bars, conditional formatting to a specific column).
			8. **Cell elements:** Data bars, icons, web URLs – add visual elements within table cells based on data.
		13. **Treemap specific options:**
			1. **Data colors:** Colors for treemap rectangles.
			2. **Category labels:** Formatting for labels on treemap rectangles.
			3. **Detail labels:** Formatting for value labels on treemap rectangles.
		14. **Funnel chart specific options:**
			1. **Data colors:** Colors for funnel segments.
			2. **Category labels:** Formatting for segment labels.
			3. **Convert labels:** Formatting for converted value labels.
			4. **Percent labels:** Formatting for percentage labels.
		15. **Waterfall chart specific options:**
			1. **Data colors:** Colors for increase, decrease, and total columns.
			2. **Category labels:** Formatting for column labels.
			3. **Value labels:** Formatting for value labels on columns.
			4. **Y-Axis:** (Standard Y-axis options).
			5. **Category axis:** (Specific options for the category axis in a waterfall chart if applicable).
	4. **Analytics Pane Formatting (Sometimes integrated or separate)**	
		1. **Constant line:** Add a fixed horizontal or vertical line at a specific value. Customize color, style, data label.
		2. **Min/Max lines:** Dynamically show lines at the minimum and maximum values in your data. Customize appearance.
		3. **Average line:** Show the average value as a line. Customize appearance.
		4. **Median line:** Show the median value as a line. Customize appearance.
		5. **Percentile lines:** Add lines at specific percentile values.
		6. **Forecast:** (For time series visuals) Add a predictive forecast to your line chart. Customize forecast length, confidence interval, appearance.
		7. **Error bars:** (Often in scatter charts and line charts) Display error ranges around data points. Customize appearance, error calculation method.

#### Imp from video
1. Drill Interactions
	1. Expand down one level - We will simply expand next hierarchy while keeping all data
	2. Go to next  hierarchy -  we will go to next hierarchy for all data without keeping original hierarchy example - in case of dates all quarters will show up for all years without the years
	3. Drill down -  if we click on a data point then we will go to its hierarchy
	4. Drill up -  simply going one level up in hierarchy
2. Edit Interactions - we can edit interactions between different visuals of same page
	1. filter
	2. highlight
	3. none
3. Filter
	1. 3 levels of filter
		1. Visual
		2. Page
		3. Report
	2. 3 Types of filter
		1. Basic
		2. Advanced
		3. Top N / Bottom N
	3. Date filter
		1. Relative date
		2. Relative time
4. Slicer - It is a visual
	1. Date and number slicer
	2. Text slicer
5. Text box
6. Slicer Synchronization - There are essentially two options here, one is actual sync with page and other is whether we can see that slice of that page or not
	1. Sync
	2. View / Visible
7. Sort
8. Small Multiples - If we add field in small multiples it will create one chart for one value of small multiple.
9. Bookmark - Create a snapshot of current state with selected slicers, filter, etc.
10. Selection pane and Groups -  Selection pane help in toggling visibility of an visuals and we can create groups made up of 2 or more visuals.
11. Drill through -a feature that allows users to navigate from a summary view of data to a more detailed view.
12. Buttons and actions - We can customize what buttons do by action following are options
	1. Drill through
	2. Back
	3. Page navigation
	4. Bookmark
	5. Web URL
	6. QnA /  Natural language query
13. Tooltip -  We can create a page and set it up as tooltip via page info.
14. Page navigator and bookmark navigator - we can create navigators for page and bookmarks which behave like slicer and will navigate user to page or bookmark.
15. Conditional formatting
	1. Gradient
	2. Rules
	3. Field value
16. Quick measure
17. Export data - we can export data of a visualization into CSV.
18. Reference line - we can add a line in some of the visualization for specific purpose example showing target which is constant line.
	1. Min
	2. Max
	3. Avg
	4. Median
	5. Constant
	6. Trendline
	7. Forecast line
	8. Percentile line
19. Error bars - if we are not confident that our data is 100% accurate then we can have margin of error as error bar in both upper bound and lower bound.
20. Identify outlier
21. Clustering -  we can use clustering in scatter plot but date should not be hierarchy. 
22. Anomaly detection - only in line chart
23. Narrative visual - 
24. Group and bin
25. Key influencers
26. Analyze feature
27. AI visual decomposition tree
28. accessibility
29. Custom theme
30. Paginated report
31. Report builder

