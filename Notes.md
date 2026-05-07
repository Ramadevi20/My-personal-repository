
## Course Overview: Introduction to Big Data Systems


## Chapter 1
**Instructor:** Shry Parick, Data Architect (10+ years experience, 13+ Cloud Certifications)

This course is designed for the **Data Architect Nanodegree**, focusing on the strategic and architectural side of big data rather than just the engineering/coding aspects.

---

### 1. The Role of a Big Data Architect
The course distinguishes between two primary roles:
*   **Big Data Engineer:** Focuses on writing code, implementation, and managing the back-end infrastructure (Hadoop, orchestration, etc.).
*   **Big Data Architect:** Acts as a **bridge** between business leadership and the engineering team. Responsibilities include:
    *   Understanding business requirements and proposing solutions.
    *   Assessing risks and comparing tools.
    *   **Soft Skills:** Articulating complex technical solutions to non-technical stakeholders.

---

### 2. What is Big Data?
Big Data is defined not as a single technology, but as a field for extracting information from datasets too complex for traditional software.
*   **Scale:** Involves processing data in **terabytes and petabytes**.
*   **Examples:** Every minute, social media generates millions of video views, hundreds of thousands of tweets, and over 500,000 comments.
*   **Value:** Leads to cost reduction (e.g., Cloud/Hadoop storage), faster decision-making, and the creation of new products.

---

### 3. Implementation Strategy: When to Use Big Data
| **Use Big Data If...** | **Avoid Big Data If...** |
| :--- | :--- |
| Data is in terabytes/petabytes. | Data is in megabytes/gigabytes. |
| Existing hardware is at its limit. | Data fits on a single computer. |
| You need to break organizational silos. | No immediate need for complex insights. |
| You expect exponential growth soon. | Data volume is static and small. |

---

### 4. Course Curriculum
The course is divided into five lessons and a final project:
*   **Lesson 1:** Characteristics, business value, and the 10,000-foot ecosystem view.
*   **Lesson 2:** Deep dive into storage and processing frameworks (Ingestion, Scale).
*   **Lesson 3:** **NoSQL** vs. Relational databases; data modeling for NoSQL.
*   **Lesson 4:** **Data Lakes** in the Cloud; design patterns and benefits.
*   **Final Project:** A real-world scenario for a medical processing company. You will research, propose, and justify an end-to-end Data Lake solution to company leadership.

---

### 5. History & Evolution
*   **1950s:** Basic analytics (spreadsheets).
*   **2003:** Google publishes the seminal Big Data research paper.
*   **2006:** Yahoo releases **Hadoop** (Open Source).
*   **2014:** **Apache Spark** enters the market, consolidating tools.
*   **2020:** Spark 3.0 provides 2x performance improvements over previous versions.

---

### 6. Tools & Prerequisites
*   **AWS Account:** Requires Root or Administrator access.
*   **Technical Skills:** Refresh **Shell/Command Line** skills.
    *   *Mac/Linux:* Use Terminal.
    *   *Windows:* Download PuTTY or similar shell software.
*   **Learning Style:** The course is highly hands-on with quizzes, demonstrations, and repetitive exercises to ensure concept absorption.




## CHapter 2

This transcript provides a comprehensive introduction to Big Data, the Hadoop ecosystem, and the practical application of these technologies in the enterprise world.

## 1. Introduction to Big Data
Big Data allows organizations to analyze massive datasets to uncover patterns, improve customer experience, and increase profitability.

### The 4 Vs of Big Data
A dataset is categorized as "Big Data" based on four primary characteristics:
* **Volume**: The sheer size of the data (terabytes or petabytes).
* **Velocity**: The speed at which data is generated and moves (e.g., social media feeds).
* **Variety**: Different types of data, including structured, semi-structured, and unstructured.
* **Veracity**: The quality and trustworthiness of the data.

### Scaling Mechanisms
To handle increasing data, systems must scale using one of two methods:
1. **Vertical Scaling**: Increasing the capacity (RAM, CPU) of a single existing server.
    * **Pros**: Easy to manage, lower licensing costs for small groups.
    * **Cons**: Limited by physical hardware limits; creates a single point of failure.
2. **Horizontal Scaling**: Adding more servers to a cluster to distribute the load.
    * **Pros**: Theoretically infinite scale and better fault tolerance (if one node fails, the system stays up).
    * **Cons**: Higher architectural complexity and increased cooling/space requirements.

---

## 2. The Big Data Ecosystem
The Big Data ecosystem is a collection of independent open-source tools that perform specific tasks and work together to build analytic solutions.

### Core Components
* **Hadoop Distributed File System (HDFS)**: The distributed storage layer. It breaks files into blocks (default 128 MB) and replicates them across multiple nodes.
* **YARN (Yet Another Resource Negotiator)**: Manages cluster resources and schedules jobs, allowing multiple engines like Spark and MapReduce to run on the same cluster.

### Data Ingestion Tools
* **Sqoop**: Transfers structured data between relational databases and Hadoop.
* **Flume**: Collects and moves large amounts of log data using a source-channel-sink architecture.
* **Kafka**: A high-performance, real-time event streaming platform.

### Data Processing Tools
* **MapReduce**: A programming model that processes data in three stages: Map, Shuffle & Sort, and Reduce.
* **Apache Pig**: A high-level scripting language used to simplify MapReduce development.
* **Apache Hive**: Provides a SQL-like interface (HiveQL) to query data stored in HDFS.
* **Apache Spark**: A unified analytics engine that is up to 100 times faster than MapReduce due to in-memory processing.
* **HBase**: A NoSQL database that provides real-time, random read/write access to billions of rows.



---

## 3. Security and Operations
* **Apache Ranger**: Provides centralized security administration and fine-grained authorization.
* **Apache Knox**: A gateway for providing secure access to Hadoop services via REST APIs.
* **Apache Atlas**: A governance tool for metadata management and data lineage tracking.
* **Apache Zookeeper**: Provides highly reliable distributed coordination and synchronization.
* **Apache Airflow**: A platform to programmatically author, schedule, and monitor workflows.
* **Apache Ambari**: A web-based tool for provisioning, managing, and monitoring Hadoop clusters.

---

## 4. Real-World Applications & Industry Roles
Big Data is utilized across various sectors:
* **Healthcare**: Creating 360-degree patient views and identifying growth markets.
* **Finance**: Detecting credit card fraud and money laundering.
* **Transportation**: Ride-sharing companies use data to analyze usage patterns and optimize service focus.

### Engineering Roles
While skill sets overlap, the focus differs between roles:
* **Big Data Engineer**: Focuses on data cleaning, ETL (Extract, Transform, Load), and pipeline orchestration.
* **AI/ML Engineer**: Focuses on feature engineering, model building, and data visualization.

---

## 5. Practical Lab: Amazon EMR
The course utilizes **Amazon EMR (Elastic MapReduce)**, a managed Hadoop framework in the cloud. 
* **Provisioning**: A cluster typically takes about 15 minutes to provision.
* **Connectivity**: Users connect to the Master Node via SSH using a `.pem` key pair.
* **Cost Management**: Billing is per-minute; clusters should be terminated after use to stop charges.



## CHapter 3
These notes provide a comprehensive technical overview of the Hadoop ecosystem, focusing on storage, ingestion, processing, and resource management based on the provided transcript[cite: 1].

---

## 1. Storage: HDFS (Hadoop Distributed File System)
HDFS is a highly fault-tolerant, scalable distributed file system designed for inexpensive commodity hardware.

### Architecture
HDFS uses a master/slave architecture:
* **NameNode (Master Node):** Stores metadata (file names, block locations) but never the actual data.
* **DataNodes (Slave Nodes/Chunkservers):** Store the actual data in fixed-size blocks (default 128 MB in Hadoop 2.x).
* **Replication:** Hadoop maintains **three copies** of every block across different nodes to ensure data integrity and fault tolerance.

### Read and Write Algorithms
* **Read:** The client asks the NameNode for block locations and connects to the **closest** healthy DataNode to retrieve the data.
* **Write:** The client sends data to the DataNodes (never through the master). A "two-phase commit" protocol ensures all three replicas are successfully written before the operation is acknowledged.



---

## 2. Data Ingestion Tools
Ingestion tools move data from various sources into the Hadoop cluster for storage and analytics.

| Tool | Primary Use Case | Key Features |
| :--- | :--- | :--- |
| **Apache Sqoop** | Relational Databases (RDBMS) | Supports **Import** (RDBMS to HDFS) and **Export** (HDFS to RDBMS). Uses Map-only jobs (no reducers). |
| **Apache Kafka** | Real-time / Streaming Data | High-scale event streaming for IoT, sensors, and logs. Uses a **Producer/Consumer** API. |

*Note: Other tools include Apache NiFi, AWS Kinesis, and Google Cloud Pub/Sub.*

---

## 3. Distributed Data Processing
Hadoop achieves distributed processing by dividing large problems into smaller tasks executed independently across the cluster.

### MapReduce Framework
MapReduce works through three primary phases:
1. **Map Phase:** Data is read locally (Data Locality) and converted into **key-value pairs**.
2. **Shuffle and Sort:** The framework automatically groups all records with the same key. This often involves high network traffic.
3. **Reduce Phase:** Aggregates the grouped data to produce the final result.

**Combiner:** An optional "mini-reducer" that runs locally on mapper nodes to aggregate data *before* it is shuffled, significantly reducing network congestion.

### Ecosystem Processing Tools
* **Apache Pig:** Uses a script-based language (Pig Latin) for data transformation. It uses "lazy execution," meaning the job only runs when a `STORE` or `DUMP` command is issued.
* **Apache Hive:** Provides a SQL-like interface (HQL) for users with SQL skills.
    * **Metastore:** Stores table schemas in an RDBMS.
    * **Managed vs. External Tables:** Deleting a managed table removes both metadata and HDFS data; deleting an external table removes only the metadata.
    * **Partitioning:** Improves performance by organizing data into sub-directories (e.g., by borough or date), allowing Hive to skip irrelevant data during queries.

### Apache Spark
Spark is **10–100x faster** than MapReduce because it processes data in **RAM** rather than writing intermediate results to disk.
* **RDD (Resilient Distributed Dataset):** The core abstraction in Spark—an immutable, distributed collection of records.
* **Operations:** 
    * **Transformations:** (e.g., `filter`, `map`) are lazy and create a logical plan.
    * **Actions:** (e.g., `collect`, `count`) trigger the actual physical execution.
* **DataFrames:** A newer, recommended API that organizes data into a table-like structure, optimized by the **Catalyst Optimizer**.

---

## 4. Resource Management: YARN
**YARN** (Yet Another Resource Negotiator) acts as the "operating system" for the Hadoop cluster.

* **Resource Manager (Master):** Consists of a **Scheduler** (allocates resources based on capacity/constraints) and an **Application Manager**.
* **Node Manager (Slave):** An agent on every DataNode that monitors CPU, memory, and disk usage.
* **Application Master:** A per-job container that negotiates resources with the Resource Manager and monitors task execution.


## CHapter 4

These notes provide a comprehensive overview of NoSQL databases, specifically focusing on Amazon DynamoDB, as discussed in the course transcript[cite: 1].

## 1. Overview of NoSQL and Big Data
The shift toward NoSQL databases was driven by the need to handle **petabyte-scale datasets** and build highly available, scalable systems. Traditional relational databases (RDBMS) were not designed for this level of scale. NoSQL databases provide:
* **High availability** and low-latency.
* **Horizontal scalability** at a reasonable cost.
* **Flexibility** in storing structured, semi-structured, or unstructured data.

## 2. Comparison: SQL vs. NoSQL
| Feature | SQL (RDBMS) | NoSQL |
| :--- | :--- | :--- |
| **Data Model** | Structured (Rows/Columns) | De-normalized; Document, Key-Value, Column, or Graph |
| **Schema** | Predefined and rigid | Schema-less / Schema evolution |
| **Scaling** | Vertical (Larger Servers) | Horizontal (More Nodes) |
| **Transactions** | ACID Guarantees | CAP Theorem |
| **Querying** | Complex (Joins/Subqueries) | Simple and efficient |

### Key Theoretical Principles
* **ACID (SQL):** Atomicity, Consistency, Isolation, and Durability.
* **CAP Theorem (NoSQL):** Consistency, Availability, and Partition-tolerance. The theorem states a distributed system can only achieve two of these three simultaneously.
    * **CA:** Consistent and Available (e.g., standard RDBMS).
    * **CP:** Consistent and Partition-tolerant (e.g., MongoDB, HBase).
    * **AP:** Available and Partition-tolerant (e.g., DynamoDB, Cassandra).

---

## 3. Amazon DynamoDB Core Concepts
DynamoDB is a fully managed, serverless NoSQL database.
* **Core Components:** Tables (collections of items), Items (records), and Attributes (fields/columns).
* **Size Limits:** Individual items cannot exceed **400 KB**.
* **Data Types:** Supports scalar values (strings, numbers) and nested attributes up to **32 levels deep**.

### Primary Keys
Every item must have a unique Primary Key.
1. **Simple Primary Key (Partition Key):** Uses a single attribute (Hash Attribute) to distribute data across partitions.
2. **Composite Primary Key:** Combines a **Partition Key** and a **Sort Key** (Range Key). This allows multiple items to share the same Partition Key if their Sort Keys are different, effectively modeling one-to-many relationships.

---

## 4. DynamoDB Operations and Throughput
### Capacity Modes
* **Provisioned Mode:** You specify Read Capacity Units (**RCU**) and Write Capacity Units (**WCU**). Best for predictable traffic.
    * **1 WCU:** 1 write per second for items up to 1 KB.
    * **1 RCU:** 1 strongly consistent read per second or 2 eventually consistent reads per second.
* **On-Demand Mode:** Flexible billing where you pay per request. Best for unpredictable workloads or new applications.

### Data Retrieval Mechanisms
* **GetItem:** Most efficient; requires the full primary key.
* **Query:** Finds items based on the Partition Key; can use Sort Key comparison operators.
* **Scan:** Scans the entire table; very expensive and should be avoided for large datasets.

---

## 5. Data Modeling Mindset
NoSQL modeling requires a "work backwards" approach.
* **Know Your Access Patterns:** Unlike SQL, where you normalize data first, in NoSQL, you must know exactly how the application will query the data before designing the schema.
* **Single Table Design:** Aim to maintain as few tables as possible.
* **Efficiency:** Optimize for the most frequent and high-volume queries (70-80% of use cases) to make them fast and inexpensive.




## Chapter 5


## Big Data Lake Architecture: Key Concepts and Design

A **Data Lake** is a centralized storage repository designed to house all of an enterprise's data—including structured, semi-structured, and unstructured formats—at a massive scale. It democratizes information by breaking down **data silos** and allowing teams to store data in its original raw format using a **schema-on-read** approach.

### Core Elements of a Data Lake
A successful implementation requires several integrated components:

* **Ingestion Tools**: Connectors like **Sqoop, Flume, Kafka, and NiFi** that load data from sources (databases, web servers, IoT) in real-time or batch.
* **Storage**: A scalable, cost-effective layer supporting diverse formats. Common solutions include **HDFS** for on-premise or **Amazon S3** for cloud-native builds.
* **Processing Tools**: Scalable engines such as **Spark, Hive, and MapReduce** used to transform and analyze data.
* **Orchestration**: Workflow managers like **Apache Oozie or Airflow** that coordinate the movement of data from raw layers to refined application layers.
* **Governance and Security**: Critical processes for managing data availability, integrity, and protection (encryption at rest/transit) while preventing unauthorized access.
* **Catalog and Discovery**: Metadata management and tagging that allow users to easily find, understand, and interpret datasets across the enterprise.

---

### Design Considerations and Best Practices
When building an enterprise-grade data lake, architects must address specific technical and organizational factors:

| Consideration | Key Focus Area |
| :--- | :--- |
| **Data Structure** | Planning for volume growth, efficient partitioning, and industry-standard file formats (e.g., **Parquet**) to optimize queries. |
| **Compliance** | Meeting regulatory requirements like **GDPR, CCPA, or FIPS**, and implementing data masking for personally identifiable information (PII). |
| **Network Design** | Determining accessibility (internal vs. API-exposed) to isolate critical data from potential security breaches. |
| **Decoupling** | Ensuring systems can work independently through buffering mechanisms (queuing) so one failure doesn't crash the entire pipeline. |
| **Automation** | Using **DevOps** to automate both application and infrastructure deployment to reduce errors and increase speed. |

---

### Challenges and the "Data Swamp" Risk
Without proper oversight, a data lake can turn into a **data swamp**—a repository where data is unusable because it cannot be found or trusted.

* **Security & Oversight**: Risks arise when data is ingested without privacy or regulatory review.
* **Data Lineage**: A lack of historical records on how data was modified by previous analysts makes it difficult to derive reliable insights.
* **Maintenance**: Data lakes can lose relevance over time if they lack semantic consistency or result in ungoverned chaos.

---

### Transactional Capabilities (ACID) in Data Lakes
Most data lakes are built on object storage (like S3), which traditionally struggles with transactional updates. Technologies like **Apache Hudi** (and others like **Delta Lake**) solve this by providing:

* **Change Data Capture (CDC)**: Capturing database transactions and replicating them to the lake without expensive full-dataset rewrites.
* **Right to be Forgotten**: Simplifying **GDPR deletions** by allowing specific records to be modified or removed without IO-intensive rewrites of petabytes of data.
* **Time Travel**: Enabling users to view how a dataset looked at a specific point in time by tracking lineage and metadata.
* **Views**: Hudi offers **Incremental Views** (changes since a specific time), **Read-Optimized Views** (full dataset as of last compaction), and **Real-Time Views** (including most recent changes).



# AWS NOtes


These notes are compiled from the provided transcripts and organized by the specific objectives and key domains of the AWS ecosystem as of 2025.


1. AWS Strategic Vision and Core Advantages
AWS provides a global cloud platform offering over 200 fully-featured services.


Strategic Themes: Businesses trade fixed expenses (CapEx) for variable expenses (OpEx), paying only for what they consume.


Scalability and Elasticity: Resources can grow or shrink automatically based on demand, ensuring high availability and cost efficiency.


Massive Economies of Scale: By aggregating usage from millions of customers, AWS achieves lower variable costs and passes these savings to users.


Global Reach: Organizations can deploy applications globally in minutes, reducing latency by placing resources closer to end users.


2. Global Infrastructure and Navigation
AWS operates a robust, distributed infrastructure designed for high availability.


Regions: Geographic areas housing multiple data centers (e.g., Northern Virginia, Mumbai). As of 2025, AWS spans 32 regions.


Availability Zones (AZs): Physically separate data centers within a region with independent power and cooling, connected via low-latency links.


Edge Locations: Small data centers used by Amazon CloudFront to cache content closer to users, drastically reducing latency.


Management Tools:

AWS Management Console: A web-based graphical interface to manage resources.


AWS CLI: A command-line tool for automating tasks and managing services via scripts.


3. Application Development and AI Platform Capabilities
Modern application development in AWS emphasizes serverless and managed architectures.


Compute Services:

Amazon EC2: Provides resizable virtual servers (instances) for full control.


AWS Lambda: A serverless "Function as a Service" (FaaS) that runs code in response to events (e.g., file uploads, API calls) without managing servers.


Containerization:

Amazon ECS and EKS: Managed orchestration for Docker and Kubernetes clusters.


Amazon ECR: A secure registry to store and manage container images.


AI and Machine Learning:

Amazon SageMaker: Simplifies building, training, and deploying ML models.


Amazon Bedrock: Focused on foundation models for generative AI.


Amazon Q: A generative AI-powered assistant for troubleshooting and guidance.


4. Data Platform and Modernization
AWS offers diverse database and storage options to meet specific workload needs.


Storage:

Amazon S3: Scalable object storage for unstructured data.


Amazon EBS: Block storage (virtual hard drives) for EC2 instances.


S3 Glacier: Low-cost archival storage for long-term data retention.


Databases:

Amazon RDS: Managed relational databases supporting MySQL, PostgreSQL, Oracle, and SQL Server.


Amazon Aurora: High-performance, cloud-native relational database (MySQL/PostgreSQL compatible) with a serverless v2 option.


Amazon DynamoDB: A serverless NoSQL database providing single-digit millisecond latency.


Amazon Neptune: A graph database for managing highly connected datasets and relationships.


5. Autonomous Security and Identity
Security is a shared responsibility: AWS secures the cloud infrastructure, while the customer secures their data in the cloud.


Identity and Access Management (IAM):

Users, Groups, and Roles: Control access based on the Principle of Least Privilege.


Cross-Account Roles: Allow secure access to resources in different AWS accounts without creating new users.


IAM Identity Center: Centralized single sign-on (SSO) for workforce access.


Autonomous Protection Services:

Amazon GuardDuty: Intelligent threat detection using machine learning.


Amazon Inspector: Automated vulnerability scanning for EC2, containers, and Lambda.


AWS Shield: DDoS protection (Standard is free; Advanced offers 24/7 expert support).


AWS WAF: Web Application Firewall to filter malicious web traffic.


6. Cost Optimization and Hybrid Deployment
AWS provides tools to ensure financial predictability and hybrid flexibility.


Cost Management:

AWS Budgets: Set custom spending targets and receive alerts when costs exceed thresholds.


AWS Cost Explorer: Visualize and forecast spending trends.


Right Sizing: The process of matching instance types and sizes to workload requirements to minimize costs.


Pricing Models:

On-Demand: Pay for what you use by the hour or second.


Reserved Instances/Savings Plans: Commit to a 1 or 3-year term for significant discounts (up to 72%).


Spot Instances: Use spare capacity for up to 90% savings (best for fault-tolerant tasks).


Hybrid Options:

AWS Outposts: Extends AWS infrastructure and services to on-premises data centers.


Direct Connect: Establishes a dedicated private network link from on-premises to AWS.


7. Strategic Frameworks
Well-Architected Framework: Six pillars (Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization, and Sustainability) provide a consistent set of best practices.


Cloud Adoption Framework (CAF): Groups capabilities into six perspectives (Business, People, Governance, Platform, Security, and Operations) to accelerate digital transformation.


Migration Strategies (7 Rs): Retire, Retain, Rehost (Lift-and-Shift), Relocate, Repurchase, Replatform, and Refactor (Re-architect).


8. Practical Resources
AWS Artifact: A self-service portal for accessing AWS's security and compliance reports (e.g., SOC, ISO).


Trusted Advisor: An automated tool that provides real-time guidance to help reduce costs, increase performance, and improve security.


AWS Free Tier: Allows users to explore services like EC2, S3, and RDS for free for 12 months or via always-free options (e.g., Lambda).

