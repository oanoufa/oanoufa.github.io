---
layout: post
title: "Investigating contamination events in SARS-CoV-2 genome data"
subtitle: "EMBL-EBI — Research Internship"
date: 2025-09-22 09:00:00
categories: [research, internship, bioinformatics]
---

This internship was completed as part of the second year of my Data Science Master's program.

## Role & Context

- Position: Scientific Trainee  
- Host: EMBL-EBI (European Bioinformatics Institute), Nick Goldman’s group  
- Supervisors: Nicola De Maio and Nick Goldman  
- Period: April — September 2025

The internship focused on applied bioinformatics research: detecting and masking contamination in SARS-CoV-2 genome data and developing scalable analysis procedures for pandemic-scale datasets.

## Objectives

- Understand the SARS-CoV-2 sequencing process, and how contamination events can affect consensus genome calls. 
- Design and implement a scalable pipeline to identify genome positions whose consensus calls may be affected by contamination.  
- Evaluate masking strategies using phylogenetic placement and quantitative metrics, and report results and recommendations.

## Methods
 
Key method points implemented in the pipeline:

- For each sample, generate three consensus versions: the original (“unmasked”), a coverage-based masked version (“masked”), and a control “randomly masked” version with the same number of masked positions.  
- Masking rule: positions with coverage under **10% of the sample median coverage** or under a hard threshold of **50X** are masked; additional standard problematic sites (known error-prone positions and terminal regions) are also masked.  
- Place all three sequence versions onto the background tree with MAPLE, compare placement distances and supports, and select candidates where masking substantially reduces distance to the tree (distance difference ≥ 2 and masked distance < 5).  
- For selected samples, search the background tree for candidate contaminants by finding genomes that share the masked mutations.

## Outcomes & Deliverables

- Analysed a dataset of **4,952,451** Viridian-processed SARS-CoV-2 samples.  
- Identified **10,932** putatively improved genomes using the Decontaminator masking (versus **6,795** using randomly shifted masks as a baseline).  
- Produced reproducible analysis notebooks, scripts, and internal research notes documenting the pipeline, selection criteria, and quantitative evaluations.  
- For each candidate, the pipeline produced placement diagnostics, lists of masked mutations, and the top contaminant candidates (with closeness and candidate counts).

## Lessons & Next Steps

- Strengthened domain knowledge in contamination modes, coverage-based masking strategies and pandemic-scale phylogenetic placement.  
- Observed that coverage-based masking can reduce placement errors, but further work is needed to distinguish contamination from other phenomena (within-host variation, recombination, low quality data, etc.).  
- Next steps:  
  - Explore probabilistic models (e.g., HMM-style approaches) to replace or complement static coverage thresholds.  
  - Improve contaminant-candidate identification to account for reversions and use masked blocks (not only masked single-site mutations).  
  - Rebuild and compare phylogenetic trees using masked vs unmasked genomes to better assess the global impact of masking and potential contamination in background data.

---
