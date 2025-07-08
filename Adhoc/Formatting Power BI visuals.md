
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
			2. **Background:** Toggle to enable/disable the background.
			3. **Color:** Choose a background color using the color picker.
			4. **Transparency:** Adjust the transparency of the background (0% is opaque, 100% is fully transparent).
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
			10. **Header icons:** Toggle to enable/disable header icons.
			11. **Background**
				2. **Background:** Toggle header icon background.
				3. **Color:** Header icon background color.
				4. **Transparency:** Header icon background transparency.
			12. **Border:**
				5. **Border:** Toggle header icon border.
				6. **Color:** Header icon border color.
			13. **Icons**:
				7. **Color:** Color of the icons themselves.
				8. **Hover color:** Color of the icons when you hover over them.
			14. **Transparency:** Overall transparency of the header icons area.
			15. **Padding:** Space around the icons within the header.
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
			4. **Alt text:** Provide a description of the visual for screen readers, improving accessibility for users with visual impairments.
		11. **Lock aspect ratio:** (Often for image visuals)
			1. **Lock aspect ratio:** Maintain the original proportions of the visual when resizing.
		12. **Maintain layer order:** (For visuals that overlap)
			2. **Maintain layer order:** Controls the stacking order of visuals.
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
			6. **Y-Axis:** Toggle to enable/disable the Y-axis.
			7. **Axis title:** (Similar options to X-axis title for customization)
			8. **Values:** (Similar options to X-axis values for formatting)
			9. **Gridlines:** (Similar options to X-axis gridlines, but controls _horizontal_ gridlines)
			10. **Range:** (Similar options to X-axis range for setting start, end, scale type, etc.)
			11. **Secondary Y-axis:** (For visuals that support a secondary Y-axis – often used for combo charts or visuals with different scales) – Options similar to the primary Y-axis are available for the secondary axis.
			12. **Show secondary:** Toggle to show/hide the secondary Y-axis.
			13. **Axis title, Values, Gridlines, Range:** Formatting options for the secondary Y-axis.
		3. **Legend**:
			1. **Legend:** Toggle to enable/disable the legend.
			2. **Position:** Choose where the legend appears (Top, Bottom, Left, Right, Top center, Bottom center, Left center, Right center).
			3. **Legend title**
				1. **Title:** Toggle to enable/disable the legend title.
				2. **Title text:** Customize the legend title.
				3. **Font color, Font size, Font family, Text alignment:** Formatting for the legend title.
			4. **Text:** (Formatting for the legend labels)
				4. **Font color, Font size, Font family:** Text formatting for legend labels.
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
					2. **Border color:** Customize data label border.
				5. **Values:** (Formatting for data label text)
					1. **Font color, Font size, Font family:** Text formatting for data labels.
					2. **Display units, Value decimal places:** Control how data label values are formatted.
					3. **Text wrap:** Wrap long data labels to multiple lines.
				6. **Series labels:** (For visuals with series like line charts or clustered bar charts, you can label the series directly)
					4. **Series labels:** Toggle series labels.
					5. **Position, Orientation, Show background, Border:** Options similar to data label options.
					6. **Values:** Font, display units, etc. formatting similar to data labels values.
		5. **Shapes:** (Controls the visual representation of data points – bars, columns, lines, markers, slices, etc.)
			1. **Color**
				1. **Default series color:** Set a base color for all data series.
				2. **Show all:** (Often present) - Enables customizing colors for individual categories or series. Click "Show all" and you'll see options to set colors for specific categories/series.
				3. **Conditional formatting:** (Often accessed here or through "Data colors") Apply rules to dynamically change data point colors based on data values.
			2. **Customize series:** (Sometimes named differently depending on the visual) – This section allows you to further customize shapes _per series or category_. Options might include:
				4. **Show bar labels:** (For bar charts - adds labels at the end of bars).
				5. **Outline:** Add outlines to shapes
					1. **Outline color, Outline width:** Customize shape outlines.
				6. **Stroke width:** Adjust the thickness of lines in line charts.
				7. **Show marker:** (Line and Scatter charts) Toggle markers on/off.
				8. **Marker shape, Marker size, Marker color:** Customize markers.
				9. **Data colors:** (Can sometimes be within "Shapes" or a separate "Data colors" category) – This is often where you can set specific colors for each category or series. You might see a list of categories and color pickers to assign colors.
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
			4. **Header:** (Slicer title)
			5. **Items:** (Formatting for the slicer values/buttons)
			6. **Slicer header:** (Formatting for the slicer's "Category" label)
		9. **Card:** (For card visuals)
			1. **Value:** (Formatting for the main value displayed)
			2. **Category label:** (Formatting for the label below the value)
			3. **Callout value:** (Another way to refer to the main value formatting)
		10. **Map visual specific options:** (For Map and Filled Map visuals)
			4. **Map styles:** Choose base map styles (Road, Aerial, Dark, Light, Grayscale).
			5. **Bubbles:** (For bubble maps) - Control bubble size, color.
			6. **Category labels:** (For maps with categories) - Formatting for category labels.
			7. **Data colors:** Color settings for map regions or bubbles.
			8. **Zoom controls:** Enable/disable zoom buttons on the map.
			9. **Search:** Enable/disable map search functionality.
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
			4. **Data colors:** Colors for funnel segments.
			5. **Category labels:** Formatting for segment labels.
			6. **Convert labels:** Formatting for converted value labels.
			7. **Percent labels:** Formatting for percentage labels.
		15. **Waterfall chart specific options:**
			1. **Data colors:** Colors for increase, decrease, and total columns.
			2. **Category labels:** Formatting for column labels.
			3. **Value labels:** Formatting for value labels on columns.
			4. **Y-Axis:** (Standard Y-axis options).
			5. **Category axis:** (Specific options for the category axis in a waterfall chart if applicable).
	4. **Analytics Pane Formatting (Sometimes integrated or separate)**	
		16. **Constant line:** Add a fixed horizontal or vertical line at a specific value. Customize color, style, data label.
		17. **Min/Max lines:** Dynamically show lines at the minimum and maximum values in your data. Customize appearance.
		18. **Average line:** Show the average value as a line. Customize appearance.
		19. **Median line:** Show the median value as a line. Customize appearance.
		20. **Percentile lines:** Add lines at specific percentile values.
		21. **Forecast:** (For time series visuals) Add a predictive forecast to your line chart. Customize forecast length, confidence interval, appearance.
		22. **Error bars:** (Often in scatter charts and line charts) Display error ranges around data points. Customize appearance, error calculation method.