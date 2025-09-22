---
layout: post
title: "Conditional Bass Guitar Tablature Generation"
subtitle: "Master 2 Data Science research project"
date: 2025-03-30 09:00:00
categories: [music, machine-learning, deep-learning, projects]
---

I led this project together with Alexandre D'Hooge and Ken Déguernel as part of the second year of my Master's degree in Data Science. The repository and accompanying resources are available at https://github.com/adhooge/BassTablatureGeneration.

## Overview

The project develops a conditional generative system that produces bass guitar tablature to accompany a given guitar part. It was created as part of our AIMC 2025 work "Conditional Generation of Bass Guitar Tablature for Guitar Accompaniment in Western Popular Music" and the codebase, demo and checkpoints are publicly available.

## Highlights

- **Paper:** [Anoufa, O., D'Hooge, A., Déguernel, K. "Conditional Generation of Bass Guitar Tablature for Guitar Accompaniment in Western Popular Music", AI Music Conference (AIMC) 2025.](https://doi.org/10.5281/zenodo.16946476)
- **Demo:** A live demo of generated tablatures is posted at https://adhooge.github.io/BassTablatureGeneration/.
- **Code & checkpoints:** the repo contains `src/` for training and inference scripts, `ckpt/` with provided checkpoints, and `data.zip` with the preprocessed dataset used for experiments.
- **Dataset:** experiments are based on the DadaGP dataset (Sarmento et al. 2021); the repository shares a preprocessed subset under the included `DATA_LICENSE`.
- **Environment:** a ready-to-use `environment.yml` is provided to reproduce the experiments (the training script `src/model_train.py` requires a GPU and several hours to run).
- **License:** code is shared under GPL-3.0 and data under ODbL-1.0; see `LICENSE` and `DATA_LICENSE` for details.

## Approach (summary)

- **Input representation:** the project uses extracted tokens and rhythmic annotations derived from DadaGP to represent guitar lines and targets for bass tablature.
- **Model:** we implemented a conditional sequence generation model inspired by prior symbolic music generation architectures (the repository documents the training and inference scripts used).
- **Training & inference:** training scripts are in `src/`, and the repository includes utilities for merging generated GP5 files and producing the demo outputs (see `merge_gp5.py` and `merged_gp5/`).

## Outcomes

- **Reproducible code and checkpoints** that allow others to generate bass tablature conditioned on guitar tracks.
- **A public demo** showcasing generated examples and the accompanying AIMC 2025 paper describing the method and experiments.

## How to reproduce

- Clone the repo and unzip `data.zip`.
- Create the conda environment with `conda env create -f environment.yml`.
- Train or run inference using `src/model_train.py` and the inference utilities; GPU is recommended for training.

## Links

- **Repository:** https://github.com/adhooge/BassTablatureGeneration
- **Demo website:** https://adhooge.github.io/BassTablatureGeneration/
- **Paper** Published at AIMC 2025: https://doi.org/10.5281/zenodo.16946476

If you'd like, I can expand this post with a technical methods section, sample tablature outputs, or a short tutorial showing how to run the demo locally.
