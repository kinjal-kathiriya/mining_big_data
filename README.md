## 1. Introduction and Objectives 
The increase in urban crimes over the years has necessitated the use of big data and machine learning techniques to extract meaningful patterns and predict future incidents. This project focuses on analyzing the large-scale Chicago crime dataset using a distributed computing pipeline built with Apache Spark and AWS services. The goal is to uncover crime patterns based on location and time, predict arrests, and provide insights through clustering. By leveraging Spark MLlib and AWS Athena, the project builds a scalable and cost-effective analytics pipeline for public safety insights. 


## 2. Dataset Overview 
The dataset used is the 'Crimes - 2001 to Present' from the Chicago Data Portal. It contains over 7 million records 
(approximately 1.7GB), including attributes like crime type, location, arrest flag, date/time, and description. The dataset spans more than two decades, making it ideal for analyzing trends. After downloading the dataset, it was uploaded to Amazon S3 and registered in Athena for SQL-based queries and feature extraction. 


## 3. Data Preprocessing and Transformation 
Using PySpark on an EMR cluster, we processed and transformed the data by: 
-	Filtering out null or missing essential fields. 
-	Deriving new features from the date such as month, day of week, and hour. 
-	Converting text-based categorical fields into indexed numerical columns using StringIndexer. 
-	Binning latitude and longitude to form crime zones. 
 
The processed data was stored back into S3 and queried efficiently from Athena using SQL. 


## 4. Machine Learning Model Development 
Two ML models were developed using Spark MLlib: 
-	Random Forest Classifier : predicted whether a crime results in an arrest using features like primary type, location, and timebased attributes. 
-	KMeans Clustering : grouped crimes based on spatial and temporal attributes to find high-risk zones and time periods. 
 
Hyperparameters were optimized using CrossValidator and ParamGridBuilder, and models were evaluated using accuracy, F1 score, and silhouette scores. 


## 5. Evaluation and Results 
The Random Forest classifier achieved: 
-	Accuracy: 85% 
-	Precision: 82% 
-	Recall: 79% 
-	F1 Score: 80.5% 
 
KMeans clustering yielded meaningful clusters showing different crime hotspots by time of day and type. Silhouette scores indicated good separation between clusters, especially for clusters aligned with late-night downtown activity. 


## 6. Architecture Diagrams 
Core data processing pipline  

![image](https://github.com/user-attachments/assets/575fc7c6-0245-4630-9c03-b3856747c555)


Full Architecture with Orchestration 

<img width="168" alt="image" src="https://github.com/user-attachments/assets/9f2a7a23-3d24-4899-b094-109c2037060a" />


illustrates an extended architecture that includes automation, orchestration, and monitoring: 

<img width="227" alt="image" src="https://github.com/user-attachments/assets/ad61dc69-37f6-44f4-940c-776930c4f613" />

Orchestrated Architecture with AWS Step Functions and CloudWatch 


## 7. Key Visualizations this is a heatmap showing hourly crime density across all days. 

<img width="247" alt="image" src="https://github.com/user-attachments/assets/aa4bf187-2994-4bfe-b351-1b10f1a402ed" />


## 8. Challenges and Solutions 
Processing over 7 million records posed scalability challenges. EMR with PySpark enabled parallel transformation and modeling. Integrating Athena required precise schema design. Model tuning was compute-intensive, which was resolved through batch processing and grid-based parameter testing. Handling location noise was improved through geospatial binning. 



## 9. Conclusion and Future Work 
This project demonstrated a full-scale big data pipeline for analyzing and predicting crime in Chicago using Spark and AWS. Both supervised and unsupervised models yielded insights useful for strategic deployment of resources. Future enhancements include real-time dashboards, deeper geospatial analytics, and integration of external datasets like weather, demographics, or events. 


## 10. Additional Visual Insights 

<img width="239" alt="image" src="https://github.com/user-attachments/assets/e7d77f4c-cd50-4392-8a0d-287ba854b5c7" />


<img width="218" alt="image" src="https://github.com/user-attachments/assets/36a79a2a-e6a5-46a0-a923-a15d0849b6cf" />







