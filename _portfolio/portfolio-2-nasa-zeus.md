---
title: "NASA ZEUS -- Air Quality Forecasting Platform"
excerpt: >-
  A real-time air-quality intelligence platform combining OpenAQ ground
  stations, NASA TEMPO/MERRA-2 satellite data, NOAA weather signals, and XGBoost
  ozone prediction through FastAPI and Next.js dashboards.
collection: portfolio
permalink: /portfolio/nasa-zeus/
order: 3
---

NASA ZEUS is an air-quality forecasting and monitoring platform built for the
NASA Space Apps Challenge. It combines environmental data streams, ML-based
ozone forecasting, interactive maps, and a conversational assistant for
health-sensitive users and environmental decision support.

<p>
  <a class="btn btn--primary" href="https://github.com/codemith/nasa_zeus">GitHub</a>
  <a class="btn" href="#architecture">Architecture</a>
  <a class="btn" href="https://www.spaceappschallenge.org/">NASA Space Apps</a>
</p>

## Problem

Air-quality information is often fragmented across ground stations, satellite
feeds, weather APIs, and historical pollutant datasets. Users need a unified
view that connects current conditions, forecast signals, health context, and
interpretable ML predictions.

## My Contributions

- Built multi-source environmental data ingestion workflows across air-quality,
  satellite, and weather APIs.
- Developed FastAPI backend endpoints and Next.js dashboard flows for real-time
  environmental intelligence.
- Trained and integrated an XGBoost O3 prediction pipeline for forward-looking
  air-quality estimates.
- Added interactive heat maps and chart-based pollutant trend exploration.
- Integrated a Gemini-powered weather and air-quality assistant for
  natural-language interpretation.
- Helped productionize deployment with Docker, Nginx, and AWS EC2.

## Architecture

NASA ZEUS ingests data from OpenAQ, NASA TEMPO/MERRA-2, and NOAA/OpenWeather
sources, normalizes environmental signals in backend services, feeds ozone
features into an XGBoost forecasting pipeline, and exposes results through
FastAPI APIs consumed by a Next.js dashboard. Docker, Nginx, and AWS EC2 support
deployment of the full-stack application.

## Technical Highlights

- Multi-source environmental data ingestion
- OpenAQ, NASA TEMPO/MERRA-2, NOAA/OpenWeather data
- XGBoost O3 prediction pipeline
- FastAPI backend
- Next.js dashboard
- Interactive heat maps
- Docker + Nginx + AWS EC2 deployment
- Gemini-powered weather/air-quality assistant

## Results / Scale

- Unified satellite, ground-station, and weather data into one air-quality
  intelligence interface.
- Supported hyperlocal ozone prediction workflows for proactive environmental
  monitoring.
- Demonstrated a practical full-stack ML system with data ingestion, model
  inference, APIs, dashboards, and cloud deployment.

## Links

<p>
  <a class="btn btn--primary" href="https://github.com/codemith/nasa_zeus">GitHub</a>
  <a class="btn" href="#architecture">Architecture</a>
  <a class="btn" href="https://www.spaceappschallenge.org/">NASA Space Apps</a>
</p>

<!--
TODO: Add static screenshots under /images/projects/, then embed them here.
Suggested files:
- /images/projects/nasa-zeus-dashboard.png
- /images/projects/nasa-zeus-heatmap.png
- /images/projects/nasa-zeus-assistant.png
-->
