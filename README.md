# AutoPersuade

## Introduction 
This repository contains the code required to reproduce the main results of *AutoPersuade: A Framework for Evaluating and Explaining Persuasive Arguments* (Preprint available here: https://arxiv.org/abs/2410.08917).

## Setup
The required Python environment is specified in `autpersuade_env.yml`. This includes the implementation of the SUpervised semi-nonnegative matrix factorization Topic Model in the `suntm` package, which is available via `pip` or directly from https://github.com/TillRS/SUN_TopicModel.

Create the python environment:
   ```bash
   conda env create -f autpersuade_env.yml
   ```

## Data
The required data, including the argument collections used in all experiments and the embeddings for fitting the topic model, are in the `data` directory. Specifically:

- **Original_Argument_Collection_with_BT_Score_and_Topics.xlsx**: This Excel file includes the original argument collection with corresponding Bradley-Terry (BT) scores and inferred topic loadings based on the selected topic model fit. It includes the original, underlying arguments and intermediate summaries, as well as the training/test data split. An indicator shows the 80% of training data used for the final, selected model fit. Topic loadings are provided for both 100-step SNMF-based inference (early stopping) and inference until convergence using CVXPY.

- **Validation_Study1_Arguments_with_Topics.xlsx**: This file contains the arguments used in the first validation study, along with inferred topic loadings based on the selected topic model fit. Topic loadings are provided for both 100-step SNMF-based inference (early stopping) and inference until convergence using CVXPY.

- **Validation_Study3_Arguments_with_Topics.xlsx**: This file contains the arguments from Validation Study 3, with their inferred topic loadings based on the selected topic model fit. Topic loadings are provided for both 100-step SNMF-based inference (early stopping) and inference until convergence using CVXPY.

- **Original_Argument_Collection_Embeddings.pt**: This file contains the pre-computed embeddings ("text-embedding-ada-002") of the original argument collection, used as input features for training the topic model.

- **Validation_Study1_Embeddings.pt**: This file contains the embeddings for the arguments in Validation Study 1, similar to the original argument collection embeddings, used for topic modeling.

- **Validation_Study3_Embeddings.pt**: This file contains the embeddings for the arguments used in Validation Study 3, used for topic modeling.

- **Original_Survey_Results.xlsx**: This file contains the survey results used to evaluate the persuasiveness of arguments in the original collection. These results are used to calculate the BT scores.

- **Validation_Study1_Survey_Results.xlsx**: This file contains the survey results from Validation Study 1, used for evaluating the persuasiveness of arguments.

- **Validation_Study2_Survey_Results.xlsx**: This file contains the survey results from Validation Study 2, used for performance evaluation of the arguments in that study.

- **Validation_Study3_Survey_Results.xlsx**: This file contains the survey results from Validation Study 3, used to assess the persuasive performance of the arguments.

All figures used in the paper are recreated by the scripts and saved in the `figures` directory.


## Recreating the Results
The scripts directory contains the following files:
- **`0_argument_generation.md`:** Documentation of the argument generation process used for the original collection and subsequent validation studies.
- **`1_argument_evaluation.ipynb`:** Jupyter notebook that calculates Bradley-Terry scores for the original argument collection using survey results.
- **`2_sun_topic_model.ipynb`:** Jupyter notebook for exploring topic model fits. This notebook generates the topic model fit used in the paper and estimates causal effects of discovered topics on the estimation set using the 100 step SNMF-based inference method (early stopping).
- **`2_sun_topic_model_cvxpy.ipynb`:** Jupyter notebook for exploring topic model fits. This notebook generates the topic model fit used in the paper and estimates causal effects of discovered topics on the estimation set using the CVXPY-based topic inference method.
- **`3_validation_study_argument_selection`:** Jupyter notebook that filters arguments used in the validation studies. Filtering using the CVXPY-based topic inferenced leads to only selecting a subset of the arguments originally chosen for the validation studies.
- **`4_validation_experiments.ipynb`:**  Jupyter notebook that evaluates the performance of different argument types in the three validation studies based on raw survey data. Results are calculated for all arguments used in the validation studies and the subsets that pass the filtering using CVXPY-based topic inference.

## Citation
If you use this code, please cite our work as follows:

Till Raphael Saenger, Musashi Hinck, Justin Grimmer, and Brandon M. Stewart. 2024. [AutoPersuade: A Framework for Evaluating and Explaining Persuasive Arguments](https://aclanthology.org/2024.emnlp-main.913/). In Proceedings of the 2024 Conference on Empirical Methods in Natural Language Processing, pages 16325–16342, Miami, Florida, USA. Association for Computational Linguistics.
