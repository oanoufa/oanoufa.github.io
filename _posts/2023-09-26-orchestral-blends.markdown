---
layout: post
title:  "Automatic detection of orchestral blends from scores"
subtitle: "Master 1 Data Science research project"
date:   2023-09-11 13:56:45
categories: [data-science, machine-learning, deep-learning]
---

### Orchestral Blends

In the Taxonomy of Orchestral Grouping Effects, we focus on *concurrent grouping*, i.e. the lowest level of the taxonomy. Blends vs non-blends of sounds contribute to the formation of concurrent grouping events. These are the basic building blocks for orchestral layering and for the formation of different “orchestral textures”.

### Research question and goal

The main hypothesis that we have, and that we want to verify in this work, is that many perceptual phenomena are contained in the score, intentionally planned or not by the composer. With this work we want to see to what extent this information can be extracted, to improve on the accuracy of previous studies, and to focus on the peculiarities of misclassified cases.

We use grouping principles based on

- onset synchronicity
- harmonicity
- parallelism in pitch and dynamics

((Antoine et al. 2021) Detected 81.60% of blends (blends as a unit) (80.80% with bar as a unit) with rules based on these three principles above), plus spectral properties of the instrument sounds (Kazazis et al. 2021)

### Project Roadmap

- Question identification and modeling strategy - Francesco, done in Canada, ''*ended*'' July 2023
- Olivier joins the project. Bibliography and model brainstorming
- Preparation of a data frame of extracted features in python
  - Preprocessing - Olivier/Francesco
  - Features on score (with music21, Antoine's parser, other parser) - Olivier
  - Features with spectral properties (spectral centroid, spectral spread, overall or alone, averange in the bar or global) - understand better Eddy's work, condense the information needed, go gradually (from easy and simple to more detailed and complex) - Francesco/Olivier
- Testing machine leaning models on the feature table - Begin with two classes: Blend/Non-blend - Olivier
- Build a proximity tree to build clusters (blend groups) starting from binary decisions - Cluster tracks in the same measures using as distance the results on Blend/Non-blend classification - Olivier
- Model evaluation, analysis of the results

### Modeling strategy

Consider a blend as a list of instruments at a given bar location, ``[11-15] (Vln1, Vln2, Cb)``. We deconstruct the list as a list of couples:

> ``(Vln1, Vln2, Cb) = [(Vln1, Vln2), (Vln1, Cb), (Vln2, Cb)]``

In this way we treat the problem as a binary classification for couples of instruments at a given location: 1 for blend, 0 for no-blend.

To reconstruct a list we use a distance-based clustering for the tracks in each measure. It uses as distance something derived from the results of the classification problem, and it gives back clusters with a tree structure. This clustering models assembles a tree or a space to show the proximity between each part.

The two models will be separated at first. We could think to stack them in the future, and to have a loss function only on the final result.

[Gitlab of the project](https://gitlab.com/algomus.fr/orchard-blends)
