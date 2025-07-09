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

## Architecture Diagram

```mermaid
flowchart TD
    Start([Start])
    A[Ingest Real-time Data with Pathway]
    B[Extract Features: Occupancy, Queue, Traffic, etc.]
    C{Model Type?}
    D1[Model 1: Linear Price Update]
    D2[Model 2: Demand-Based Pricing]
    D3[Model 3: Competitive Pricing]
    E[Update Price]
    F[Emit to Visualization (Bokeh)]
    G([End])

    Start --> A --> B --> C
    C -->|Model 1| D1 --> E
    C -->|Model 2| D2 --> E
    C -->|Model 3| D3 --> E
    E --> F --> G




