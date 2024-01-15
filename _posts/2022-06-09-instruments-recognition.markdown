---
layout: post
title:  "Instruments recognition using supervised training"
subtitle: "Deep learning course project"
date:   2022-06-29 18:34:01
categories: [data-science, machine-learning, deep-learning]
---
Deep learning course project where we chose to work on instruments recognition using supervised training. We used the [IRMAS dataset](https://www.upf.edu/web/mtg/irmas) which contains 6705 audio files of 3 seconds each, divided into 11 categories of instruments. We  also used the [Librosa](https://librosa.org/doc/latest/index.html) library to extract features from the audio files and the [Keras](https://keras.io/) library to build our neural network.

We managed to build different models, a dense one and a convolutional one, partly trained using transfer learning. We finally reached 0.5 accuracy on the instruments recognition task.
