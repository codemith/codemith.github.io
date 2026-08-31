---
title: "System Failure Forecasting -- Capgemini Challenge Winner"
excerpt: >-
  A predictive maintenance system using LSTM and XGBoost models to forecast
  system failures from high-dimensional time-series data, deployed through AWS
  SageMaker-style ML workflows.
collection: portfolio
permalink: /portfolio/system-failure-forecasting/
order: 4
---

System Failure Forecasting was built for the Capgemini Predictive Failure
Challenge at CUHackit 2025, where the project won the challenge track. The
system focuses on forecasting failures from high-dimensional operational
time-series data so teams can monitor system health before downtime occurs.

<p>
  <a class="btn btn--primary" href="#architecture">Architecture</a>
  <a class="btn" href="/files/Mithilesh_Biradar_resume.pdf">Resume Context</a>
</p>

## Problem

Infrastructure and industrial systems often fail after subtle patterns appear
across telemetry, usage, and sensor signals. Reactive monitoring catches issues
too late; predictive maintenance needs models that can learn temporal patterns
and produce actionable failure-risk forecasts.

## My Contributions

- Built LSTM and XGBoost models for system failure prediction.
- Processed high-dimensional time-series data for predictive maintenance.
- Designed scalable model training, evaluation, and deployment workflows.
- Framed the system around business value: reducing downtime, enabling
  proactive monitoring, and supporting real-world system health prediction.

## Architecture

The workflow processes multivariate time-series inputs, creates model-ready
features and sequences, trains both LSTM and XGBoost predictors, evaluates
failure-risk performance, and packages the model workflow for repeatable
deployment through AWS SageMaker-style training and inference stages.

## Technical Highlights

- High-dimensional time-series processing
- LSTM sequence modeling
- XGBoost baseline and tabular forecasting workflow
- Predictive maintenance framing
- Model training, validation, and deployment pipeline design
- AWS SageMaker-style ML workflow

## Results / Scale

- Won the Capgemini Predictive Failure Challenge at CUHackit 2025.
- Demonstrated a practical ML workflow for reducing downtime and enabling
  proactive system monitoring.
- Compared deep sequence modeling and gradient-boosted tree approaches for
  system health prediction.

## Links

<p>
  <a class="btn btn--primary" href="#architecture">Architecture</a>
  <a class="btn" href="/files/Mithilesh_Biradar_resume.pdf">Resume Context</a>
</p>

<!--
TODO: Add screenshots or diagrams under /images/projects/, then embed them here.
Suggested files:
- /images/projects/system-failure-pipeline.png
- /images/projects/system-failure-results.png
-->
