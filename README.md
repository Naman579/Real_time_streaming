# 🚀 Real-Time Ride Booking Data Engineering Pipeline

A real-time data engineering project built on Microsoft Azure.

The pipeline generates ride-booking events through an API, streams them through Azure Event Hubs, processes them using Azure Databricks and PySpark Structured Streaming, stores them using a Medallion Architecture, and serves the final data through Power BI dashboards.

## Project Overview

The project simulates a ride-booking platform with events such as:

- Ride Requested
- Driver Assigned
- Ride Started
- Ride Completed
- Ride Cancelled

The main goal was to understand how a real-time data engineering pipeline moves data from event generation to analytics with minimal delay.

## Architecture

```text
API
     ↓
Azure Event Hubs
     ↓
Azure Databricks
     ↓
PySpark Structured Streaming
     ↓
Delta Lake
     ↓
Bronze → Silver → Gold
     ↓
Star Schema
     ↓
Power BI
```

### Data Generation

Ride events are generated through an API.

Each event contains information related to:

- Ride
- Driver
- Passenger
- Location
- Payment
- Fare
- Ride status
- Event timestamp

## Real-Time Ingestion

Azure Event Hubs is used as the streaming ingestion layer.

### Event Flow

```text
Ride Event Generator / API
          ↓
    Azure Event Hubs
          ↓
Azure Databricks Streaming
```

Events are continuously published to Event Hubs and consumed by the Databricks streaming pipeline.

## Azure Databricks – Structured Streaming

Azure Databricks uses **PySpark Structured Streaming** to continuously process incoming ride events.

Main responsibilities:

- Read streaming events
- Parse incoming data
- Apply transformations
- Validate records
- Write data to Delta Lake
- Maintain streaming checkpoints
- Support continuous processing

## Medallion Architecture

### Bronze Layer

The Bronze layer stores raw streaming events.

Implemented using:

- PySpark Structured Streaming
- Delta Lake
- Raw event storage
- Streaming checkpoints
- Original event history

```text
Azure Event Hubs
       ↓
Structured Streaming
       ↓
Bronze Delta Table
```

### Silver Layer

The Silver layer contains cleaned and standardized streaming data.

Main transformations:

- Null value handling
- Duplicate removal
- Data type validation
- Schema enforcement
- Invalid record filtering
- Business rule validation
- Data standardization

The objective is to create reliable data for downstream analytics.

### Gold Layer

The Gold layer contains analytics-ready tables using a Star Schema.

#### Fact Tables

- `Fact_Ride_Events`
- `Fact_Revenue_Summary`

#### Dimension Tables

- `Dim_Driver`
- `Dim_Passenger`

```text
              Dim_Driver
                   │
                   │
Dim_Passenger ─ Fact_Ride_Events
                   │
                   │
          Fact_Revenue_Summary
```

## Power BI Dashboards

The Gold layer is used for real-time reporting in Power BI.

### Ride Analytics

- Revenue
- Active Rides
- Completed Rides
- Cancellation Rate
- Ride Status
- Payment Methods
- City-wise Revenue

### Driver Analytics

- Driver Availability
- Busy vs Available Drivers
- Revenue by Driver
- Driver Locations
- Driver Performance

### Passenger Analytics

- Passenger Lifetime Value
- Average Fare
- Repeat Passengers
- Payment Trends
- Customer Ride Statistics

## End-to-End Pipeline

```text
RIDE EVENT API
  Ride Requested
  Driver Assigned
  Ride Started
  Ride Completed
  Ride Cancelled
          ↓
AZURE EVENT HUBS
  Real-Time Event Ingestion
          ↓
AZURE DATABRICKS
  PySpark Structured Streaming
          ↓
DELTA LAKE
  BRONZE
  Raw Streaming Events
          ↓
  SILVER
  Cleansing | Validation | Standardization
          ↓
  GOLD
  Fact + Dimension Tables
          ↓
POWER BI
  Ride Analytics
  Driver Analytics
  Passenger Analytics
```

## Data Processing

The streaming pipeline continuously processes newly arriving events.

```text
New Event
    ↓
Event Hubs
    ↓
Structured Streaming
    ↓
Bronze
    ↓
Silver
    ↓
Gold
    ↓
Power BI
```

This allows new ride events to move through the pipeline without waiting for a traditional batch processing cycle.

## Technology Stack

| Area | Technology |
|---|---|
| Cloud | Microsoft Azure |
| Streaming Ingestion | Azure Event Hubs |
| Data Processing | Azure Databricks |
| Programming | Python / PySpark |
| Streaming | Structured Streaming |
| Storage Format | Delta Lake |
| Architecture | Medallion Architecture |
| Data Modeling | Star Schema |
| BI | Power BI |
| Version Control | Git / Azure DevOps |

## Project Structure

```text
Real-Time-Ride-Data-Engineering/
│
├── API/
│   └── Ride_Event_Generator/
│
├── Databricks/
│   ├── Bronze/
│   ├── Silver/
│   └── Gold/
│
├── Event_Hubs/
│   └── Configuration/
│
├── PowerBI/
│   └── Dashboards/
│
├── Documentation/
│   └── Architecture/
│
└── README.md
```

## Key Features

- Real-time event generation
- Event-driven architecture
- Azure Event Hubs ingestion
- PySpark Structured Streaming
- Streaming checkpoints
- Delta Lake
- Medallion Architecture
- Data quality validation
- Schema enforcement
- Duplicate handling
- Star Schema
- Real-time Power BI reporting
- Azure DevOps
- Git version control

## Project Learning

This project provided hands-on practice with the real-time Azure data engineering flow:

```text
Event Generator
      ↓
Azure Event Hubs
      ↓
Structured Streaming
      ↓
Bronze
      ↓
Silver
      ↓
Gold
      ↓
Star Schema
      ↓
Power BI
```

Main areas covered:

- Real-time data streaming
- Event-driven architecture
- Azure Event Hubs
- PySpark Structured Streaming
- Delta Lake
- Medallion Architecture
- Data quality
- Data modeling
- Power BI real-time reporting
- Azure DevOps
- Git

## Future Improvements

- Better handling of streaming edge cases
- More advanced monitoring
- Additional data quality checks
- Streaming performance optimization
- Improved dashboard UI
- More detailed error handling
- Additional real-time business metrics
- Automated testing

## Screenshots

Recommended screenshots to add:

1. Overall architecture
2. API / event generation
3. Azure Event Hubs
4. Databricks streaming pipeline
5. Bronze / Silver / Gold tables
6. Power BI Ride Analytics
7. Power BI Driver Analytics
8. Power BI Passenger Analytics

## Repository Links

**GitHub Repository:** Add your repository link here

**LinkedIn:** Add your LinkedIn profile here

## Author

**Naman Kanojia**

Aspiring Data Engineer

**Skills:** Azure | Python | SQL | PySpark | Databricks | Event Hubs | Delta Lake | Power BI | Azure DevOps

## Disclaimer

This is a personal learning/project implementation created to practice real-time Azure Data Engineering concepts. The ride-booking data is simulated and is not intended to represent real customer or driver data.
