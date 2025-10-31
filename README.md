Predictive Maintenance for Railway Wheelsets

INFORMS RAS Competition 2025 — Team Rail@IITK

This repository contains the complete pipeline for predicting railway wheel failure types using multi-sensor operational data and historical maintenance logs.

Overview

Goal: Predict wheel failure type in advance to support proactive maintenance.

Data Size: ~1.5M+ rows of real operational railway wheel data
Sensors used: WILD, WPD, THD, and mileage logs
Output: Multiclass failure probability for each wheel

Key Features of the Solution

End-to-end automated workflow (cleaning → feature engineering → training → evaluation)

Time-series feature engineering (lags, rolling stats, trend measures)

Anomaly-based features using baseline healthy wheel behavior

Interpretable ML using SHAP

Failure progression modeling (Markov transition analysis)

Why This Problem Matters

Railway wheel failures can cause derailments and costly downtime.
Predictive maintenance helps:

Reduce unplanned failures

Improve safety and reliability

Optimize inspection and maintenance schedules

Approach Summary
Data Preparation

Created unique wheel IDs (truck + axle + side)

Converted dates to monthly granularity

Merged ~7 large sensor datasets

Imputed missing engineered features with zeros (best for tree models)

Feature Engineering

Aggregated monthly statistics for each sensor

Created lag & rolling window features

Computed anomaly features by comparing to healthy baseline wheels

Included part mileage (strong wear signal)

Excluded global mileage (not available in test set)

Modeling

Model: LightGBM

Loss: Multiclass log-loss

No SMOTE/oversampling — anomaly features handled imbalance better

Results

Very strong performance on rare failures

Stable generalization from train to test

Best performing model uses:

Part mileage

Rolling statistics

Anomaly deviation features

Wheel location metadata

Insights from Failure Sequence Analysis

Thin flange often progresses to high impact (critical wear path)

High impact failures frequently repeat — poor recovery after repair

Location matters — certain truck/axle/side combinations show higher failure probability
