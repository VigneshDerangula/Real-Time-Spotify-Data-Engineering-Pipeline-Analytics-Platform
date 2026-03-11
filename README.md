🎧 Spotify Modern Data Stack Project
Snowflake DBT Apache Airflow Apache Kafka Python Docker Power BI Modern Data Stack

📌 Project Overview
This project demonstrates an end-to-end real-time data engineering pipeline for Spotify music analytics using the Modern Data Stack (MDS).
We simulate streaming music data — including song plays, listeners, regions, and device types — and build a fully automated pipeline from data ingestion to visualization.

Once the pipeline starts, every component runs automatically:
data simulation → streaming via Kafka → storage in Snowflake → transformation with DBT → visualization in Power BI.

👉 Think of it as a real-world Spotify analytics system built on top of cutting-edge data tools.

🏗️ Architecture
Architectur
Pipeline Flow:

Data Simulator → Generates fake Spotify streaming data (user, track, region, device).
Kafka Producer → Streams the data to Kafka topics in real time.
Kafka Consumer → Consumes and stores the raw data into MinIO (S3-compatible storage).
Airflow → Orchestrates data loading from MinIO → Snowflake (Bronze).
Snowflake → Stores and manages data in Bronze → Silver → Gold layers.
DBT → Cleans, transforms, and builds analytics-ready models directly inside Snowflake.
Power BI → Connects to the Snowflake Gold tables for interactive dashboards and insights.
⚡ Tech Stack
Python (Faker) → Data simulation
Apache Kafka → Real-time data streaming
MinIO → Object storage (S3-compatible)
Snowflake → Cloud data warehouse
DBT → Transformations, tests, and models
Apache Airflow → Orchestration and DAG scheduling
Power BI → Business intelligence dashboard
Docker & docker-compose → Containerized environment
✅ Key Features
Fully automated pipeline — end-to-end from ingestion to insights
Real-time streaming using Kafka
Medallion Architecture (Bronze → Silver → Gold) implemented in Snowflake
DBT for transformation and testing (clean, modular SQL models)
Power BI dashboard showing region-wise plays, song trends, and listener insights
Containerized deployment for reproducibility
CI/CD pipeline with dbt test automation
📂 Repository Structure
spotify-mds-pipeline/
├── docker/ # DAGs for orchestration
│   ├── .env
│   ├── docker-compose.yml
│   └── dags/
│       ├── minio-to-kafka.py
│       └── .env
├── spotify_dbt/
│   └── models/
│       ├── gold/
│       ├── silver/
│       └── sources.yml
├── simulator/
│   ├── producer.py
│   └── .env
├── consumer/
│   ├── kafka-to-minio.py
│   └── .env
├── docker-compose.yml
├── requirements.txt
└── README.md
⚙️ Step-by-Step Implementation
1. Data Simulation
Generated fake Spotify streaming data using Python + Faker.
Data fields: user_id, track_name, artist, region, device_type, timestamp, duration.
Simulated a continuous stream of song plays.
2. Kafka Streaming
Used Kafka Producer to send data into Kafka topics in real-time.
Each message represents a song play event.
Kafka Consumer stores these events as raw JSON files in MinIO.
3. Airflow Orchestration
DAG 1: Loads raw data from MinIO → Snowflake Bronze tables.
DAG 2: Triggers DBT transformation runs to build Silver and Gold models.
4. Snowflake Data Warehouse
Bronze Layer: Raw data ingested directly from MinIO.
Silver Layer: Cleaned and standardized data.
Gold Layer: Aggregated insights such as:
Top artists
Most-streamed regions
Device usage
5. DBT Transformations
Staging models: Clean column names, handle nulls, standardize timestamps.
Marts:
Facts: plays, listeners
Dimensions: tracks, artists, devices, regions
Automated tests and documentation via:
dbt test
dbt docs generate
6. Visualization in Power BI
Connected directly to Snowflake Gold layer.
Built interactive visuals:
🎵 Top Artists / Songs by Plays
🌎 Regional Heatmap (U.S. States)
📈 Trends Over Time (Line Chart)
💽 Device-Type Distribution (Donut Chart)
dashboard (2)
📊 Final Deliverables
Real-time Spotify data streaming pipeline
Clean Snowflake Medallion Architecture (Bronze → Silver → Gold)
DBT transformation project (staging, marts, gold)
Automated orchestration via Airflow
Interactive Power BI dashboard
🧠 Concepts Covered
Real-time data ingestion (Kafka)
Medallion architecture (Bronze → Silver → Gold)
Data modeling with DBT
Data warehousing in Snowflake
Workflow orchestration with Airflow
Visualization with Power BI
