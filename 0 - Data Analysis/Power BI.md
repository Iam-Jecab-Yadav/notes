[[Power BI short notes]]
### What is Power BI?
**Business Intelligence Tool:** Power BI is a suite of tools from Microsoft designed for **data visualization and business intelligence**. It helps you analyze data and share insights.
**Self-Service BI:** It's built to be user-friendly, allowing business users (not just IT) to create reports and dashboards without extensive technical skills.
**Connects to Data Sources:** Power BI can pull data from a wide variety of sources (databases, spreadsheets, cloud services, web APIs, etc.).
**Transforms and Models Data:** You can clean, shape, and model your data within Power BI to make it ready for analysis and visualization.
**Visualizations and Reports:** Power BI allows you to create interactive charts, graphs, maps, and reports to understand your data visually.
**Dashboards:** You can consolidate key visualizations and reports into dashboards for a high-level overview of your data.
**Sharing and Collaboration:** Power BI facilitates sharing reports and dashboards with others and collaborating on data analysis.


### [[Lifecycle of power BI project]]





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


### Power query / Get data

#### Detailed Overview of Power Query

Power Query is a powerful data transformation and preparation engine available in various Microsoft products like Excel, Power BI, Azure Data Factory, Power Apps, and Analysis Services. It provides an intuitive, user-friendly interface for connecting to, cleaning, shaping, and transforming data from a wide range of sources. Think of it as a self-service ETL (Extract, Transform, Load) tool for business users and data analysts.

Here's a detailed breakdown of Power Query:

**1. Core Functionality:**

- **Data Connectivity:** Power Query can connect to a vast array of data sources, including:
    - Files: Excel workbooks, CSV files, Text files, XML, JSON, PDF, etc.
    - Databases: SQL Server, Oracle, MySQL, PostgreSQL, Access, Azure SQL Database, etc.
    - Online Services: SharePoint, Dynamics 365, Salesforce, Google Analytics, Facebook, etc.
    - Web: Web pages, APIs.
    - Other Sources: Hadoop files, Active Directory, ODBC, OLE DB, etc.
- **Data Transformation:** This is the heart of Power Query. It allows you to perform numerous operations to clean, shape, and restructure your data without writing complex code. Some key transformations include:
    - **Filtering:** Removing rows based on specific criteria.
    - **Sorting:** Arranging rows in ascending or descending order.
    - **Grouping:** Summarizing data by aggregating values based on common columns.
    - **Merging:** Combining data from multiple tables based on matching columns (similar to SQL JOIN).
    - **Appending:** Combining rows from multiple tables into a single table (similar to SQL UNION ALL).
    - **Pivoting and Unpivoting:** Reshaping data to change the orientation of columns and rows.
    - **Adding/Removing Columns:** Creating new calculated columns or deleting unnecessary ones.
    - **Data Type Conversion:** Changing the data type of columns (e.g., text to number, date to text).
    - **Text Manipulation:** Splitting columns, extracting substrings, changing case, trimming whitespace.
    - **Number Manipulation:** Performing mathematical operations, rounding, calculating percentages.
    - **Date and Time Manipulation:** Extracting date parts, calculating date differences, formatting dates.
    - **Error Handling:** Identifying and managing errors in your data.
    - **Conditional Logic:** Applying transformations based on specific conditions.
- **Data Loading:** Once the data is transformed, Power Query allows you to load it into various destinations:
    - **Excel:** Load the transformed data into worksheets or the Excel Data Model (for Power Pivot).
    - **Power BI Desktop:** Load the data into the Power BI data model for visualization and analysis.
    - **Azure Data Factory:** Use the transformed data in data flows for building ETL pipelines.
    - **Power Apps (Dataflows):** Create reusable data preparation logic for Power Apps.
    - **Analysis Services (Tabular Models):** Prepare data for use in tabular models.

**2. Key Features and Concepts:**

- **Power Query Editor:** This is the primary interface for building and managing your data transformations. It provides a visual, step-by-step approach to data manipulation.
    - **Query Pane:** Displays a list of all your queries.
    - **Formula Bar:** Shows the underlying M code for each transformation step.
    - **Preview Pane:** Displays a sample of the data at each step of the transformation process.
    - **Applied Steps Pane:** Lists all the transformations you've applied to your data in sequential order. This allows you to easily review, edit, reorder, or delete steps.
- **M Formula Language:** While Power Query offers a user-friendly interface, it also has a powerful underlying functional programming language called "M". You can directly write or edit M code for more advanced transformations or to automate complex logic.
- **Query Folding:** At its core, Query Folding is the process where Power Query (the data transformation engine in Power BI, Excel Get & Transform, Dataflows, etc.) translates the transformations you build in the Power Query Editor (which are written in the M language) into the native query language of the data source. Instead of Power Query pulling all the data from a SQL server and then filtering it, removing columns, and grouping it on your local machine, Query Folding tells the SQL server: "Hey, SQL Server, please execute this SQL query which already includes the filtering, column removal, and grouping. Then just send me the much smaller, pre-processed result." It is supported for - **Relational Databases**, It is not supported for - **Flat files (CSV, TXT)**, **Excel files**, **Web pages (basic Web.Contents)**, **Folders**
- **Parameters:** Power Query allows you to define parameters, which are named values that can be used within your queries. This enables you to create dynamic queries that can be easily adapted to different scenarios (e.g., filtering by a specific date range).
- **Functions:** You can create custom functions in M to encapsulate reusable transformation logic. This helps in creating modular and maintainable queries.
- **Templates:** Power Query allows you to save your queries as templates, which can then be easily applied to other similar data sources.
- **Error Handling:** Power Query provides mechanisms to detect and handle errors that might occur during data transformation. You can choose to remove error rows, replace error values, or keep the errors for further investigation.

**3. Power Query Workflow:**

The typical workflow in Power Query involves these steps:

1. **Connect:** Establish a connection to your desired data source using one of the available connectors.
2. **Transform:** Use the Power Query Editor to apply various transformations to clean, shape, and restructure your data according to your requirements. Each transformation is recorded as a step in the "Applied Steps" pane.
3. **Combine (Optional):** If needed, combine data from multiple queries using operations like Merge or Append.
4. **Load:** Once the data is transformed and ready, load it into your chosen destination (e.g., Excel worksheet, Power BI data model).

**4. Benefits of Using Power Query:**

- **User-Friendly Interface:** The intuitive graphical interface makes data transformation accessible to users without extensive programming knowledge.
- **Wide Range of Data Source Connectivity:** Ability to connect to virtually any data source used in modern business environments.
- **Automation of Data Preparation:** Once a query is created, it can be refreshed to automatically apply the same transformations to updated data.
- **Improved Data Quality:** By allowing you to clean and validate data, Power Query helps ensure the accuracy and reliability of your analysis.
- **Increased Efficiency:** Automating data preparation tasks saves significant time and effort compared to manual data manipulation.
- **Centralized Data Transformation Logic:** Power Query stores the transformation steps within the query itself, providing a clear and auditable record of how the data was processed.
- **Enhanced Data Analysis Capabilities:** By providing clean and well-structured data, Power Query empowers more effective data analysis and reporting.
- **Code-Free (Mostly):** While M code provides advanced capabilities, most common transformations can be performed using the graphical interface without writing any code.

**5. Use Cases of Power Query:**

Power Query is used in a wide variety of scenarios, including:

- **Cleaning and Preparing Data for Excel Analysis:** Removing duplicates, standardizing formats, filling in missing values, and structuring data for pivot tables and charts.
- **Building Data Models in Power BI:** Connecting to multiple data sources, transforming and combining data to create a robust data model for visualizations and reports.
- **Automating Data Integration Processes:** Setting up recurring data refreshes to automatically pull and transform data from various systems.
- **Consolidating Data from Multiple Sources:** Combining data from different databases, spreadsheets, and online services into a unified dataset for analysis.
- **Transforming Web Data:** Extracting data from web pages and APIs and shaping it for analysis.
- **Preparing Data for Machine Learning:** Cleaning and structuring data to make it suitable for machine learning algorithms.
- **Data Wrangling and Exploration:** Quickly exploring and understanding data by applying various transformations and observing the results.

**6. Where to Find Power Query:**

- **Microsoft Excel:** Found under the "Data" tab in the "Get & Transform Data" group (formerly known as "Get External Data").
- **Power BI Desktop:** Integrated as the data transformation engine when you click "Get Data" or "Transform Data".
- **Azure Data Factory:** Available as a "Data Flow" activity, allowing you to build graphical data transformation pipelines.
- **Power Apps (Dataflows):** Can be used to create reusable data preparation logic that can be used within Power Apps.
- **SQL Server Analysis Services (SSAS) Tabular:** Integrated for data preparation within tabular models.


#### M Code

**What is M Code?**

M code, formally known as the Power Query Formula Language, is the language used behind the scenes in Microsoft Power Query (available in Excel, Power BI Desktop, and other Microsoft products) to perform data transformations. When you use the Power Query Editor's graphical interface to connect to data sources and apply transformations (like filtering, sorting, merging, pivoting, etc.), Power Query automatically generates the corresponding M code.

**Key Characteristics of M Code:**

- **Functional Language:** M is a functional programming language. This means that computations are performed by evaluating expressions, and functions are treated as first-class citizens.
- **Expression-Based:** Every piece of M code is an expression that evaluates to a value.
- **Case-Sensitive:** `MyVariable` is different from `myvariable`.
- **Strongly Typed (Implicitly):** While you don't explicitly declare data types for variables, M infers the types based on the operations and data. It enforces type compatibility during execution.
- **Lazy Evaluation:** Expressions are only evaluated when their results are needed. This can improve performance for complex queries.
- **Immutable:** Once a value is assigned to a variable, it cannot be changed directly. Instead, new values are created based on transformations.

**Structure of an M Query:**

An M query typically consists of the following elements:

1. **Sections (Optional):**
    
    - Sections provide a way to organize and name related queries, functions, and variables.
    - They start with the keyword `section` followed by a section name and a semicolon.
    - Within a section, you can define members using the `=` operator.
    - Example:
        

        
        ```
        section MySection;
        
        Shared Query1 = ...;
        Shared MyFunction = (...) => ...;
        ```
        
    - In most common scenarios, you'll work with a single query without explicitly defining sections.
    
2. **Let Expression:**
    
    - The `let` expression is the heart of an M query. It allows you to define a series of named steps (variables) that represent intermediate transformations.
    - Each step is defined as `variableName = expression;`.
    - The semicolon `;` separates each step.
    - The order of steps matters as subsequent steps can refer to the results of previous steps.
    - Example:
        
        Code snippet
        
        ```
        let
            Source = Csv.Document(File.Contents("C:\Data\Sales.csv"),[Delimiter=",", Columns=5, Encoding=1252, QuoteStyle=QuoteStyle.None]),
            #"Promoted Headers" = Table.PromoteHeaders(Source, [PromoteAllScalars=true]),
            #"Changed Type" = Table.TransformColumnTypes(#"Promoted Headers",{{"OrderID", Int64.Type}, {"Product", type text}, {"Quantity", Int64.Type}, {"Price", type number}, {"OrderDate", type date}}),
            FilteredRows = Table.SelectRows(#"Changed Type", each [Quantity] > 1)
        in
            FilteredRows
        ```
        
3. **In Clause:**
    
    - The `in` clause specifies the final result of the query. It refers to one of the variables defined in the `let` expression.
    - In the example above, `in FilteredRows` means the table resulting from the `FilteredRows` step will be the output of the query.

**Core Concepts and Elements of M Code:**

1. **Data Types:** M supports various primitive and structured data types:
    
    - **Primitive Types:**
        - `type number`: Represents numeric values (integers and decimals).
        - `type logical`: Represents boolean values (`true` or `false`).
        - `type text`: Represents text strings.
        - `type date`: Represents dates.
        - `type datetime`: Represents1 date and time values.
        - `type datetimezone`:2 Represents date, time, and timezone information.
        - `type duration`: Represents a time interval.
        - `type binary`: Represents binary data.
        - `type null`: Represents the absence of a value.
    - **Structured Types:**
        - `type list`: An ordered sequence of values enclosed in curly braces `{}`. Example: `{1, 2, 3}` or `{"Apple", "Banana", "Cherry"}`. Lists can contain values of different types.
        - `type record`: A set of fields, where each field has a name and a value, enclosed in square brackets ``. Example: `[Name="John", Age=30]`. Field names are case-sensitive.
        - `type table`: A structured collection of data organized into rows and columns.
2. **Operators:** M provides various operators to perform operations on data:
    
    - **Arithmetic Operators:** `+` (addition), `-` (subtraction), `*` (multiplication), `/` (division), `&` (concatenation for text).
    - **Comparison Operators:** `=`, `<>`, `<`, `>`, `<=`, `>=`.
    - **Logical Operators:** `and`, `or`, `not`.
    - **Text Operators:** `&` (concatenation).
    - **List Operators:** `{}` (list creation), `{index}` (accessing element at index), `&` (list concatenation).
    - **Record Operators:** `` (record creation), `[FieldName]` (accessing field value).
    - **Conditional Operator:** `if ... then ... else ...`.
3. **Functions:**
    
    - M has a rich library of built-in functions that perform various data transformations. These functions are often used in the steps of a `let` expression. Examples include:
        - `Table.AddColumn()`
        - `Table.SelectRows()`
        - `Table.TransformColumnTypes()`
        - `List.Average()`
        - `Text.Upper()`
        - `Date.AddDays()`
    - You can also define your own custom functions using the `=>` (goes-to) operator.
        - Example: `(x, y) => x + y` defines a function that takes two arguments and returns their sum.
4. **Control Flow:**
    
    - **Conditional Statements:** The `if ... then ... else ...` expression allows you to perform different actions based on a condition.
        - Example:
            
            Code snippet
            
            ```
            if [Quantity] > 10 then "High" else "Low"
            ```
            
5. **Error Handling:**
    
    - The `try ... otherwise ...` expression allows you to handle potential errors that might occur during the evaluation of an expression.
        - Example:
            
            Code snippet
            
            ```
            try Number.FromText("abc") otherwise null
            ```
            
            This will attempt to convert "abc" to a number. If it fails, it will return `null` instead of raising an error.
6. **Variables:**
    
    - Variables are defined within the `let` expression to store intermediate results. They are immutable within their scope.
7. **Comments:**
    
    - You can add comments to your M code to explain the logic.
    - Single-line comments start with `//`.
    - Multi-line comments are enclosed between `/*` and `*/`.

**Accessing and Editing M Code:**

You can view and edit the M code generated by Power Query through the **Advanced Editor**. To access it:

1. Open Power Query Editor (e.g., in Excel: Data tab > Get Data > Launch Power Query Editor).
2. Select the query you want to examine.
3. In the Power Query Editor ribbon, go to the **Home** tab.
4. Click on **Advanced Editor** in the Query group.

The Advanced Editor window will display the M code for the selected query. You can directly edit this code to perform more complex or customized transformations that might not be easily achievable through the graphical interface.

**Benefits of Using M Code:**

- **Customization:** M code provides granular control over data transformations, allowing you to implement complex logic tailored to your specific needs.
- **Advanced Transformations:** Certain transformations are only possible or easier to implement by directly writing or modifying M code.
- **Performance Optimization:** Understanding M code can help you write more efficient queries.
- **Reusability:** You can create custom functions in M code that can be reused across multiple queries.
- **Understanding Power Query Internals:** Working with M code gives you a deeper understanding of how Power Query works.




### Data model


#### Data Modeling in Power BI (Focus on Structure)

Data modeling in Power BI is the foundational process of structuring and organizing your data to create a robust and efficient analytical environment. It involves defining the relationships between different datasets, choosing an appropriate schema, and optimizing the structure for performance and accurate insights. A well-defined data model is critical for building effective and reliable Power BI reports and dashboards.

**1. Core Components of a Data Model:**

- **Tables:** These are the containers for your data. In a Power BI data model, tables can generally be categorized into two primary types based on their role:
    
    - **Fact Tables:**
        
        - **Purpose:** Fact tables are the central tables in your data model and contain the core measurements, metrics, or events that you want to analyze. They record what happened and often include quantitative data.
        - **Characteristics:**
            - Typically contain foreign keys that link to dimension tables.
            - Often have one or more numeric columns representing the measures (e.g., Sales Amount, Quantity, Temperature).
            - Can have a composite key formed by the combination of foreign keys.
            - Tend to be tall and thin, with many rows and relatively few columns.
        - **Types of Fact Tables:**
            - **Transaction Fact Tables:** Record individual transactions or events as they occur (e.g., each sale, each website visit).
            - **Snapshot Fact Tables:** Capture the state of something at a particular point in time (e.g., daily inventory levels, monthly account balances).
            - **Accumulating Snapshot Fact Tables:** Track the progress of a process over its lifecycle, with columns that can be updated as the process moves through different stages (e.g., order fulfillment process).
    - **Dimension Tables:**
        
        - **Purpose:** Dimension tables contain descriptive attributes that provide context to the facts in the fact tables. They answer the questions of who, what, where, when, and why related to the events recorded in the fact table.
        - **Characteristics:**
            - Contain a primary key that uniquely identifies each record.
            - Have descriptive columns or attributes that provide context (e.g., for a "Product" dimension, attributes might include Product Name, Category, Color, Size).
            - Tend to be wide and short, with fewer rows but many columns.
        - **Common Dimension Tables:**
            - **Date Dimension:** Contains attributes related to dates (Year, Quarter, Month, Day, Day of Week). This is crucial for time-based analysis.
            - **Product Dimension:** Details about products (Name, Category, Subcategory, Brand).
            - **Customer Dimension:** Information about customers (Name, City, Country, Segment).
            - **Geography Dimension:** Details about locations (Country, Region, City).
            - **Organization Dimension:** Information about internal structures (Department, Employee).
- **Relationships:** These define the associations between tables in your data model, allowing Power BI to understand how data in one table relates to data in another.
    
    - **Types of Relationships:**
        
        - **One-to-Many (1:*):** A single record in one table (the "one" side, typically a dimension table) can be associated with multiple records in another table (the "many" side, typically a fact table). For example, one product can appear in multiple sales transactions.
        - **One-to-One (1:1):** Each record in one table is associated with exactly one record in another table. This is less common and might be used to split a table with many columns for performance or security reasons.
        - **Many-to-Many (*:*):** Multiple records in one table can be associated with multiple records in another table. Power BI handles many-to-many relationships by automatically creating an intermediary hidden table (often referred to as a bridge or junction table) that contains unique combinations of the related columns from the two original tables. You don't typically create this table manually.
    - **Cardinality:** This refers to the uniqueness of the data in the related columns of two tables. Power BI infers cardinality based on the data but it's crucial to ensure it's correct. Common cardinality options you might see in the relationship editor include:
        
        - **One to many (1:*):** As described above.
        - **Many to one (* : 1):** This is the same as one-to-many but viewed from the perspective of the "many" side.
        - **One to one (1:1):** As described above.
        - **Many to many (*:*):** As described above.
    - **Cross-filter Direction:** This determines how filters applied to one table will affect the data displayed in related tables. There are two main options:
        
        - **Single:** Filtering occurs in only one direction. Typically, filtering flows from the "one" side of a one-to-many relationship to the "many" side. For example, if you filter by a specific product in the Product dimension table, it will filter the corresponding sales records in the Sales fact table.
        - **Both:** Filtering can occur in both directions between the two tables. This is often used in scenarios with one-to-one relationships or when Power BI creates the intermediary table for many-to-many relationships. While it offers flexibility, using "Both" directionality in one-to-many relationships should be done cautiously as it can sometimes lead to ambiguous filter propagation and performance issues if not well understood. Power BI might automatically suggest "Both" in certain situations, but it's important to review if it aligns with your analytical needs.

**2. Data Modeling Schemas:**

The way you structure your tables and relationships defines your data model's schema. Here are the most common schemas used in Power BI:

- **Star Schema:**
    
    - **Structure:** The star schema is the most widely recommended schema for Power BI due to its simplicity and performance benefits. It consists of one or more fact tables at the center, surrounded by several dimension tables, resembling a star.
    - **Characteristics:**
        - Fact tables are directly related to dimension tables through foreign keys.
        - Dimension tables are typically not related to each other (they are denormalized).
        - This structure simplifies queries and improves performance as Power BI can efficiently filter and aggregate data.
    - **Advantages:**
        - Simple to understand and implement.
        - Optimized for query performance, especially for aggregations.
        - Reduces the complexity of joins needed for analysis.
    - **Disadvantages:**
        - Can lead to some data redundancy in dimension tables as attributes might be repeated across different product categories, for example.
- **Snowflake Schema:**
    
    - **Structure:** The snowflake schema is a variation of the star schema where dimension tables are further normalized into sub-dimension tables, creating a branching structure that resembles a snowflake.
    - **Characteristics:**
        - Fact tables are connected to dimension tables.
        - Dimension tables are further broken down into related dimension tables. For example, a Product dimension might be split into Product, Category, and Subcategory tables.
    - **Advantages:**
        - Reduces data redundancy in dimension tables compared to the star schema.
    - **Disadvantages:**
        - Can increase the complexity of the data model with more tables and relationships to manage.
        - May lead to more complex queries and potentially impact performance due to the need for more joins.
        - While it reduces redundancy, the performance trade-off often makes the star schema a preferred choice for Power BI.
- **Galaxy Schema (or Forest of Stars)**
	- **Structure:** A galaxy schema is essentially a collection of multiple star schemas. It arises when you have multiple fact tables that share some common dimension tables, but also have dimension tables unique to each fact table. Imagine several star schemas linked together through conformed dimensions.
	- **Characteristics**
		- - Contains multiple fact tables.
		- Fact tables can share some dimension tables (these are called **conformed dimensions**).
		- Each fact table may also have its own set of dimension tables that are not shared.
	- **When to Use:** Galaxy schemas are typically used in more complex data warehousing environments where different business areas or processes have their own sets of facts and specific dimensions but also share common dimensions like Date, Customer, or Product.
	- **Advantages**
		- Allows for modeling complex business scenarios with multiple areas of analysis.
		- Provides flexibility to analyze data within specific business processes or across them using conformed dimensions.
	- **Disadvantages**
		- Can be more complex to design and understand than a single star schema.
		- Performance might be impacted if relationships and filtering are not carefully managed across the multiple star schemas.


**3. Data Types and Formatting (in the context of modeling):**

While seemingly basic, ensuring correct data types for each column is crucial for the integrity and performance of your data model. For instance, if a column containing dates is treated as text, you won't be able to perform proper time-based analysis. Similarly, choosing the most appropriate numeric data type (e.g., Integer vs. Decimal) can impact storage and calculation efficiency. Formatting primarily affects how the data is displayed in visuals but doesn't directly impact the model's structure.

**4. Data Cleansing and Transformation (Impact on Modeling):**

The steps you take in Power Query to clean and transform your data directly influence the structure and quality of your final data model. For example:

- **Splitting columns:** Can create more granular attributes that can become part of dimension tables.
- **Pivoting/Unpivoting data:** Can reshape your data into a more analytical-friendly format with clear fact and dimension structures.
- **Merging queries:** Can combine data from different sources into a single table that fits your model.
- **Adding calculated columns (in Power Query):** Can create new attributes that become part of your tables before the modeling stage.

**5. Best Practices for Structural Data Modeling in Power BI:**

- **Identify Fact and Dimension Tables Clearly:** Understand the core measurements and the contextual attributes that describe them.
- **Aim for a Star Schema:** Unless there's a compelling reason (like significant data redundancy that impacts storage and is unlikely to change), the star schema is generally the best starting point for Power BI.
- **Ensure Data Integrity:** Clean and transform your data thoroughly in Power Query to handle missing values, inconsistencies, and errors before loading it into the model.
- **Establish Relationships Correctly:** Accurately define the relationships between your tables, ensuring the cardinality and cross-filter direction are appropriate for your analytical needs. Be cautious with "Both" cross-filter direction in one-to-many relationships.
- **Use Meaningful Table and Column Names:** Clear and descriptive names make your data model easier to understand and maintain.
- **Keep Dimension Tables Denormalized (in a Star Schema):** Avoid unnecessary normalization of dimension tables that can complicate the model and potentially impact performance.
- **Optimize Data Types:** Choose the most appropriate data type for each column to improve performance and reduce storage.
- **Minimize the Use of Calculated Columns in the Model (if possible):** While sometimes necessary, excessive use of calculated columns can impact performance. Consider performing these calculations in Power Query or using measures instead.
- **Test Your Relationships and Filters:** Ensure that filters applied in one table correctly propagate to related tables as expected.

**6. Advanced Structural Modeling Concepts:**

- **Calculated Tables (from a structural perspective):** While they involve DAX, calculated tables allow you to create new tables based on existing data in your model. This can be useful for creating supporting dimension tables, summarizing data for specific purposes, or creating disconnected tables for user selections. They add to the structural complexity of your model but can solve specific analytical challenges.

By focusing on these structural aspects of data modeling, you can build a solid foundation for your Power BI reports, ensuring accuracy, performance, and ease of use for your end users. Remember that a well-thought-out data model is a critical investment in the success of your business intelligence efforts.

#### DAX


DAX (Data Analysis Expressions) is the formula language of Power BI, Power Pivot in Excel, and Analysis Services Tabular models. It's a powerful tool that allows you to create custom calculations on your data, going beyond the simple aggregations offered by drag-and-drop functionality. Understanding DAX is crucial for unlocking the full potential of Power BI and creating insightful and dynamic reports.

Here's a detailed overview of DAX in Power BI:

**1. What is DAX and Why is it Important?**

- **Definition:** DAX is a collection of functions, operators, and constants that can be used in a formula, or expression, to calculate and return one or more values. Think of it as the "Excel formulas" for your Power BI data model.
- **Purpose:** DAX enables you to:
    - **Perform complex calculations:** Calculate ratios, percentages, running totals, year-over-year growth, and more.
    - **Create custom aggregations:** Define specific ways to summarize your data beyond standard SUM, AVERAGE, COUNT, etc.
    - **Implement business logic:** Apply specific rules and conditions to your data for analysis.
    - **Enhance data insights:** Derive meaningful information and patterns from your raw data.
    - **Create dynamic reports:** Make your visuals respond to user interactions and filters.

**2. Core Concepts of DAX:**

- **Measures:** These are the most common use case for DAX. Measures represent calculations that are evaluated within the context of a visual. They don't exist in your underlying data model as static values.
    - **Characteristics:**
        
        - Calculated on the fly based on the filters and context applied to the visual.
        - Typically involve aggregations (SUM, AVERAGE, MIN, MAX, COUNT, etc.).
        - Defined within a specific table but can reference columns from other related tables.
        
    - **Example:** `Total Sales = SUM(Sales[Amount])`1
- **Calculated Columns:** These are new columns that you add to an existing table in your data model. The DAX formula for a calculated column is evaluated for each row in the table.
    - **Characteristics:**
        - Stored in the data model, increasing its size.
        - Calculated once during data refresh.
        - Useful for categorizing data, creating segments, or performing row-level calculations.
    - **Example:** `Profit Margin = DIVIDE(Sales[Profit], Sales[Amount])`
- **Calculated Tables:** These are virtual tables that are created using DAX formulas. They don't exist in your original data source but are derived from existing tables.
    - **Characteristics:**
        - Useful for creating summarized tables, date tables, or tables based on specific criteria.
        - Can help simplify complex calculations or create specific data slices for analysis.
    - **Example:** `High Performing Products = FILTER(Products, Products[Sales] > 1000)`

**3. Key Components of DAX:**

- **Functions:** DAX has a rich library of functions categorized into various types:
    - **Aggregation Functions:** (e.g., `SUM`, `AVERAGE`, `MIN`, `MAX`, `COUNT`, `COUNTA`, `COUNTROWS`, `DISTINCTCOUNT`) - Perform aggregations on data.
    - **Logical Functions:** (e.g., `IF`, `AND`, `OR`, `NOT`, `SWITCH`) - Evaluate conditions and return different values based on the outcome.
    - **Information Functions:** (e.g., `ISBLANK`, `ISERROR`, `ISFILTERED`, `HASONEVALUE`) - Provide information about the data or the current context.
    - **Date and Time Functions:** (e.g., `TODAY`, `NOW`, `YEAR`, `MONTH`, `DAY`, `DATE`, `TIME`, `DATEDIFF`, `DATEADD`) - Work with date and time values.
    -  **Filter Functions:** (e.g., `FILTER`, `ALL`, `ALLEXCEPT`, `ALLSELECTED`, `CALCULATE`, `KEEPFILTERS`, `HASONEVALUE`, `HASMANYVALUES`, `ISFILTERED`) - Helps in filter.
    - **Text Functions:** (e.g., `CONCATENATE`, `LEFT`, `RIGHT`, `MID`, `UPPER`, `LOWER`) - Manipulate text strings.
    - **Table Manipulation Functions:** (e.g., `FILTER`, `CALCULATETABLE`, `ALL`, `VALUES`, `DISTINCT`, `UNION`, `INTERSECT`, `EXCEPT`) - Create and modify tables.
    - **Relationship Functions:** (e.g., `RELATED`, `RELATEDTABLE`, `USERELATIONSHIP`) - Navigate and utilize relationships between tables.
    - **Mathematical Functions:** (e.g., `DIVIDE`, `SQRT`, `ABS`, `ROUND`) - Perform mathematical operations.
    - **Statistical Functions:** (e.g., `STDEV.P`, `VAR.P`) - Perform statistical calculations.
    - **Time Intelligence Functions:** (e.g., `TOTALYTD`, `PREVIOUSYEAR`, `SAMEPERIODLASTYEAR`, `DATEYTD`) - Perform calculations across time periods.
- **Operators:** These symbols are used to perform operations within DAX expressions:
    - **Arithmetic Operators:** (+, -, *, /, ^) - Perform mathematical calculations.
    - **Comparison Operators:** (=, >, <, >=, <=, <>) - Compare values.
    - **Logical Operators:** (&& - AND, || - OR, NOT) - Combine or negate conditions.
- **Syntax:** DAX expressions follow a specific structure:
    - `Measure Name =` or `Column Name =` or `Table Name =`
    - `DAX Function( [Column Name] , [Optional Argument] , ... )`
    - DAX is not case-sensitive, but it's good practice to use consistent capitalization for readability.

**4. Understanding Evaluation Context:**

This is a crucial concept in DAX. The context in which a DAX expression is evaluated determines the final result. There are two main types of context:

- **Row Context:** This applies when a DAX formula is evaluated for each row of a table (primarily in calculated columns and within iterator functions like `SUMX`). In row context, the formula can directly refer to the values in the columns of the current row.
- **Filter Context:** This applies when a DAX formula is evaluated within a visual. Filters applied to the visual (either explicitly by the user or implicitly by the visual structure) restrict the data that is being considered for the calculation.

**Context Transition:** Certain DAX functions, like `CALCULATE` and `CALCULATETABLE`, can transition the context. For example, `CALCULATE` can take a row context and apply it as a filter context. This is a powerful mechanism for manipulating the data being evaluated.

**5. Variables in DAX:**

The `VAR` keyword allows you to declare variables within a DAX expression. This can improve the readability and performance of your formulas, especially for complex calculations.

- **Syntax:**
    
    Code snippet
    
    ```
    Measure Name =
    VAR TotalRevenue = SUM(Sales[Amount])
    VAR TotalCost = SUM(Sales[Cost])
    RETURN TotalRevenue - TotalCost
    ```
    
- **Benefits:**
    - **Readability:** Breaks down complex calculations into smaller, understandable steps.
    - **Performance:** Avoids redundant calculations by storing intermediate results.
    - **Debugging:** Makes it easier to identify issues within a complex formula.

**6. Best Practices for Writing DAX:**

- **Understand your data model:** A well-designed data model is essential for writing efficient DAX.
- **Write clear and concise formulas:** Use meaningful names for measures, columns, and variables. Add comments for complex logic.
- **Optimize for performance:** Avoid unnecessary iterations and complex calculations on large datasets. Use functions like `DIVIDE` to handle potential division by zero errors.
- **Test your calculations thoroughly:** Verify that your DAX formulas are producing the expected results.
- **Use variables for complex calculations:** Improve readability and potentially performance.
- **Leverage the Power BI community and documentation:** There are vast resources available online to help you learn and troubleshoot DAX.
- **Consider the evaluation context:** Always be mindful of how the row and filter context will affect your calculations.

**7. Common Use Cases for DAX in Power BI:**

- **Calculating sales growth:** Comparing current period sales to previous periods.
- **Identifying top-performing products or customers:** Filtering data based on specific criteria.
- **Calculating moving averages or running totals:** Analyzing trends over time.
- **Creating custom KPIs (Key Performance Indicators):** Defining and tracking important business metrics.
- **Implementing complex filtering logic:** Showing data based on multiple conditions.
- **Performing what-if analysis:** Simulating different scenarios and their impact on results.
- **Creating dynamic segmentation:** Grouping customers or products based on their behavior.

##### [[Functions]]


**[[DAX Functions]]**




#### [[Dax Query]]

#### [[Dax Functions Input And Return]]

### [[Power service]]




### [[Power BI theocraticals]]






