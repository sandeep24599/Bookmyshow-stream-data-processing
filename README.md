# BookMyShow Stream Data Processing with Azure

## Overview

This project simulates an online ticket booking and payment processing system using **Azure Event Hubs**, **Azure Stream Analytics**, and **Azure Synapse SQL**. The project demonstrates real-time event processing with window-based join operations and writes the final processed data into Azure Synapse SQL tables for further analysis.

## Project Structure

### 1. **Event Hubs (Booking & Payment Data Streams)**
   - Simulates the online booking and payment events for **BookMyShow**.
   - Data is generated using **Python** and published to **Azure Event Hubs**.

### 2. **Azure Stream Analytics**
   - Real-time stream processing job for transforming and joining booking and payment events.
   - Implements window-based operations to correlate booking and payment events.
   - Outputs the final transformed data to **Azure Synapse SQL**.

### 3. **Azure Synapse SQL**
   - Acts as the final destination for the processed data.
   - The transformed and joined data is stored in tables for further data analysis and reporting.

## Tech Stack

- **Programming Language**: Python
- **Event Streaming**: Azure Event Hub
- **Stream Processing**: Azure Stream Analytics
- **Data Warehouse**: Azure Synapse Analytics
- **SQL**: SQL scripts for creating Synapse SQL tables

## Files

### 1. `mock_bookings.py`
   - Generates mock booking events and publishes them to **Event Hub** (`bookingstopic`).
   - Uses the **Faker** library to generate random booking details like event, seats, and customer information.

### 2. `mock_payments.py`
   - Generates mock payment events and publishes them to **Event Hub** (`paymentstopic`).
   - Generates payment data including order ID, payment method, and payment status.

### 3. `stream_analytics_job_query.sql`
   - Contains the **SQL-like query** used in **Azure Stream Analytics** to process booking and payment events, apply window-based join operations, and write the results to **Azure Synapse SQL**.

### 4. `synapse_create_table.sql`
   - SQL script for creating necessary tables in **Azure Synapse SQL** to store the transformed data from Azure Stream Analytics.

## Setup Instructions

### 1. Azure Event Hubs
- Set up two **Event Hubs**: one for booking events and another for payment events.
- Use the `mock_bookings.py` and `mock_payments.py` Python scripts to publish data to these Event Hubs.

### 2. Azure Stream Analytics
- Create an **Azure Stream Analytics job**.
- Configure two inputs (Event Hubs for booking and payment data).
- Configure one output (Azure Synapse SQL).
- Use the query from `stream_analytics_job_query.sql` to process and join the streams.

### 3. Azure Synapse SQL
- Create the necessary tables in **Azure Synapse SQL** using the `synapse_create_table.sql` script.
- Verify that data is being written to the Synapse SQL tables as per the Stream Analytics output.

## How it Works

1. **Booking and Payment Data Simulation**:
   - The `mock_bookings.py` and `mock_payments.py` scripts simulate the real-world ticket booking and payment process.
   - Events are sent to **Azure Event Hubs**.

2. **Real-Time Processing with Azure Stream Analytics**:
   - Stream Analytics job processes the events in real-time.
   - Joins booking and payment events based on a common `order_id`.
   - Uses window-based join operations to account for delays in payment data.

3. **Data Storage in Azure Synapse SQL**:
   - The final output is written to the **Azure Synapse SQL** database for further analytics and reporting.

## Running the Project

1. Clone the repository and navigate to the project directory.
2. Install dependencies:
   ```bash
   pip install azure-eventhub faker
