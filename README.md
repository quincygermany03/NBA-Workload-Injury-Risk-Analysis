# NBA-Workload-Injury-Risk-Analysis
SQL + Tableau project analyzing NBA player workload and injury risk. Explores MPG, workload spikes, and injury patterns to generate insights for performance and injury prevention.
NBA-Workload-Injury-Risk-Analysis
Executive Summary

This project investigates the relationship between NBA player workload and injury risk using a SQL-driven data pipeline and Tableau visualization.

Unlike basic sports analysis, this approach:

Integrates game-level performance data with injury records
Engineers player workload and injury metrics across seasons
Classifies injuries using text-based feature engineering (ILIKE + CASE)
Produces a master analytical dataset for visualization and insights

The result is a structured framework for understanding how minutes played and workload changes impact injury likelihood.

Dashboard Preview

<img width="1998" height="1166" alt="NBA Workload" src="https://github.com/user-attachments/assets/9444e99a-2344-4b24-bb89-d55e07bb2f6d" />


Business / Sports Medicine Motivation

In professional sports, managing player workload is critical for performance, availability, and long-term health.

Key questions:

Does higher MPG increase injury risk?
Do sudden workload spikes lead to more injuries?
Which injury types are most associated with high workload?

This framework enables:

Data-driven load management strategies
Identification of high-risk workload patterns
Foundations for injury prevention analytics
Data

Time Period: Multi-season NBA data (~2003–2023)
Granularity: Player-game → Player-season

Sources
games – game-level metadata
games_details – player minutes and performance
injuries_clean – cleaned injury records
nba_workload – aggregated workload metrics
injury_summary – injury counts and classifications
Processing
Converted minutes from "MM:SS" → numeric using split_part()
Standardized injury dataset using TRUNCATE + INSERT pipeline
Derived season using EXTRACT(YEAR FROM injury_date)
Classified injuries using CASE WHEN + ILIKE (knee, ankle, etc.)
Created injury_flag and injury_count metrics
Joined all datasets into a final master_tableau dataset
Analytical Approach
Cohort Definition
Active NBA players with recorded minutes
Linked to injury events across seasons
Feature Engineering
Minutes per game (MPG)
Workload buckets (0–9.9, 10–19.9, 20–29.9, 30+)
Injury classification (body region)
Injury counts per player
Core SQL Concepts
Common Table Expressions (CTEs)
LEFT JOINs for dataset integration
Aggregations (COUNT, AVG)
Conditional logic (CASE WHEN)
Text classification (ILIKE)
Date extraction and casting
Key Results
Players with 30+ MPG show ~77% injury rate
Workload spikes correlate with higher injury likelihood
Injury risk remains elevated even at moderate workloads
Knee and ankle injuries are the most frequent
Interpretation

This analysis suggests that injury risk is driven by both:

Absolute workload (high MPG)
Relative workload changes (spikes)

Findings highlight the importance of:

Monitoring short-term workload fluctuations
Managing cumulative player fatigue
Targeting lower-body injury prevention strategies
Tech Stack
PostgreSQL – Data extraction, cleaning, transformation
SQL – Feature engineering, joins, aggregations
Tableau – Data visualization and dashboarding
Notes
Data compiled from public/synthetic sources for portfolio use
Demonstrates an end-to-end analytics pipeline
Future improvements:
Rolling workload metrics (7-day / 14-day windows)
Back-to-back game analysis
Predictive injury modeling
