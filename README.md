Real-Time Ride Booking Data Engineering Pipeline

A real-time data engineering project built on Microsoft Azure to simulate how ride-booking events can be ingested, processed, transformed, and served for analytics.

The project focuses on understanding real-time streaming, event-driven architecture, and stream processing with PySpark.

🚀 Project Overview

The pipeline simulates ride-booking events such as:

Ride Requested
Driver Assigned
Ride Started
Ride Completed
Ride Cancelled

These events are generated through an API and continuously streamed into Azure Event Hubs.

Azure Databricks then processes the incoming events using PySpark Structured Streaming and stores the processed data using a Bronze → Silver → Gold Medallion Architecture.

The Gold layer is connected to Power BI for real-time analytics and reporting.

🏗️ Architecture
API
 │
 ▼
Azure Event Hubs
 │
 ▼
Azure Databricks
 │
 │  PySpark Structured Streaming
 ▼
Delta Lake
 │
 ├── Bronze
 │
 ├── Silver
 │
 └── Gold
      │
      ▼
   Power BI
      │
      ▼
Real-Time Dashboards
🛠️ Tech Stack
Microsoft Azure
Azure Event Hubs
Azure Databricks
PySpark
Structured Streaming
Delta Lake
Medallion Architecture
Power BI
Azure DevOps
Git
🔄 Data Flow
1. Event Generation

Ride events are generated through an API.

Example events:

Ride Requested
Driver Assigned
Ride Started
Ride Completed
Ride Cancelled

Each event contains information related to the ride, passenger, driver, location, payment, fare, and ride status.

2. Real-Time Ingestion

The generated events are sent to Azure Event Hubs.

Event Hubs acts as the real-time ingestion layer between the API and Databricks.

3. Stream Processing

Azure Databricks continuously reads events from Event Hubs using PySpark Structured Streaming.

The streaming pipeline processes new events as they arrive instead of waiting for a batch load.

🟤 Bronze Layer

The Bronze layer stores the incoming streaming data in its raw form.

Responsibilities
Capture raw streaming events
Store events in Delta format
Preserve original event history
Maintain streaming checkpoints
Support continuous ingestion
Azure Event Hubs
       ↓
Structured Streaming
       ↓
Bronze Delta Table
⚪ Silver Layer

The Silver layer cleans and validates the incoming streaming data.

Transformations
Null value handling
Duplicate removal
Data type validation
Schema enforcement
Invalid record filtering
Business rule validation
Data standardization

The objective is to create clean and reliable streaming data for downstream analytics.

🟡 Gold Layer

The Gold layer contains analytics-ready data.

A Star Schema is used for reporting and analysis.

Fact Tables

Fact_Ride_Events

Contains ride-level event information used for ride analytics.

Fact_Revenue_Summary

Contains aggregated revenue information for reporting.

Dimension Tables

Dim_Driver

Contains driver-related information.

Dim_Passenger

Contains passenger-related information.

              Dim_Driver
                  │
                  │
Dim_Passenger ─ Fact_Ride_Events
                  │
                  │
          Fact_Revenue_Summary
📊 Power BI Dashboards

The processed Gold data is used to build real-time dashboards.

🚕 Ride Analytics

Key metrics include:

Revenue
Active Rides
Completed Rides
Cancellation Rate
Ride Status
Payment Methods
City-wise Revenue
🚗 Driver Analytics

Key metrics include:

Driver Availability
Busy vs Available Drivers
Revenue by Driver
Driver Locations
Driver Performance
👤 Passenger Analytics

Key metrics include:

Passenger Lifetime Value
Average Fare
Repeat Passengers
Payment Trends
Customer Ride Statistics
⚡ Streaming Processing

The Databricks streaming pipeline continuously processes incoming events.

New Event
    ↓
Event Hubs
    ↓
Databricks Structured Streaming
    ↓
Bronze
    ↓
Silver
    ↓
Gold
    ↓
Power BI

This allows newly generated ride events to move through the pipeline with minimal delay.

🔍 Key Learning Areas

Through this project, I worked with:

Real-Time Data Streaming
Event-Driven Architecture
Azure Event Hubs
PySpark Structured Streaming
Delta Lake
Medallion Architecture
Data Quality & Validation
Star Schema Data Modeling
Real-Time Power BI Reporting
Azure DevOps
Git
📁 Project Structure
real-time-ride-data-engineering/
│
├── api/
│   └── ride_event_generator
│
├── databricks/
│   ├── bronze/
│   ├── silver/
│   └── gold/
│
├── powerbi/
│   └── dashboards/
│
├── architecture/
│   └── architecture.png
│
└── README.md
🎯 Project Objective

The main objective of this project was to understand how a real-time data engineering pipeline works from event generation to business reporting.

Instead of processing data only in batches, this project focuses on continuously processing incoming events using Azure Event Hubs and PySpark Structured Streaming.

🚧 Future Improvements

This project is still a work in progress. Some areas I plan to improve include:

Better handling of edge cases
Additional streaming optimizations
Improved dashboard UI
More advanced monitoring
Additional data quality checks
Performance optimization
More production-oriented error handling

Building the project this way also helped me understand that real-world data pipelines require continuous testing, monitoring, and improvement.

👨‍💻 Author

Naman Kanojia

Data Engineering | Azure | PySpark | SQL | Power BI

⭐ If you find this project useful

Feel free to explore the repository, raise issues, or share suggestions for improving the pipeline.
