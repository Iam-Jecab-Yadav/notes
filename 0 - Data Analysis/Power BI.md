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

- **[[Power BI Visuals Details]]**
- **[[Visuals and their fields]]**
- **[[Formatting Power BI visuals]]**
- **[[Some Ad-Hoc Points From Visual]]**


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

**[[Dax Pattern]]**

**[[Time Intelligence]]**












#### [[Dax Query]]

#### [[Dax Functions Input And Return]]

### [[Power service]]




### [[Power BI theocraticals]]






