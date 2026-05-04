Logistics Data Warehouse & Business Intelligence Solution

🚚 Project Overview
This project is a comprehensive Business Intelligence (BI) solution designed to analyze logistics operations. It handles data across four key business processes: Trips, Fuel Consumption, Vehicle Maintenance, and Delivery Events.

The goal was to transform raw operational data into actionable insights regarding fleet efficiency, revenue generation, and delivery performance.

🏗️ Architecture & Tech Stack
Database: SQL Server (Data Warehouse & Staging)

ETL Tool: SQL Server Integration Services (SSIS)

OLAP Engine: SQL Server Analysis Services (SSAS) - Multidimensional Cube

Visualization: Power BI & Excel Pivot Tables

📊 Data Modeling (Galaxy Schema)
The project utilizes a Galaxy Schema (also known as a Fact Constellation) where multiple fact tables share conformed dimensions:

Fact Tables: FactTrips, FactFuel, FactMaintenance, FactDeliveryEvents.

Shared Dimensions: DimDate, DimTruck, DimDriver, DimRoute, DimCustomer.

Key Feature: Accumulating Snapshot
I implemented an Accumulating Snapshot logic for the FactTrips table. This allows for tracking the lifecycle of a trip from creation to completion, enabling the calculation of total process duration (txn_process_time_hours).

⚙️ ETL Workflow
The ETL process is orchestrated through a series of SSIS packages:

PKG_01_Staging: Extracts data from CSV/Source systems into a staging area.

PKG_02_Dimensions: Populates the dimension tables using a lookup strategy.

PKG_03_Facts_Initial: Performs the initial insert for the Fact tables.

PKG_04_Update_Facts: Updates existing Fact records (Accumulating Snapshot) to fill in completion milestones and calculated metrics.

📈 Analytics & Dashboards
The final Power BI report provides:

Delivery Performance: Event counts broken down by Year, Quarter, and Month.

Temporal Filtering: Dynamic slicers for deep-dive analysis across different time grains.

Drill-down Capabilities: From yearly trends down to specific daily delivery events.
