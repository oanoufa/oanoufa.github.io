---
layout: post
title: "Electrification potential of a client’s fleet using GPS data"
subtitle: "Volvo Group — Data Science Internship"
date: 2024-07-30 09:00:00
categories: [industry, internship, data-science]
---

This internship was completed as part of the first year of my Data Science Master's program.

## Role & Context

- Position: Data Science Intern  
- Host: Volvo Group – Renault Trucks, Technology & Service Development  
- Period: April — July 2024  
- Supervisor: Benjamin Echard  

The internship focused on applied data science for sustainable transport: building tools to evaluate the electrification potential of heavy-duty truck fleets using GPS and telematics data, and delivering visual, reproducible outputs for business and technical stakeholders.

## Objectives

- Anticipate electrification needs of long-haul fleets using GPS data.  
- Develop a tool to analyse customer fleets, rank depots by electrification potential, and propose charging strategies.  
- Provide visual and quantitative results (figures, dashboards, and maps) to support customer decisions on electrification investments.  
- Deliver code artefacts, notebooks, and a final presentation usable by the host teams.

## Methods & Tools

Work combined geospatial analysis, big data processing, and visualization:

- **Data access & preprocessing**: GPS and telematics data retrieved via ODBC, cleaned with Spark & Python. Stop/trip files generated, noisy data filtered, and stops merged into ≥30 min charging opportunities.  
- **Geospatial stack**:  
  - `GeoPandas` and `Shapely` for geometric operations (points, polygons, buffers).  
  - Coordinate Reference Systems (EPSG:4171, EPSG:2154) for distance-preserving operations.  
  - `H3` hierarchical hexagonal grid for depot detection, base merging, and stop aggregation.  
- **Storage & computation**: Apache Parquet for columnar storage; Spark (PySpark) for large-scale filtering and joins.  
- **Visualisation**: Plotly for histograms, CDFs, and interactive plots; Folium for interactive fleet and depot maps with layers (stops, heatmaps, bases, stations). PowerBI dashboards for depot ranking and business reporting.  
- **Algorithm**: “Electrification score” simulation with five charging strategies (from a single AC depot station up to AC+DC stations, public infrastructure, and one/two optimally placed DC stations). Score = fraction of mission energy achievable under electric constraints. Threshold of 80% used to classify electrifiable vehicles.

## Outcomes & Deliverables

- **Fleet electrification tool**: produced stop/trip preprocessing, depot/base identification, and electrification simulations for ~35 weeks of 2023 GPS data.  
- **Depot ranking**: scoring routine applied across depots, producing ranked histograms of electrification potential.  
- **Dashboards & maps**:  
  - PowerBI report with depot-level scores, fleet composition, simulation durations, and depot maps.  
  - Folium HTML maps with interactive heatmaps, bounding boxes, and charging stations.  
- **Example results**:  
  - Vehicles’ energy scores improved progressively from Config. 1 (AC only) through Config. 5 (two optimal DC stations).  
  - Optimal station placement identified using H3 aggregation, maximizing depot-level electrification with minimal infrastructure.  

These deliverables were used internally to support customer-facing discussions on electrification strategy.

## Lessons & Next Steps

- Strengthened skills in geospatial data science, Spark-based preprocessing, and communicating technical insights to both engineers and business owners.  
- Learned to balance computation realism (continuous simulations, charging assumptions) with feasibility and performance.  
- Recommended next steps:  
  - Sensitivity analyses on thresholds (stop definition, base detection, night stops).  
  - Simulations at finer granularity (per week/day) to better capture mission variability.  
  - Incorporating infrastructure constraints (station availability/occupancy).  
  - Extending visual dashboards with automation for recurring customer studies.  

---