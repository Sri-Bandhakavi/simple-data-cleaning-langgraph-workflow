# Data Cleaning Workflow (LangGraph)

## Overview
This project implements a structured, LLM-driven workflow for basic data cleaning using LangGraph.  
The workflow analyzes a dataset and decides which cleaning action to apply.

## Workflow Steps
1. Load data from CSV
2. Generate dataset summary
3. Use an LLM to select a cleaning action
4. Route to the appropriate node
5. Apply cleaning (if needed)
6. Generate final summary
7. Output results

## Supported Actions
- `clean_missing` → Fill missing numeric values using column mean
- `remove_outliers` → Remove outliers using IQR method
- `both` → Apply both missing value cleaning and outlier removal
- `none` → No cleaning performed, only summary generated

## Key Components
- **State (`DataState`)**: Dictionary that passes data between nodes
- **Reasoning Node**: Uses LLM to decide action based on summary
- **Router (`route_action`)**: Maps decision to next node
- **Execution Nodes**: Perform data transformations

## Notes
- The LLM determines the action based on dataset summary
- The workflow follows a fixed structure with one decision point
- All cleaning steps are deterministic once the action is selected