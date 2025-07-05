1. **SELECT Statement**
2. **Describe relational data loads**
3.  **Describe azure relational data loads**
	1. Azure SQL Database
	2. Azure SQL Managed Instance
	3. Azure VM
	4. Azure Database - PostgreSQL
	5. Azure Database - MYSQL
	6. Azure Database - Maria DB
4. **Describe Non relational/Semi structured data loads**
5. **Describe azure Non relational/Semi structured data loads**
	1. Azure Cosmos DB
		1. APIs
			1. Core(SQL) API -  Documents (JSON)
			2. Gremlin API - graph database
			3. MongoDB API -  JSON
			4. Table API - Kay Value
			5. Cassandra API - Column Family
		2. Inconsistencies
			1. Strong 
				1. A read is guaranteed to return the most recent version of an item. Your read will wait until the change you made (the "write") has been confirmed by a majority of the data replicas.
				2. Financial transactions, e-commerce orders, critical inventory systems.
			2. Bounded Staleness
				1. Reads might lag behind the latest writes, but only by a specific, configurable amount. You can set the "bound" in two ways **Time**, **Versions**
				2. Stock tickers, live sports scores, dashboards
			3. Session Consistency
				1. This is the most popular level. Within a single client session (e.g., a user's session on your website), you are guaranteed to read your own writes. If you update an item, your next read in that same session will see the update. Other users (in other sessions) might see the old data for a short time.
				2. User profiles, shopping carts, social media feeds
			4. Consistent Prefix
				1. Reads will never see out-of-order updates. If you performed writes in the order A, then B, then C, a user will see A, then A and B, then A, B, and C. They will **never** see C before they have seen B. They might be behind, but the order is always correct.
				2. Change feeds, event sourcing pipelines
			5. Eventual Consistency
				1. This is the weakest level. Reads will eventually see the latest write, but there are no guarantees on the delay or the order. Different replicas may have different versions of the data at any given time.
				2. Non-critical data like a "like" count on a post, view counts
	2. Azure Cache for Redis
6. **Describe Unstructured data loads**
7. **Describe Unstructured data loads on azure**
	1. Azure Blob Storage
		1. **Analogy:** Think of it as a massive, infinitely scalable cloud drive for your files, but instead of a folder structure, it's a flat object store. It's like a limitless digital warehouse.
		2. **Primary Use Cases**
			1. Serving images or documents directly to a browser.
			2. Storing files for distributed access (e.g., software installation files).
			3. Streaming video and audio.
			4. Storing data for backup, restore, disaster recovery, and archiving.
			5. Hosting static websites.
		3. Types 
			1. **Block Blobs**
			2. **Append Blobs**
			3. **Page Blobs**
		4. **Access Tiers (Cost Optimization)**
			1. **Hot**
			2. **Cool**
			3. **Cold**
			4. **Archive**
		5. Uses **REST API (HTTPS)**
	2. Azure File Storage (Azure Files)
		1. **Analogy:** A fully managed shared network drive (like an S: drive in an office) in the cloud.
		2. Primary Use Cases
			1. **"Lift and Shift" Applications:** Migrating applications to the cloud that rely on traditional file shares for data.
			2. **Replacing On-Premises File Servers:** Use Azure Files as a cloud-based, maintenance-free replacement for your local NAS or file server.
			3. **Shared Development/Testing Environments:** Provide a central, shared location for tools and code that multiple developers or VMs need to access.
		3. **Standard Protocols:** The use of **SMB** and **NFS** is its defining feature. It requires no changes to applications that already use these protocols.
	3. Azure Disk Storage
		1. **Analogy:** The C: drive or D: drive for your cloud virtual machine.
		2. Primary Use Cases
			1. **OS Disk:** Every Azure VM has one attached operating system disk.
			2. **Data Disks:** Storing application data, databases, or any other data that needs to be persisted by a VM.
	4. Azure Data Lake Storage (**Gen2**)
		1. **Analogy:** A specialized, massive reservoir built to hold water (data) of all types, with high-speed intake pumps and output channels specifically designed for large-scale industrial processing (big data analytics).
		2. Primary Use Cases
			1. The foundational storage layer for building modern data platforms on Azure.
			2. Big data analytics using services like Azure Synapse Analytics, Azure Databricks, and Azure HDInsight.
			3. Machine learning and AI model training.
			4. Data warehousing and real-time analytics.
		3. **Hierarchical Namespace (HNS)**
		4. **Built on Blob Storage**
		5. **Optimized for Analytics**
		6. It Uses Hadoop Distributed File System (HDFS)
8. **Describe Analytical work load**
	1. Transactional systems
	2. Describe transactional workloads 
		1. Transactions
			1. Begin
			2. Commit or Rollback
		2. ACID
	3. Describe batch data
	4. Describe streaming data
	5. Describe the concepts of data processing
	6. Services
		1. Azure Data Factory
			1. ADF is a cloud-based **data integration and ETL/ELT service**. It automates the movement and transformation of data. You create "pipelines" which are logical workflows of activities.
			2. **Orchestration:** It can trigger other services to do work. For example, an ADF pipeline can move data into a data lake and then tell Azure Databricks to start a complex analysis job on that new data.
			3. **Connectors**
		2. SQL Server Integration Services (SSIS)
			1. SSIS is a traditional **ETL (Extract, Transform, Load)** tool that is part of the Microsoft SQL Server database software suite. It's primarily used for on-premises data integration. You build "packages" using a visual drag-and-drop interface. These packages can perform complex workflows, data cleansing, and transformations.
			2. While SSIS is traditionally on-premises, you can run your existing SSIS packages in the cloud using Azure Data Factory. This is called "lift and shift."
		3. Azure Data Lake
			1. Azure Data Lake Storage (specifically Gen2) is a highly scalable and cost-effective cloud storage repository. It's built on top of Azure Blob Storage but adds key features for big data analytics.
			2. **No Schema Required** - You can store data in its native, raw format without needing to structure it first. This is called "schema-on-read."
			3. **Hierarchical Namespace**
		4. Azure Databricks
			1. Azure Databricks is a premium, managed platform for **Apache Spark**. Spark is an open-source engine for large-scale data processing and machine learning. Databricks makes Spark easy to use, collaborative, and fast.
			2. **Collaborative Notebooks**
		5. Azure Synapse Analytics
			1. Synapse Analytics is an integrated analytics platform that brings together **data warehousing, big data processing, and data integration** into a single, unified service. Its goal is to be a one-stop-shop for all enterprise analytics needs.
			2. **Synapse SQL:** Offers both **Dedicated Pools** (pre-provisioned resources for high-performance, predictable data warehouse queries) and **Serverless Pools** (pay-per-query engine for exploring data in the data lake).
			3. **Synapse Spark:** Provides a managed Apache Spark environment (like Databricks) for big data engineering and data science.
			4. **Synapse Pipelines:** Incorporates the functionality of Azure Data Factory for data movement and orchestration.
			5. **Synapse Studio:** A single web UI to manage and use all these components.
		6. Azure Analysis Services
			1. AAS is a Platform-as-a-Service (PaaS) offering that provides a **semantic modeling layer** for business intelligence. You create "tabular models" in memory. These models contain pre-calculated aggregations, business logic, and hierarchies.
			2. **Semantic Layer:** It translates complex data tables into simple business terms like "Total Sales," "YoY Growth," and "Products."
			3. **In-Memory Cache:** It holds the data and calculations in memory (RAM), which makes querying incredibly fast.
			4. **The BI Middleman:** It sits between your data warehouse (like Synapse) and your reporting tool (like Power BI or Excel) to guarantee high performance and a "single version of the truth."
		7. Azure HDInsight
			1. HDInsight is a managed cloud service that makes it easier to deploy and manage clusters of popular **open-source big data frameworks**. It's for organizations that are heavily invested in the open-source Hadoop ecosystem.
			2. If Databricks is a sleek, modern science lab where everything is provided, HDInsight is a **"Do-It-Yourself" big data toolkit**.
			3. **Frameworks:** You can spin up clusters for Hadoop (MapReduce), Spark, Hive (for SQL queries on Hadoop), Kafka (for real-time streaming), HBase (a NoSQL database), and more.
			4. **Control & Flexibility:** It gives you more fine-grained control over the environment compared to more abstracted services like Databricks or Synapse.
		8. Microsoft Fabric
			1. Microsoft Fabric is a SaaS (Software-as-a-Service) all-in-one analytics solution that integrates all the different data roles and functions into one product. It combines the capabilities of Data Factory, Synapse, and Power BI.
			2. **OneLake:** A single, unified, logical data lake for the entire organization. Data is stored once in OneLake and can be used by all the different "experiences" (engines) without duplication.
			3. **DirectLake Mode:** A groundbreaking feature in Power BI that allows it to query data directly from OneLake at in-memory speeds, without having to import or cache the data first.
	7. Power BI
	8. Types Of Analysis
		1. Descriptive- Its goal is to summarize historical data to provide a clear and concise picture of the past. It's the "rearview mirror" of analytics, telling you what has already occurred.
		2. Diagnostic - - Once you know what happened, you want to understand the root cause. Diagnostic analysis involves drilling down into the data to find dependencies and identify patterns.
		3. Predictive - Predictive analysis uses historical data, statistical algorithms, and machine learning techniques to identify the likelihood of future outcomes. It’s about forecasting, not just guessing.
		4. Prescriptive - This is the most advanced form of traditional analysis. It goes beyond predicting a future outcome and actually recommends specific actions to take to achieve a desired goal or mitigate a future risk.
		5. Cognitive - Cognitive analysis is a "next generation" of analytics that aims to mimic human thought processes. It combines various AI technologies, including machine learning, deep learning, and natural language processing (NLP), to understand context, ambiguity, and learn from new information.
	9. **Database Locks**
		1. A database lock is a **signal** or a **marker** that a transaction places on a piece of data (like a row, a page, or a whole table). This lock tells other transactions what they can and cannot do with that data until the lock is released.
9. **Encryption**
	1. **Transport Layer Security (TLS)**
	2. **Transparent Data Encryption (TDE)**
10. **Real Time Data Processing**
	1. Data Ingestion (The Entry Point)
		1. **Azure Event Hubs**
		2. **Azure IoT Hub**
	2. Stream Processing (The "Brain")
		1. **Azure Stream Analytics (ASA)**
		2. **Azure Functions**
		3. **Azure Databricks**
		4. **Azure Synapse Analytics**
	3. Data Storage & Serving (The Destination)
		1. **Hot Path**
			1. **Azure Cosmos DB**
			2. **Azure SQL Database**
			3. **Azure Cache for Redis**
		2. **Cold Path**
			4. **Azure Data Lake Storage (ADLS) Gen2**








