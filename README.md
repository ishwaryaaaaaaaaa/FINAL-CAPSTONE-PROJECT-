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
graph TD
    A[CSV Input Stream] --> B[Pathway Real-Time Engine]
    B --> C[Feature Engineering - UDF]
    C --> D[Pricing Logic: Model 1 / 2 / 3]
    D --> E[Output Stream - JSONL]
    E --> F[Bokeh Dashboard]





