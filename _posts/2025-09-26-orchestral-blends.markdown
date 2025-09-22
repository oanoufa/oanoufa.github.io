---
layout: post
title:  "Automatic detection of orchestral blends from scores"
subtitle: "Master 1 Data Science research project"
date:   2023-09-11 13:56:45
categories: [music, data-science, machine-learning, deep-learning, projects]
---

I worked on this project together with Francesco Maccarini and Mathieu Giraud as part of the first year of my Master's degree in Data Science. The repository and accompanying resources are available at https://gitlab.com/algomus.fr/orchestral-blends.

## Overview

Orchestral blends describe situations where multiple instruments played together produce a cohesive perceptual timbre. The work in the companion repository aims to detect such blending directly from musical scores using a combination of perception-informed features, dataset annotations and machine learning.

## Goal

We hypothesise that many compositional cues that promote perceived blending (synchrony, harmonicity, parallel motion, relative note density, etc.) are present in the score and can be extracted and used by a model to predict which instrument pairs (or groups) form blends.

## Data

- Ground-truth annotations from OrchARD (Orchestration Analysis and Research Database) and curated MusicXML excerpts collected by collaborators.
- Result tables from Antoine et al. (used as reference annotations in `anotine_csv_results`).
- Precomputed feature tables and processed spectral fingerprints (TimbreToolbox on Vienna Symphonic Library samples) are included in the repository under `data/` (some raw files are restricted and not public).

## Modeling strategy

- We cast the problem as binary classification on instrument pairs at a given measure: for each pair (Part1, Part2, MeasureID) we compute per-track features, cross-track similarity features and a target blend flag (1/0).
- Lists of instruments are decomposed into pairs: e.g. (Vln1, Vln2, Cb) -> [(Vln1, Vln2), (Vln1, Cb), (Vln2, Cb)].
- To reconstruct blend groups from pairwise predictions we use a depth-first algorithm that treats each measure as a graph of instruments and aggregates connected pairs into groups.

## Code and analysis notebooks

The repository organises the full pipeline. Key components include:

- `build_blends_table.ipynb` — extract and build the ground-truth `blends_table.csv` from annotations.
- `build_spectral_table.ipynb` and `timbre_toolbox_vsl_plots.ipynb` — compute and inspect spectral fingerprints.
- `src/build_feature_table.py` — compute score-based and cross-track features into the `data/features` tables.
- `models_evaluation.ipynb` — training and evaluation using a leave-one-piece-out cross-validation; predictions saved in `results/predictions`.
- `models_statistics.ipynb` and `models_further_investigations.ipynb` — visual analysis and follow-up experiments.
- `note_count_model_evaluation.ipynb` — evaluation for a simple baseline that compares concurrent note counts between parts.

## Findings and results

- The models using perception-informed features improve on prior score-based algorithms for blend detection.
- Interestingly, a simple baseline based on comparing the number of concurrently sounding notes between two parts performs competitively on some metrics, which highlights the importance of simple synchrony cues in perceived blending.

## Reproducibility

- The repository provides preprocessed tables in `data/` and notebooks to reproduce feature extraction, model training and evaluation. Some original MusicXML files are restricted and not mirrored in the repo due to copyright.

## Paper

This repository accompanies the paper:

[Francesco Maccarini, Olivier Anoufa, Mathieu Giraud, Florence Levé, Stephen McAdams. "Detection of orchestral blends in musical scores." Sound and Music Computing (SMC) 2025, Graz.](https://www.mcgill.ca/mpcl/files/mpcl/maccarini_2025_smc.pdf)

## Links

- Repository: https://gitlab.com/algomus.fr/orchestral-blends
- License: GNU GPLv3 (see repo)
