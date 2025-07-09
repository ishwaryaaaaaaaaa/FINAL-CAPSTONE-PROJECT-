# FINAL-CAPSTONE-PROJECT-






# Dynamic Pricing for Urban Parking Lots

## Overview

This project implements a real-time, dynamic pricing engine for 14 urban parking lots using real-world traffic, occupancy, and queue data. The goal is to ensure efficient space utilization by adjusting prices based on demand, time, location, and competition.

It was developed as part of the Summer Analytics 2025 Capstone, organized by the Consulting & Analytics Club × Pathway.

---

## Tech Stack Used

- **Python** – Core programming language
- **Pandas & NumPy** – Data processing and numerical logic
- **Pathway** – Real-time streaming and dataflow execution
- **Bokeh** – Real-time data visualization
- **Google Colab** – Development environment
- **Mermaid** – Architecture diagram

---









## Project Architecture & Workflow
This project implements a real-time, intelligent pricing engine for urban parking lots using Python, Pathway, and Bokeh. The architecture is modular and designed to simulate a real-world dynamic pricing system that adapts continuously to live factors such as traffic conditions, occupancy levels, queue length, and competitive pricing.

## Architecture Overview
The system is composed of the following key components:

## 1. Real-Time Data Ingestion (Pathway)
The raw dataset (dataset.csv) simulates a real-time data stream using Pathway’s streaming functionality.

It contains data from 14 different parking lots, sampled every 30 minutes for 73 consecutive days.

Each row includes fields like occupancy, queue length, vehicle type, traffic level, and special event indicators.

## 2. Feature Engineering Module
Each incoming data record is processed into meaningful features for modeling, including:

Occupancy Rate = Occupancy ÷ Capacity

Vehicle Type Weight: Bikes = 0.5, Cars = 1.0, Trucks = 1.5

Traffic Level: Converted from {low, medium, high} to {1, 2, 3}

Timestamp: Combined from LastUpdatedDate and LastUpdatedTime for time-ordered processing

## 3. Pricing Logic Layer (Model Selector)
The pricing layer dynamically selects and applies one of three models:

## Model 1: Linear Pricing
  A simple model that increases price proportionally as occupancy increases.
  Price_t+1 = Price_t + α * (Occupancy / Capacity)
  
## Model 2: Demand-Based Pricing
   A more advanced model that factors in multiple demand indicators:
   Demand = α * OccRate + β * Queue - γ * Traffic + δ * SpecialDay + ε * VehicleTypeWeight  
   Price = 10 * (1 + λ * NormalizedDemand)
   
## Model 3: Competitive Pricing
  Introduces location intelligence by comparing prices with nearby lots:
  If a lot is full and nearby lots are cheaper, reduce price or suggest rerouting.
  If nearby lots are expensive, increase price while staying competitive.

## 4. Real-Time Execution Engine
Pathway runs a continuously updating dataflow that:
Maintains the timestamp order of events
Applies UDFs and pricing logic in sequence
Produces a real-time pricing output stream

## 5. Output Emission
Final prices are streamed and written to a streamed_prices.jsonl file in real-time.
This file can be used for further analysis or visualization.

## 6. Visualization Dashboard (Bokeh)
Bokeh is used to create an interactive, real-time visualization dashboard.
Displays pricing trends for each parking lot over time.
Optionally includes model comparisons, occupancy levels, and rerouting triggers.

## Workflow Summary
1.Load & Stream Data – Simulate real-time feed using Pathway from the raw CSV file

2.Process Features – Compute occupancy rate, vehicle weights, traffic level, and timestamp using UDFs

3.Apply Pricing Model – Dynamically select and apply Model 1, 2, or 3

4.Output Pricing – Stream computed price to a live .jsonl file

5.Visualize – Plot real-time prices using Bokeh for monitoring and insights

















## Architecture Diagram

```mermaid
flowchart TD
    Start([Start])
    A[Ingest Real-Time Data using Pathway]
    B[Extract Features: Occupancy, Queue, Traffic, Vehicle Type, etc.]
    C{Select Pricing Model}
    D1[Model 1: Linear Pricing]
    D2[Model 2: Demand-Based Pricing]
    D3[Model 3: Competitive Pricing]
    E[Compute Updated Price]
    F[Stream Output to Bokeh Dashboard]
    G([End])

    Start --> A --> B --> C
    C -->|Model 1| D1 --> E
    C -->|Model 2| D2 --> E
    C -->|Model 3| D3 --> E
    E --> F --> G






