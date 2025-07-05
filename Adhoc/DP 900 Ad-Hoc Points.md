1. **Hybrid Deployment** - At its core, a **hybrid deployment** is an IT architecture that combines your private, on-premise infrastructure (your own data center) with a public cloud service (like Microsoft Azure). The two environments are not isolated; they are connected and work together to run applications and services.
2. **Dedicated SQL Pools** VS **On-demand pools** - On-demand pools only allow you to query data held in external files. If you want to ingest and load the data into Synapse Analytics, you must create your own SQL pool
3. Parquet 
		1. An open-source, **columnar storage** file format. Think of a spreadsheet: instead of storing data row-by-row, Parquet stores all the values from a single column together.
		2. **High Compression**
		3. **Performance:** Optimized for "write-once, read-many" analytical workloads.
		4. **Use Case:** The standard for data warehousing and analytics in the big data ecosystem, especially with Apache Spark.
4. Avro
		1. An open-source, **row-based** data serialization system. It focuses heavily on rich data structures and robust schema evolution.
		2. **Schema is Key:** Avro requires a schema, which is typically defined in JSON format.
		3. **Use Case:** Ideal for data streaming with tools like Apache Kafka, where producers and consumers might be running different versions of the code and need to handle schema changes gracefully. Also used for serializing data for RPC (Remote Procedure Calls).
5. ORC 
		1. Another open-source, **columnar storage** file format, very similar to Parquet.
		2. **ACID Transactions:** Optimized to support ACID (Atomicity, Consistency, Isolation, Durability) transactions in Hive.
		3. **Use Case:** Heavily used with Apache Hive. It competes directly with Parquet, and the choice between them often depends on the specific tools and workloads. ORC is often cited as being slightly better for read-heavy workloads in Hive.
6. XML
		1. A markup language that defines a set of rules for encoding documents in a format that is both human-readable and machine-readable. It uses tags to define elements.
		2. **Use Case:** Still used in many enterprise systems, SOAP web services, configuration files (e.g., Java's Maven, .NET config), and for document markup (like RSS feeds).
		3. Uses angel brackets like HTML
7. JSON
		1. A lightweight, text-based data interchange format that uses key-value pairs. It is the de facto standard for modern web APIs.
		2. **Use Case:** Web APIs (REST APIs), configuration files, and data exchange between applications.
8. Bicep
		1. A **Domain-Specific Language (DSL)** created by Microsoft for declaratively deploying Azure resources. It is an abstraction layer on top of Azure Resource Manager (ARM) templates.
		2. **Use Case:** The recommended way to practice Infrastructure as Code (IaC) for deploying and managing any resource in Microsoft Azure (e.g., virtual machines, databases, networks, storage accounts).
9. Azure Resource Manager (ARM) template - An **ARM template is the blueprint for your cloud environment in Azure**. It's a file that defines all the Azure resources you want to create, their configurations, and their relationships. At its core, an ARM template is a **JSON (JavaScript Object Notation) file** that defines the infrastructure and configuration for your Azure deployment. It's a key component of **Infrastructure as Code (IaC)** on Azure.
10. Azure Data Explorer - 
	1. Azure Data Explorer (also known as **Kusto**) is a fast, fully managed, big data analytics service from Microsoft. Its primary strength is performing **near real-time, interactive analysis** on extremely large volumes of structured and semi-structured data. **Kusto Query Language (KQL)**, **Time-Series Analysis Powerhouse
	2. **Use Cases** - **Log and Telemetry Analytics**, **IoT Analytics**
11. Spark Structured Streaming
	1. Spark Structured Streaming is a high-level, fault-tolerant, and scalable stream processing engine built on the Spark SQL engine. It's not about processing events one by one. Instead, it treats a live data stream as a continuously growing table.
	2. Used In -
		1. **Azure Databricks**
		2. **Azure Synapse Analytics**
		3. **Azure HDInsight**
12. ELT VS ETL
13. **Lakehouse**
	1. A **Lakehouse** is a modern data architecture that combines the low-cost, flexible storage of a **Data Lake** with the data management, reliability, and performance features of a **Data Warehouse**.
14. Delta Lake
	1. **Delta Lake** is an open-source transactional storage layer that sits on top of ADLS Gen2. It doesn't store the data itself (that's still in Parquet files in ADLS), but it manages it by adding a transaction log.
15. Database and Database server IP rules
16. Paginated report
17. Zero Trust model (Security)
18. SQL Injection Attack- SQL Injection is tricking a website's database into running unintended commands by "injecting" them into a data input field.
19. XSS (Cross Site Scripting) - XSS is an attack where a malicious script is injected into a trusted website. When other users visit the site, their browser executes the script, thinking it's a legitimate part of the page.
20. Brute Force Attack - A brute force attack is an automated, trial-and-error method used to guess a password, PIN, or encryption key.
21. Distributed Denial of Service (DDoS) Attack - A DDoS attack aims to make a website or online service unavailable by overwhelming it with a flood of internet traffic from **many different sources** (this is the "Distributed" part).
22. Authorization token and resource token cosmos DB
23. sqlcmd - **sqlcmd** is a command-line utility provided by Microsoft that allows you to connect to SQL Server instances, run Transact-SQL (T-SQL) statements, and execute script files. It's a powerful and lightweight tool that has been a staple for database administrators (DBAs), developers, and system administrators for many years.
24. Azure File Storage - Transaction Optimized
25. Azure Blob Storage - Blob versioning and **Soft delete**
26. Shared Access Signatures (SAS)
27. Azure PowerShell vs Azure cli