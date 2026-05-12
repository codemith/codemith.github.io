---
title: "NASA ZEUS Air Quality Monitoring System"
excerpt: "A real-time air quality intelligence platform that combines ground stations, NASA satellite observations, weather forecasts, and AI-powered ozone predictions in a unified monitoring dashboard."
collection: portfolio
---

## Overview

NASA ZEUS is an air quality monitoring and forecasting platform built for the NASA Space Apps Challenge. It unifies environmental signals from ground sensors, satellite observations, and weather feeds to provide actionable air quality insights for health-sensitive users.

<p><a href="https://github.com/codemith/nasa-zeus">GitHub</a> &nbsp; <a href="https://www.spaceappschallenge.org/">NASA Space Apps Challenge</a></p>

### Key Features
- **Interactive heat-map monitoring** with live spatial air quality visualization.
- **Multi-source ingestion** across OpenAQ ground stations, NASA TEMPO data, and OpenWeather forecasts.
- **AI Weather Agent** for conversational analysis of weather and pollution context.
- **Ozone (O3) prediction pipeline** for forward-looking air quality estimates.
- **Historical trend exploration** with chart-based analysis of pollutant patterns.

### Technical Highlights
- Architected an end-to-end data pipeline to normalize and combine heterogeneous environmental APIs.
- Built a low-latency full-stack system with FastAPI + Next.js for real-time map and analytics workflows.
- Integrated Gemini-powered agent endpoints for natural-language weather and air quality interpretation.
- Containerized and productionized deployment with Docker, Nginx, and AWS EC2 for cost-efficient hosting.

### Core Stack
- **Frontend:** Next.js, React, Tailwind CSS, React Leaflet, Chart.js
- **Backend:** Python, FastAPI, SQLite, httpx
- **AI/ML:** Google Gemini, PyTorch, Pandas, NumPy
- **Data Sources:** OpenAQ, NASA TEMPO, OpenWeatherMap
- **Deployment:** Docker, Docker Compose, Nginx, AWS EC2
