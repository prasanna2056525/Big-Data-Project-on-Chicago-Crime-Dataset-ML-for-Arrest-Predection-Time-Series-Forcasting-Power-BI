# Big-Data-Project-on-Chicago-Crime-Dataset-ML-for-Arrest-Predection-Time-Series-Forcasting-Power-BI
A cloud-based platform on Azure analysed 8M+ Chicago crime records using XGBoost for arrest prediction and SARIMA for 12-month forecasting. Interactive Power BI dashboards and a Gradio app enabled real-time insights, demonstrating scalable, cost-effective big data analytics for smart city poli

























Big Data and Cloud Computing for Predictive Crime Analytics: Arrest Prediction, Time Series Forecasting, and Interactive Visualisation with Gradio Deployment for Smart City




















Abstract


The rapid expansion of digital technologies and smart city infrastructures has generated vast volumes of data across public safety domains. Law enforcement agencies require scalable, cost effective, and intelligent solutions to process, analyse, and derive actionable insights from millions of crime records. This report presents a cloud based big data analytics platform for the Chicago Crime Dataset (2001–2025), hosted on Microsoft Azure. The dataset, comprising over eight million structured crime incidents, was ingested into Azure Blob Storage, cleaned and preprocessed using Python/Pandas, and analysed through two machine learning pipelines: an XGBoost classifier to predict arrest likelihood, and a SARIMA time series model to forecast monthly crime volumes for the next 12 months. The analytical outputs were visualised in an interactive Power BI dashboard featuring temporal trends, and key performance indicators. Additionally, a Gradio web application was deployed to provide real time arrest probability predictions. The architecture addresses critical aspects of cloud computing, including scalability, redundancy, cost optimisation, security, and performance monitoring. The findings demonstrate that integrating big data processing, predictive modelling, and cloud based visualisation can significantly enhance data driven decision making in smart city policing.


Keywords: Big Data, Cloud Computing, Microsoft Azure, Crime Analytics, Arrest Prediction, XGBoost, Time Series Forecasting, SARIMA, Power BI, Smart City, Gradio.















Table of Contents
Abstract	4
Introduction	6
Objectives	7
Section 1: Data Ingestion and Storage	7
1.1 Types and Sources of Data	7
1.2 Proposed Cloud-Based Storage Solution	9
1.3 Data Ingestion Process	10
Section 2: Scalable Processing Architecture	14
2.1 Proposed Scalable Big Data Processing Architecture	14
2.2 Choice of Cloud Services for Distributed Computing and Parallel Processing	15
2.3 Accommodating Growing Data Volumes	16
Section 3: Data Extraction and Pre-processing	18
3.1 Selection of Dataset for Extraction and Analysis	18
3.2 Data Extraction Process	18
3.3 Data Pre-processing	20
Section 4: Data Analysis & Insights	25
4.1 Implementation of a Cloud Based Analytics Solution	25
4.2 Examples of Analytical Queries or Machine Learning Algorithms	34
4.3 Contribution to Informed Decision Making	35
Section 5: Cost Optimization Strategies	36
Section 6: Security and Compliance	39
6.1 Security Measures and Compliance Considerations	39
6.2 Access Control Mechanisms and Encryption Practices	41
Section 7:  Performance Monitoring and Management	44
7.1 Strategies for Performance Monitoring and Troubleshooting	44
7.2 Tools and Services for System Management and Monitoring	46
Section 8: Conclusion, Limitations and Future Work	47
8.1 Conclusion	47
8.2 Limitations	47
8.3 Future Work	47
References	48
Appendix	50









































Introduction

The rapid digitalisation of urban environments has generated vast, multidimensional datasets across public safety, transport, and healthcare. Law enforcement agencies now routinely collect millions of crime records, including temporal, geospatial, and categorical attributes. Analysing such data can uncover hidden crime patterns, identify high risk areas, and support proactive resource allocation. However, traditional on premises systems are often constrained by limited storage, processing bottlenecks, and poor scalability (Kumar & Singh, 2022).
Cloud computing offers a scalable, cost effective alternative. Platforms such as Microsoft Azure provide elastic storage, on demand compute, and integrated analytics services. This project leverages Azure to design and implement an end to end big data pipeline for the Chicago Crime Dataset (2001–2025) – a publicly available CSV containing over eight million crime incidents (Chicago Open Data Portal, 2025). The dataset exhibits high volume (>2GB), variety (categorical, temporal, spatial), and historical velocity, making it ideal for big data analytics.
After ingestion into Azure Blob Storage, the data was cleaned using Python and Pandas. Two predictive models were built: an XGBoost classifier to predict arrest likelihood (Prasad & Patil, 2024), and a SARIMA time series model to forecast monthly crime volumes for the next 12 months (Kumar & Singh, 2022). Analytical outputs are visualised in an interactive Power BI dashboard, and a Gradio web application provides real time arrest predictions. This report critically evaluates cloud cost optimisation, security, compliance, and performance monitoring, demonstrating how big data and cloud computing can enhance smart city policing.
Objectives

•	Design a scalable cloud storage architecture using Azure Blob Storage with geo redundancy (GRS) and cost effective tiering (Hot, Cool, Archive).
•	Preprocess and clean the raw Chicago Crime Dataset (handle missing values, inconsistent text, duplicates, invalid coordinates) using Python and Pandas on Azure ML notebook.
•	Train an XGBoost classifier to predict arrest likelihood, optimising F1 score on imbalanced test data.
•	Build a SARIMA model to forecast monthly crime counts for the next 12 months, evaluated with MAE and RMSE.
•	Create an interactive   Power BI dashboard visualising crime trends and patterns.
•	Deploy a Gradio web application providing real time arrest probability predictions.
•	Evaluate cost optimisation, security, compliance, and performance monitoring within Microsoft Azure using native tools.


Section 1: Data Ingestion and Storage

1.1 Types and Sources of Data

Modern organizations and smart city systems generate large volumes of data from multiple digital sources. These datasets are generally classified into structured, semi-structured, and unstructured data based on their format and organization (Khan et al., 2021).
Structured data refers to highly organized data stored in rows and columns, making it easier to process and analyse using databases and analytical tools. Examples include banking transactions, healthcare records, customer databases, and crime reports. Semi-structured data contains metadata and tags that provide partial organization, such as JSON files, XML documents, and API responses. In contrast, unstructured data does not follow a predefined schema and includes images, videos, social media posts, emails, and audio files (Hashem et al., 2015).
Big data environments collect information from several sources including IoT devices, government databases, enterprise applications, sensor networks, web platforms, and social media systems. These continuously growing datasets require scalable cloud infrastructure for efficient storage and processing (Microsoft Azure, 2024).
For this assessment, the selected dataset is the Chicago Crime Dataset (2001–2025), obtained from the Chicago Open Data Portal. The dataset contains millions of crime records reported across different districts of Chicago and the dataset is available in CSV format and exceeds 2GB in size, making it suitable for cloud-based big data analytics. It includes attributes such as:
•	primary_type (type of crime: theft, battery, assault, etc.)
•	arrest (a binary flag indicating whether an arrest was made)
•	date (timestamp of the incident)
•	block (block level address for location privacy)
•	police district, ward and community area (geographic administrative divisions)
•	latitude and longitude (geocoordinates for mapping)
•	case number (a unique identifier)
•	IUCR (Illinois Uniform Crime Reporting code)
•	description and location_description (a textual description of the incident and the type of location where it occurred, e.g. “street”, “apartment”, “school”)
The dataset demonstrates key characteristics of big data including:
•	Volume due to the large number of records, 
•	Variety through numerical, categorical, and geospatial data, 
•	Velocity because crime data is accumulated continuously over multiple years, 
•	and Value by supporting crime trend analysis and predictive analytics. (Ali, O. and Kaur, 2025)


 
Figure 1: Chicago Crime Dataset Overview

 
Figure 2: Chicago Open Data Portal

1.2 Proposed Cloud-Based Storage Solution

Cloud-based storage solutions play a critical role in managing large-scale datasets by providing scalability, redundancy, high availability, and cost-efficient resource management. Major cloud providers such as Amazon Web Services (AWS), Google Cloud Platform (GCP), and Microsoft Azure offer storage services suitable for big data applications (Marinescu, 2017).

Cloud Provider	Storage Service	Advantages	Limitations
AWS	Amazon S3	Highly scalable and strong analytics ecosystem	Complex configuration for beginners
Google Cloud	Google Cloud Storage	Strong AI and analytics integration	Higher operational costs in some services
Microsoft Azure	Azure Blob Storage	Easy integration, scalable, secure, and cost-effective	Slightly lower market adoption than AWS
Table 1: Cloud Provider & their Advantages

For this assessment, Microsoft Azure was selected because it provides an integrated cloud ecosystem that supports storage, analytics, machine learning, and visualization within a single platform. An Azure Resource Group named rg-chicagocrime-analytics was created to manage all cloud resources centrally. The Chicago Crime Dataset was stored in an Azure Storage Account named stchicagocrime01 using Azure Blob Storage containers:
•	raw-data (Stores the original, unprocessed CSV file)
•	processed-data (Holds cleaned and transformed data (Parquet/CSV) after preprocessing)
•	outputs (Contains machine learning model files, forecast results, and analysis outputs)
Azure Blob Storage was selected because it supports scalable object storage capable of handling large datasets efficiently. The platform allows storage resources to expand dynamically as data volume increases, making it suitable for long-term crime data management (Microsoft, 2024).
To ensure redundancy and reliability, Azure provides replication mechanisms such as:
•	Locally Redundant Storage (LRS) 
•	Geo-Redundant Storage (GRS) 
These features create multiple copies of the data to improve availability and disaster recovery capabilities.
From a cost-effectiveness perspective, Azure follows a pay-as-you-go pricing model, which reduces unnecessary infrastructure expenses. Azure also provides multiple storage tiers including Hot, Cool, and Archive storage, (Microsoft,2025) enabling historical datasets to be stored at lower operational costs.
Overall, Microsoft Azure was considered the most suitable cloud platform due to its scalability, redundancy mechanisms, integrated security, and seamless compatibility with machine learning and analytics services used throughout this assessment.

1.3 Data Ingestion Process

The data ingestion process was implemented to enable secure and efficient transfer of the Chicago Crime Dataset into the Microsoft Azure cloud environment for storage and analytics. The workflow involved multiple stages including resource configuration, cloud storage setup, dataset upload, and cloud accessibility.

Step 1: Creation of Azure Resource Group
The ingestion process began with the creation of an Azure Resource Group named rg-chicagocrime-analytics. The Resource Group was used to centrally manage all Azure services and cloud resources associated with the assessment.
 
 
Figure 3: Azure Resource Group Configuration
This figure illustrates the Azure Resource Group created to manage storage, virtual machines, and analytics services within a centralized cloud environment.

Step 2: Creation of Azure Storage Account
After configuring the Resource Group, an Azure Storage Account named stchicagocrime was created to provide scalable cloud storage infrastructure for the Chicago Crime Dataset.
 
Figure 4: Azure Storage Account Configuration

This figure presents the Azure Storage Account configuration used for storing the Chicago Crime Dataset with Locally Redundant Storage (LRS) enabled.

Step 3: Configuration of Blob Storage Containers
Blob Storage containers were created within the Storage Account to organize the dataset and analytical outputs efficiently. Separate containers were configured for:
•	raw-data 
•	processed-data 
•	outputs 
This structure improved data organization, scalability, and accessibility throughout the analytics workflow.
 
Figure 5: Azure Blob Storage Containers
This figure shows the Blob Storage containers configured for managing raw datasets, processed files, and analytical outputs within Azure Blob Storage.

Step 4: Uploading Dataset to Azure Blob Storage
The Chicago Crime Dataset (2001–2025) was downloaded from the Chicago Open Data Portal in CSV format and uploaded into the raw-data container using the Azure Portal upload interface.
Azure Blob Storage was selected because it supports efficient transfer and storage of large datasets while ensuring high availability and cloud scalability.
 
Figure 6: Dataset Upload to Blob Storage raw Container
This figure illustrates the process of uploading the Chicago Crime Dataset into the Azure Blob Storage container using the Azure Portal.

Step 5: Seamless Data Transfer and Accessibility
Azure Blob Storage enabled seamless data transfer between the local environment and the cloud platform through secure cloud connectivity and centralized storage management. The uploaded dataset became directly accessible from other Azure services without requiring additional manual transfer processes.
The cloud-based storage environment also improved accessibility, scalability, and integration across the analytics workflow while ensuring secure storage and efficient resource management.

After the ingestion process was completed, the uploaded dataset was accessed through Azure Machine Learning and the Azure Virtual Machine environment for preprocessing, analytics, and visualization tasks.














Section 2: Scalable Processing Architecture

2.1 Proposed Scalable Big Data Processing Architecture

A scalable cloud-based processing architecture was designed using Microsoft Azure services to support efficient storage, processing, analytics, and visualization of the Chicago Crime Dataset (2001–2025). The architecture was developed to provide centralized resource management, flexible compute resources, and scalable storage capabilities suitable for large-scale analytical workloads.

 
Figure 7: Proposed Azure-Based Big Data Processing Architecture
The workflow begins with the ingestion of the crime dataset into Azure Blob Storage, which acts as the primary cloud storage layer. The storage environment was organized using separate Blob containers for raw datasets, processed files, and analytical outputs to improve data organization and workflow efficiency.
An Azure Virtual Machine named vm-chicagocrime was deployed to provide a dedicated cloud-based analytics environment. Python and Jupyter Notebook were used within the VM to perform preprocessing, machine learning, and visualization operations on the uploaded dataset.
Azure Machine Learning Workspace was integrated to support model development and cloud-based experimentation, while Power BI was connected to the processed datasets to generate interactive dashboards and crime trend visualizations. In addition, a Gradio interface was deployed to provide web-based access to predictive analytics outputs.
The architecture also incorporates Azure monitoring and security services including Azure Monitor, Role-Based Access Control (RBAC), and Network Security Groups (NSG) to support secure and manageable cloud operations.
Overall, the proposed architecture provides a scalable and integrated cloud computing framework capable of supporting large-scale crime data analytics and machine learning applications (Microsoft Azure, 2024).

2.2 Choice of Cloud Services for Distributed Computing and Parallel Processing

The selection of cloud services is a critical factor in designing scalable big data architectures capable of supporting distributed computing and parallel data processing. Microsoft Azure was selected for this assessment because it provides integrated cloud services that support scalable storage, cloud-based computation, machine learning, and analytical processing within a centralized environment (Microsoft Azure, 2024).
Azure Blob Storage was used as the primary cloud storage service for managing the Chicago Crime Dataset. The service supports scalable object storage and enables centralized access to large datasets across multiple cloud resources. Blob Storage improves distributed computing by allowing different cloud services to access and process the same dataset simultaneously without requiring local data duplication.
For computational processing, an Azure Virtual Machine named vm-chicagocrime01 was deployed to provide cloud-based processing resources for data analytics and machine learning tasks. The VM configuration included:
•	2 vCPUs 
•	14 GB RAM 
•	28 GB storage 
Distributed computing was achieved by separating storage, processing, analytics, and visualization into independent cloud components that interact through the Azure cloud environment. This modular architecture improves flexibility, resource accessibility, and workload management across the system.
Parallel processing was supported through the multi-core virtual machine environment, where multiple analytical operations could execute simultaneously across different CPU cores. This improved processing efficiency during tasks such as data cleaning, transformation, feature engineering, and machine learning model training on millions of crime records. Parallel execution reduced processing time and improved computational performance when handling large datasets (Khan et al., 2021).
Azure Machine Learning Workspace was also integrated to support cloud-based machine learning workflows and centralized experiment management. The service enabled efficient model development, evaluation, and resource integration within the Azure ecosystem.


Azure Service	Purpose	Contribution
Azure Blob Storage	Cloud-based dataset storage	Enables centralized and distributed data accessibility
Azure Virtual Machine	Cloud computing environment	Supports parallel execution using multi-core processing
Azure Machine Learning Workspace	Machine learning workflow management	Provides scalable analytical experimentation
Azure Monitor	Resource and performance monitoring	Tracks system performance and resource utilization
RBAC & NSG	Security and access control	Protects cloud resources and manages secure access

Table 2: Cloud Services Supporting Distributed and Parallel Processing

 
Figure 8: Azure Cloud Services for Distributed and Parallel Processing
This figure illustrates the Microsoft Azure cloud services configured to support distributed computing, parallel data processing, cloud storage, and machine learning operations within the proposed architecture.

2.3 Accommodating Growing Data Volumes

The proposed cloud architecture was designed to efficiently accommodate growing data volumes through scalable storage infrastructure, flexible computing resources, and modular cloud service integration. Since the Chicago Crime Dataset contains millions of records, the architecture must support increasing storage and analytical requirements over time.
Azure Blob Storage provides dynamic scalability, allowing storage capacity to expand automatically without requiring physical hardware upgrades. This enables the architecture to efficiently manage continuously growing datasets while maintaining high availability and accessibility across the cloud environment (Microsoft Azure, 2024).
The storage environment was also organized using separate Blob containers for raw data, processed data, and analytical outputs. This modular storage structure improves data management, simplifies workflow organization, and supports future expansion as additional datasets or analytical outputs are generated.
To accommodate increasing computational workloads, the Azure Virtual Machine can be vertically scaled by increasing CPU, memory, and storage resources whenever additional processing power is required. This flexibility enables the architecture to adapt to larger datasets, more complex analytical tasks, and future machine learning workloads without redesigning the overall infrastructure.
The architecture also supports future scalability through integrated Azure services. Additional cloud resources such as storage accounts, virtual machines, monitoring tools, or machine learning services can be incorporated into the existing environment with minimal configuration changes. This modular cloud design improves long-term flexibility and operational efficiency.
Furthermore, Microsoft Azure provides cost optimization features including:
•	pay-as-you-go pricing, 
•	flexible storage tiers, 
•	and resource monitoring services. 
These features help maintain operational efficiency while supporting continuous growth in data storage and processing requirements.
                              
                 Figure 9: Azure Storage Scalability and Resource Monitoring
This figure illustrates the scalability and monitoring capabilities of Microsoft Azure used to manage increasing storage capacity and cloud resource utilization within the proposed architecture.

Section 3: Data Extraction and Pre-processing

3.1 Selection of Dataset for Extraction and Analysis

The dataset selected for extraction and analysis is the Chicago Crime Dataset (2001–2025), publicly available from the Chicago Open Data Portal (Chicago Data Portal, 2025). This dataset directly aligns with the project objectives: to demonstrate a cloud based big data pipeline for smart city public safety. It contains over 8 million records (structured CSV format) and 22 attributes, including temporal (date, year, hour), geospatial (latitude, longitude, district), categorical (crime type, location description), and boolean (arrest, domestic) fields.
The dataset is particularly suitable because:
•	It exhibits high volume (>2 GB), requiring scalable cloud storage and processing.
•	Its variety of data types enables both machine learning (arrest prediction) and time series forecasting (monthly crime counts).
•	Its historical velocity (daily updates) and value (actionable public safety insights) match the assessment’s focus on real world big data challenges (Enterprise Big Data Framework, 2020).
Thus, the selection demonstrates adeptness in choosing a pertinent, non trivial dataset that supports all subsequent analytical stages.
 
Figure 10: Dataset Shape and Attributes of Chicago Crime Dataset

3.2 Data Extraction Process

The data extraction process involved collecting, transferring, and preparing the Chicago Crime Dataset for cloud-based analytics within the Microsoft Azure environment. The extraction workflow began by storing the dataset within the raw-data Blob container created inside the Azure Storage Account. Azure Blob Storage enabled secure and scalable storage of the dataset while supporting seamless accessibility across the cloud environment.
Python and Jupyter Notebook were used within the Azure Virtual Machine environment to access and extract the dataset directly from Azure Blob Storage. The Pandas library was used to load and manipulate the dataset efficiently for preprocessing and analytical operations.
Several transformations were applied during the extraction stage to improve data consistency and analytical usability. These transformations included:
•	converting date columns into datetime format, 
•	selecting relevant analytical attributes, 
•	renaming columns for readability, 
•	filtering unnecessary records, 
•	and standardizing categorical values. 
These transformations improved dataset quality and prepared the data for preprocessing and machine learning tasks.
The extraction process also ensured centralized accessibility because the dataset remained stored within Azure Blob Storage while being accessed directly from the cloud-based analytical environment. This reduced manual data transfer operations and improved workflow efficiency throughout the project (Microsoft Azure, 2024).	   
Tool / Service	Purpose
Azure Blob Storage	Centralized cloud-based dataset storage
Azure Virtual Machine	Cloud processing environment
Python	Data extraction and transformation
Jupyter Notebook	Interactive analytics environment
Pandas Library	Dataset loading and manipulation

Table 3: Data Extraction Tools and Transformations
 
Figure 11: Dataset Extraction in Jupyter Notebook
This figure illustrates the extraction of the Chicago Crime Dataset from Azure Blob Storage into the Jupyter Notebook analytical environment using Python.






3.3 Data Pre-processing

Data preprocessing was performed to improve dataset quality, consistency, and analytical accuracy before applying machine learning and visualization techniques. Since the Chicago Crime Dataset contains millions of records collected over multiple years, preprocessing was necessary to remove inconsistencies and prepare the data for efficient analysis. Several preprocessing operations were applied using Python and the Pandas library within the Jupyter Notebook environment. The pre-processing steps are:
Initial Summary of Dataset: Checking missing value and shape in dataset 
 

Standardise column names: Converted all column names to lower case and replaced spaces with underscores (e.g., Primary Type → primary type). This ensures error free referencing in code.
 
Drop entirely empty rows/columns:Removed rows and columns that were completely null (dropna(how='all')). This eliminates noise and reduces memory footprint.
 
Handle missing critical fields: Dropped rows where date, primary_type, or arrest were missing, as these are essential for analysis (Prasad & Patil, 2024).
  
Convert arrest and domestic to Boolean: Mapped string values ('true'/'false') to Python bool. This enables direct use in ML algorithms.
 

Parse date/time and extract features: Converted date string to datetime using the explicit format '%m/%d/%Y %I:%M:%S %p' (fast, 5 10× speed gain). Extracted year, month, day_of_week, and hour as new integer columns. This enables temporal aggregations and seasonality analysis (Kumar & Singh, 2022).
 

Filter years 2001–2025: Kept only records with year between 2001 and 2025, discarding any outliers (e.g., future dates).
 
Standardise text fields: Applied str.upper() and str.strip() to categorical columns (primary_type, location_description, etc.). This unifies categories (e.g., “Theft” vs “THEFT”) for accurate grouping.
 
Clean geographic coordinates: Kept only rows where latitude and longitude are within Chicago’s bounding box (41.6–42.1, -87.9–-87.5) or null. Invalid values were set to NaN and later imputed by district median.
 
Remove duplicate records: Dropped duplicates based on case_number (if available) or a combination of date, block, and primary_type.
 
Convert to categorical types: Changed low cardinality columns (district, beat, ward, fbi_code) to category dtype, reducing memory usage by ~40%.
 
Add derived feature: violent crime flag: Created is_violent = True if primary_type in predefined list (HOMICIDE, ASSAULT, BATTERY, ROBBERY, etc.). This binary feature improves interpretability of arrest predictions.
 
Final Check for Missing values:
	 
This figure presents the remaining missing values identified after the data cleaning process. The results indicate that most attributes contain a very low percentage of missing data, particularly geographical fields such as latitude and longitude with approximately 1.14% missing values. Although the community_area and ward columns still contain around 7% missing data, these attributes were retained because they were not critical for the main predictive analysis. Overall, the dataset quality remained suitable for preprocessing, machine learning, and visualization tasks after cleaning operations were completed.
Save cleaned data: Exported as both CSV (for compatibility) and Parquet (compressed, faster loading) – Crime_dataset_cleaned.parquet.
 
All pre processing steps were documented in a Jupyter notebook and re run on the full dataset. The final cleaned DataFrame contains no missing values in critical columns, consistent data types, and derived temporal/spatial features ready for EDA, ML, and forecasting.






















Section 4: Data Analysis & Insights

4.1 Implementation of a Cloud Based Analytics Solution

The cloud based analytics solution was implemented on Microsoft Azure using a decoupled architecture: storage (Azure Blob), compute (Azure VM), visualisation (Power BI), and deployment (Gradio). Below are the six implementation steps that I used:
Step 1: Data Preparation & Feature Engineering
•	Load the cleaned dataset (Crime_dataset_cleaned.parquet) from Azure Blob into a Pandas DataFrame on the    Azure VM.
•	Extract year, month, day_of_week, hour from the date_parsed column.
•	Create a binary flag is_violent using a predefined list (e.g., Homicide, Assault, Battery, Robbery).
•	Encode categorical variables (district, ward, community_area, primary_type, location_description) using LabelEncoder
 
Figure 12: Code snippet for extracting hour and is_violent.
 
Figure 13: Python cell showing df.shape and df.columns after feature engineering.

Step 2: Exploratory Data Analysis (EDA) (Shah, R. et al. ,2025)
•	Compute summary statistics (mean, median, standard deviation) for numeric features and (count, top, unique, freq) for categoricial features.
 
 
•	Create visualisations including yearly and monthly crime trend charts, hourly and day-of-week bar plots, district-wise crime and arrest rate maps, crime type distribution bar charts, arrest vs non-arrest breakdowns, violent vs non-violent crime comparisons, and a correlation heatmap.
 
Figure 14: Crime Trend by Year (2001-2025)
 
Figure 15: Crime Incidents by Month

 
Figure 16: Top 10 Police Districts by Crime Volume

 
Figure 17: Top 15 Crime Types

 
Figure 18: Arrest Rate by Crime Type (Top 15)

 
Figure 19: Correlation Analysis

Final EDA Summary:
 
Step 3: Arrest Prediction with XGBoost

An XGBoost classifier was employed to predict arrest probability. Stratified splitting preserved the arrest class ratio (Zhang et al., 2025). Hyperparameters were tuned via grid search with 3 fold cross validation, optimising F1 score. The final test performance yielded a recall of 0.59, indicating the model captures 59% of actual arrests, which is suitable for a decision support system in policing (Jha & Verbert, 2024). Feature importance analysis ranked  primary_type, is_violent and location_description as the top three predictors.
 
Figure 20: XGBOOST ML Model Implementation

 
Figure 21: ROC curve with AUC value.
 
Figure 22: Feature importance bar chart (top 10)

Step 4: Crime Trend Forecasting with SARIMA
Monthly crime counts were aggregated, revealing a strong seasonal pattern with period 12. Auto ARIMA selection identified a SARIMA(1,1,1)(1,1,1,12) model as optimal, balancing goodness of fit and parsimony (Li & Zhang, 2024). The model produced a 12 month forecast for 2026, validated on 2025 data with an MAE of 1,167 crimes – well below 10% of the average monthly volume, confirming its reliability for operational planning (Kozlov & Chen, 2025).
 
Figure 23: Time series plot of monthly counts (2001–2025).
 
Figure 24: Forecast plot (historical + 2026 forecast)

			                         
Figure 25: Table of monthly forecast values for year 2026

Step 5: Interactive Dashboard with Power BI
Power BI was directly connected to the ‘processed data’ container in Azure Blob Storage, enabling live data access (Microsoft, 2025). The dashboard incorporates seven interactive visuals. A year slicer provides dynamic filtering, allowing stakeholders to drill into specific periods. The dashboard was published to the Power BI Service, facilitating secure sharing with department leadership. (SJPD, 2024)
 
Figure 26: Power BI “Get Data” window showing Azure Blob connection.
 
Figure 27: Full dashboard view in Power BI

 
Figure 28: Dashboard visual filtered for a specific period from 2010-2020

 Step 6: Real Time Deployment with Gradio

The final XGBoost model was deployed as an interactive web application using Gradio, a Python framework for rapid ML deployment (Gradio, 2025). The interface accepts all ten input features and returns an arrest probability in real time. By setting share=True, a public link valid for 1 week is generated, allowing non technical users to test scenarios without coding. This bridges the gap between model development and operational use.
 
Figure 29: Gradio interface code snippet

 
Figure 30: Terminal output showing the public shareable link.


 
Figure 31: Screenshot of the web interface & Example prediction output (“Arrest Likely – 11.5%”)

4.2 Examples of Analytical Queries or Machine Learning Algorithms

Example 1: Analytical Query – “Weekend Theft Arrest Rate in District 5”

 

Insight Extracted: The arrest rate for this scenario was 12.3%, significantly lower than the overall theft arrest rate (18.7%). This indicates a potential policing gap during late weekend hours in District 5.

Example 2: Machine Learning – XGBoost for Arrest Prediction
As detailed in Step 3 above, the XGBoost classifier achieved an F1 score of 0.72 and a recall of 0.59. Feature importance analysis revealed that  primary_type, is_violent and location_description are the most influential predictors (Jha & Verbert, 2024).
Example 3: Time Series – SARIMA for Monthly Crime Forecasting
As detailed in Step 4 above, The SARIMA model forecasted 12 month crime totals for 2026. Validation on 2025 data gave an MAE of 1,167 crimes, demonstrating sufficient accuracy for operational planning (Kozlov & Chen, 2025).
4.3 Contribution to Informed Decision Making

The analytics solution directly supports three levels of decision making within a public safety enterprise (e.g., Chicago Police Department or a smart city command centre).
Level	Decision	Analytics Output	Business Impact
Tactical (daily/weekly)	Patrol allocation by hour and district	Heatmap of crime by hour/day; district arrest rates	Officers can be redeployed to high crime, low arrest districts during peak hours (e.g., 10 PM 2 AM in District 5).
Operational (monthly/quarterly)	Resource planning for seasonal spikes	SARIMA forecast (2026 monthly predictions)	The forecast predicts a summer peak (June–August) of ~22,000 crimes/month. Commanders can schedule overtime and increase patrols three months in advance.
Strategic (yearly)	Predictive policing and technology investment	XGBoost feature importance (hour, crime type, district)	Insights guide investments in real time surveillance during high impact hours (e.g., 10 PM 2 AM) and specialised training for high priority crime types (e.g., battery, robbery).
Table 4: Decision & Business Impact

Furthermore, the Gradio web app enables officers in the field to input crime details and obtain an arrest probability before responding. For example, if the model predicts a low arrest probability for a given location and time, the dispatcher can send additional units or request nearby CCTV assistance – a proactive strategy The Power BI dashboard serves as a centralised intelligence hub, replacing static reports with interactive drill‑downs. Decision‑makers can filter by district, crime type, or time period to investigate anomalies (e.g., why District 8’s arrest rate dropped by 15% in March). This self‑service analytics reduces dependency on IT and accelerates insight‑to‑action cycles.
Finally, the forecasting capability supports budget planning. Knowing that crime is projected to increase by 3% in 2026 compared to 2025 (based on forecasted annual total), the department can justify a proportional increase in patrol hours and technology spending. Conversely, if forecasted crime decreases, resources could be reallocated to community outreach – demonstrating data‑driven agility.
Innovative business strategy proposed: Integrate the arrest prediction model with the Computer‑Aided Dispatch (CAD) system. When a 911 call is received, the system would automatically compute an arrest probability based on real‑time location, time, and call type (converted to primary_type). If the probability is below a threshold (e.g., 20%), the dispatcher is alerted to collect additional information or dispatch a community service officer instead of a full patrol unit – optimising high‑cost resources.  

Section 5: Cost Optimization Strategies

Efficient cost management is an important consideration in cloud-based big data analytics because large-scale storage and computational resources can significantly increase operational expenses over time. For this assessment, several cost optimization strategies were implemented within the Microsoft Azure environment to reduce storage and processing costs while maintaining analytical performance and scalability.
Step 1: Selection of Cost-Effective Storage Redundancy
Azure Blob Storage was configured using Locally Redundant Storage (LRS) instead of Geo-Redundant Storage (GRS). LRS was selected because it maintains multiple copies of the data within a single Azure region while offering lower operational costs compared to geographically replicated storage solutions.
Since the project dataset did not require global replication or enterprise-level disaster recovery, LRS provided a cost-effective balance between data durability and affordability (Microsoft Azure, 2024).
 
Figure 32: Azure Storage Redundancy Configuration
Step 2: Utilization of Cost-Effective Storage Tiers
Azure Blob Storage supports multiple storage tiers including:
•	Hot Tier 
•	Cool Tier 
•	Archive Tier 
For this assessment, frequently accessed datasets were stored within the Hot storage tier to support analytics and machine learning operations, while historical and infrequently accessed files could be moved to Cool or Archive storage tiers to reduce long-term storage expenses.
This tiered storage strategy improves cost optimization by aligning storage costs with data access frequency.
 
Figure 33: Azure Blob Storage Tiers
Step 3: Optimizing Resource Utilization
To reduce computational costs, a low-cost Azure Virtual Machine named vm-chicagocrime was selected for analytical processing. The VM configuration included:
•	2 vCPUs 
•	14 GB RAM 
•	28 GB storage 
This configuration provided sufficient computational resources for preprocessing, analytics, and machine learning tasks while minimizing unnecessary infrastructure expenses.
Resource utilization was further optimized by running the VM only during analytical operations and stopping the instance when not in use. This approach reduced compute charges associated with continuous VM operation.
 
Figure 34: Azure Virtual Machine Configuration
Step 4: Monitoring and Cost Management
Azure monitoring and cost management services were used to track cloud resource usage and operational expenses. Azure Cost Management enables monitoring of storage consumption, virtual machine usage, and resource utilization across the cloud environment.
This monitoring process helps identify unnecessary resource consumption and supports better allocation of cloud resources for long-term cost efficiency.
 
Figure 35: Azure Cost Management Dashboard

Step 5: Reserved Instance Consideration
Microsoft Azure also provides Reserved Instance (Microsoft, 2025) pricing options that allow long-term cloud resources to be purchased at reduced pricing compared to pay-as-you-go models. Although Reserved Instances were not implemented in this assessment due to the short-term academic nature of the project, they would be beneficial for enterprise-level deployments requiring continuous analytical workloads.
Reserved Instances can significantly reduce long-term computational expenses for organizations processing large-scale datasets regularly (Marinescu, 2017).

Overall, the implemented cost optimization strategies improved storage efficiency, minimized unnecessary computational expenses, and supported scalable cloud analytics within a cost-effective Microsoft Azure environment.









Section 6: Security and Compliance

6.1 Security Measures and Compliance Considerations

To ensure the confidentiality, integrity, and protection of the Chicago Crime Dataset within the Microsoft Azure environment, several security measures were implemented during the project workflow.

Securing Cloud Storage
The Chicago Crime Dataset was stored within Azure Blob Storage, which provided centralized and secure cloud-based storage for managing large-scale datasets. The storage account was configured using secure access settings to reduce unauthorized access risks.
Azure Blob Storage also supports built-in redundancy and secure cloud accessibility throughout the analytical workflow.
 
Figure 36: Azure Blob Storage Security Configuration
This figure illustrates the security configuration of Azure Storage Account used to securely manage the uploaded dataset.

Implementing Network Security
Network Security Groups (NSG) were configured to protect the Azure Virtual Machine from unauthorized network access. NSGs control inbound and outbound traffic by applying security rules to the cloud environment.
This security mechanism reduced exposure to unauthorized remote connections and improved protection of the analytical environment.

 
Figure 37: Network Security Group Configuration
This figure presents the Network Security Group rules configured to secure the Azure Virtual Machine environment.

Maintaining Data Integrity
Azure Blob Storage was configured using Locally Redundant Storage (LRS), which automatically maintains multiple copies of the dataset within a single Azure region. This replication mechanism improves data durability and reduces the risk of accidental data loss or corruption.
Azure Monitor was also used to track resource activity and monitor the cloud environment for unusual behaviour.
 
Figure 38: Azure Monitoring and Data Integrity Management
This figure illustrates Azure monitoring services used to maintain data integrity and monitor cloud resource activities.

Compliance Considerations
Although the Chicago Crime Dataset is publicly available, compliance considerations remain important when handling large-scale datasets within cloud environments. Organizations operating in regulated sectors such as healthcare, finance, or government industries must comply with data protection regulations including:
•	GDPR, 
•	ISO 27001, 
•	and organizational security policies. 
Microsoft Azure supports compliance management through built-in security frameworks, monitoring services, and identity management controls (Microsoft Azure, 2024).

 
Figure 39: Azure Compliance and Security Standards
This figure presents Microsoft Azure compliance and security management capabilities for supporting regulated cloud environments.

Overall, the implemented security measures improved confidentiality, integrity, monitoring, and secure cloud operations throughout the project environment.

6.2 Access Control Mechanisms and Encryption Practices

Access control and encryption (Microsoft,2025) are important security practices for protecting cloud-stored datasets and analytical resources. For this assessment, Microsoft Azure security services were used to implement controlled access and secure data management within the cloud environment.
Role-Based Access Control (RBAC) was implemented to manage permissions across Azure resources. RBAC restricts unauthorized access by assigning users specific roles and permissions based on operational responsibilities. This approach improves security by ensuring that only authorized users can access storage resources, virtual machines, and analytical services.
The Azure Virtual Machine environment was also protected using authentication credentials and restricted network access through Network Security Groups. These controls reduce exposure to unauthorized remote access attempts.
Microsoft Azure additionally provides encryption mechanisms to protect stored and transmitted data. Azure Blob Storage automatically applies server-side encryption using Microsoft-managed encryption keys to secure stored datasets. Encryption protects the confidentiality of data by preventing unauthorized users from reading stored information.
Data transmitted between Azure services is also secured using encrypted communication protocols such as SAS HTTPS, which improves protection during cloud-based data transfer operations. For stronger enterprise-level security, organizations can additionally implement:
•	Multi-Factor Authentication (MFA), 
•	private endpoints, 
•	customer-managed encryption keys, 
•	and advanced identity management policies. 
These security mechanisms improve secure cloud operations and support protection of analytical resources and datasets within scalable cloud environments (Marinescu, 2017).

 
Figure 40: SAS key Generation for cloud-based data transfer

 
Figure 41: Azure Access Control of Storage Account
This figure presents the access control configurations implemented within Microsoft Azure to protect cloud resources and stored datasets.






















Section 7:  Performance Monitoring and Management

7.1 Strategies for Performance Monitoring and Troubleshooting

Efficient performance monitoring is important in cloud-based big data environments to ensure stable processing, resource optimization, and smooth analytical operations. For this assessment, several monitoring and management strategies were implemented within the Microsoft Azure environment to track system performance and identify potential processing bottlenecks during analytics and machine learning operations.

Monitoring Virtual Machine Performance
The Azure Virtual Machine used for analytics was continuously monitored to evaluate CPU utilization, memory consumption, disk usage, and network activity during preprocessing and machine learning operations.
Monitoring these resources helped identify performance limitations when processing large volumes of crime data and ensured that the VM operated efficiently throughout the analytical workflow.
 
Figure 42: Azure Virtual Machine Performance Metrics
This figure illustrates the monitoring of CPU, memory, and resource utilization within the Azure Virtual Machine environment.

Monitoring Storage Performance
Azure Blob Storage performance was monitored to evaluate storage usage, data accessibility, and transaction activity during dataset retrieval and processing operations.
Monitoring storage performance ensured that large datasets could be accessed efficiently without causing delays in analytical operations.



 
Figure 43: Azure Blob Storage Monitoring
This figure presents the monitoring of Azure Blob Storage usage and storage activity during cloud-based analytical processing.

 Monitoring System Activity and Alerts
Azure Monitor was used to track cloud resource activities and generate performance insights across the analytical environment. Monitoring services help identify unusual resource consumption, processing delays, or operational failures within the cloud system.
Alert mechanisms can also be configured within Azure Monitor to notify administrators when resource usage exceeds predefined thresholds.
 
Figure 44: Azure Monitor Dashboard
This figure presents the Azure Monitor dashboard used for monitoring cloud resource performance and system activities.
Overall, these monitoring and troubleshooting strategies improved system reliability, optimized resource utilization, and reduced processing inefficiencies within the cloud-based analytical environment.
7.2 Tools and Services for System Management and Monitoring

Microsoft Azure offers a suite of integrated monitoring and management services that facilitate effective administration of cloud based big data ecosystems. These tools ( ManageEngine,2025) enhance visibility, resource governance, system optimisation, and operational dependability across the entire analytical pipeline.
For this assessment, Azure Monitor served as the central monitoring service. It enables real time tracking of resource utilisation, system performance, storage operations, and virtual machine metrics within the Azure environment. Additionally, Azure Monitor supports alert configuration and performance visualisation, allowing rapid identification of operational anomalies (Microsoft Azure, 2024).
Virtual Machine monitoring features were employed to assess CPU load, memory usage, and disk activity during data preprocessing and machine learning tasks. These capabilities helped sustain consistent processing performance when handling the large scale Chicago Crime Dataset.
Azure Storage monitoring services were also leveraged to track storage capacity, transaction volumes, and dataset accessibility in Azure Blob Storage. This improved transparency into storage operations and supported efficient management of cloud resident datasets.
Furthermore, Azure Cost Management tools enabled monitoring of cloud resource consumption and operational expenditures. This facilitated better resource optimisation and cost efficient management of analytical workloads.
Finally, the combination of Role Based Access Control (RBAC) and Azure Monitor enhanced centralised cloud administration by enabling secure resource management and performance oversight across the entire cloud environment.

Tool / Service	Purpose
Azure Monitor	Tracks system performance and resource usage
VM Monitoring Metrics	Monitors CPU, memory, and disk activity
Azure Storage Metrics	Tracks storage usage and transactions
Azure Cost Management	Monitors cloud operational costs
RBAC	Controls resource access and administration

Table 5: Azure Monitoring and Management Tools







Section 8: Conclusion, Limitations and Future Work

8.1 Conclusion

This assessment successfully implemented a cloud based big data analytics solution for the Chicago Crime Dataset using Microsoft Azure. Services such as Azure Blob Storage, Virtual Machine, Machine Learning Workspace, and Power BI were integrated to support scalable storage, preprocessing, analytics, visualisation, and predictive modelling. The project demonstrated how cloud computing enables efficient handling of large scale datasets through scalability, cost effective resource use, and centralised management. Preprocessing, machine learning (XGBoost, SARIMA), and security controls (RBAC, encryption) produced actionable insights into crime trends, arrest patterns, temporal distributions, and hotspots. Interactive dashboards and real time Gradio predictions further enhanced decision making. Overall, the work proves that Microsoft Azure can effectively support scalable big data analytics in a smart city context.

8.2 Limitations

Several constraints were identified. The low cost Azure VM configuration (2 vCPUs, 14 GB RAM) may struggle with larger datasets or more complex ML workloads. The analysis was limited to historical data (2001–2025); real time streaming was not implemented. Missing values in some attributes required extensive preprocessing, and the ML models focused on basic predictive analytics due to time and computational scope.

8.3 Future Work

Future enhancements could include real time data streaming and automated pipelines using advanced Azure services for continuous crime monitoring. More sophisticated ML and deep learning algorithms could improve prediction accuracy. Additional cloud resources and distributed processing (e.g., Azure Databricks) would enhance scalability. Integration with Geographic Information Systems (GIS), advanced dashboards, and automated alert systems would enable real time spatial crime analysis and intelligent decision support. The proposed architecture provides a solid foundation for scalable smart city analytics.









References

Ali, O. and Kaur, R. (2025). ‘Beyond the hype: navigating the 4 VIPs of big data for sustainable agriculture’, Journal of Plant Biochemistry and Biotechnology.

Chicago Data Portal (2025). Chicago Crime Dataset – 2001 to present. Available at: https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-Present/ijzp-q8t2 (Accessed: 3 May 2026).
Note: Also cited as Chicago Open Data Portal (2025) – treat as the same source.

Enterprise Big Data Framework (2020). Big Data Characteristics: Volume, Variety, Velocity, Value. Available at: https://www.bigdataframework.org (Accessed: 1 May 2026).

Gradio (2025). Build and share delightful machine learning apps, all in Python. Available at: https://github.com/gradio-app/gradio (Accessed: 15 May 2026).

Hashem, I.A.T., Yaqoob, I., Anuar, N.B., Mokhtar, S., Gani, A. and Khan, S.U. (2015). ‘The rise of “big data” on cloud computing: review and open research issues’, Information Systems, 47, pp. 98–115.

Jha, R. and Verbert, K. (2024). ‘Beyond GridSearchCV: advanced hyperparameter tuning strategies for scikit learn models’, Machine Learning, 113(4), pp. 2151–2179.

Khan, N., Al-Yasiri, A. and Kaur, R. (2021). ‘Cloud computing for big data analytics: a survey of techniques and challenges’, International Journal of Cloud Computing, 10(3), pp. 235–260.

Kozlov, A. and Chen, Y. (2025). ‘Hybrid of deep learning and exponential smoothing for enhancing crime forecasting accuracy’, Neural Computing and Applications, 37(2), pp. 845–862.

Kumar, R. and Singh, S. (2022). ‘Time series forecasting of crime patterns using SARIMA models’, Journal of Big Data, 9(1), 45.

Li, D. and Zhang, H. (2024). ‘SARIMA GRU crime prediction model based on BP neural network nonlinear combination’, Journal of Computational Science, 78, 102376.

ManageEngine (2025). ‘Monitoring Azure VM performance using Azure Monitor: Optimize VM performance with advanced tools’. ManageEngine Blogs. Available at: https://www.manageengine.com/ca/products/applications_manager/blog/how-to-monitor-azure-vm-performance.html (Accessed: 17 May 2026).

Marinescu, D.C. (2017). Cloud Computing: Theory and Practice. 2nd edn. Cambridge, MA: Morgan Kaufmann.

Microsoft (2025). Azure Blob Storage documentation. Microsoft Learn. Available at: https://learn.microsoft.com/en-us/azure/storage/blobs/ (Accessed: 10 May 2026).

Microsoft (2025). ‘Optimize Azure costs with reserved instances’. Microsoft Learn. Available at: https://learn.microsoft.com/en-us/shows/azure-essentials-show/optimize-azure-costs-with-reserved-instances (Accessed: 17 May 2026).

Microsoft (2025). ‘Access tiers for blob data – Azure Storage’. Microsoft Learn. Available at: https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-overview (Accessed: 10 May 2026).

Microsoft Azure (2024). Azure security and compliance. Available at: https://azure.microsoft.com/en-gb/explore/security-compliance/ (Accessed: 17 May 2026).

Microsoft (2025). ‘Encryption at rest – Azure security’. Microsoft Learn. Available at: https://learn.microsoft.com/en-us/azure/security/fundamentals/encryption-atrest. (Accessed: 18 May 2026).

Prasad, S. and Patil, S. (2024). ‘XGBoost for imbalanced crime data: predicting arrest outcomes’, Data Science Journal, 21(3), pp. 210–225.

San Jose Police Department (2024). ‘SJPD launches new council district crime stats dashboard’. City of San José. Available at: https://www.sjpd.org/Home/Components/News/News/2044/262 (Accessed: 12 May 2026).

Shah, R. et al. (2025). ‘Exploratory data analysis, time series analysis, crime type prediction, and trend forecasting in crime data using machine learning, deep learning, and statistical methods’, Neural Computing and Applications, 37, pp. 11773–11798.

Zhang, S., Li, X. and Wang, F. (2025). ‘Cybercrime incident and arrest prediction model through time series analysis: prediction of trends and patterns’, Journal of Information Processing Systems, 21(1), pp. 55–73





Appendix

 
Figure 45:  Crime Incidents by Day

This figure illustrates crime incidents by day and it is found that Friday has maximum crime incident and Sunday has low crime incidents.

 
Figure 46: Crime Incidents by Hour of Day
This figure illustrates that the crime is peaked at midnight and low at morning 5 am.



 
Figure 47: Heatmap showing Crime Intensity
The heatmap illustrates that crime volume varies significantly across police districts and hours, with peak intensities observed in specific districts during late evening and early morning hours. Darker regions indicate higher crime counts, highlighting temporal and spatial hotspots for targeted policing.
 
Figure 48: Pie-chart Showing Violent and Non-Violent Crime

The pie chart shows that non-violent crimes account for 69.2% of all incidents, while violent crimes represent 30.8%. This indicates that the majority of reported crimes are non-violent, though a substantial minority involve violence.

 
Figure Name: Arrest Rate by Hour of Day
The line chart demonstrates that arrest rates fluctuate significantly across different hours, with notably lower rates during late night and early morning hours (approximately 0–5). Peak arrest rates occur during midday and early evening, suggesting higher police effectiveness or different crime characteristics during these periods.

Dataset link: https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-Present/ijzp-q8t2/about_data
