# AutoPersuade

## Introduction 
This repository contains the code required to reproduce the main results of *AutoPersuade: A Framework for Evaluating and Explaining Persuasive Arguments* ([Link to paper]). The necessary data can be accessed at [Link to data].

## Installation
The required Python environment is specified in `autpersuade_env.yml`. Please note that the environment requires the manual installation of the custom `sun_topicmodel` package, which will be available via Conda or Pip soon. Until then, follow these steps:

1. Clone the `sun_topicmodel` repository:  
   ```bash
   git clone https://github.com/TillRS/SUN_TopicModel
   ```

2. Install the package locally:
    ```bash
    cd SUN_TopicModel
    pip  install .
    ```

## Data
The required data, including the argument collections used in all experiments and the embeddings for fitting the topic model, can be found at [Link to data]. Further details on accessing and preparing the data will be provided soon.

## Recreating the Results
The scripts directory contains the following files:
- **`0_argument_generation.md`:** Documentation of the argument generation process used for the original collection and subsequent validation studies.
- **`1_argument_evaluation.ipynb`:** Jupyter notebook that calculates Bradley-Terry scores for the original argument collection using survey results.
- **`2_sun_topic_model.ipynb`:** Jupyter notebook for exploring topic model fits. This notebook generates the topic model fit used in the paper and estimates causal effects of discovered topics on the estimation set.
- **`3_validation_experiments.ipynb`:**  Jupyter notebook that evaluates the performance of different argument types in the three validation studies based on raw survey data.

## Citation
If you use this code, please cite our work as follows:
[Citation details will be added here]
