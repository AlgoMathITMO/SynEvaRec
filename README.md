## SynEvaRec: A Framework for Evaluating Recommender Systems on Synthetic Data Classes
This work is an addition to the paper "SynEvaRec: A Framework for Evaluating Recommender Systems on Synthetic Data Classes" by Provalov et al.

## Abstract
This study proposes a novel method for evaluating and comparing recommender systems using synthetic user and item data and parametric synthetic user-item response (rating) functions. The method compares recommender systems on classes of synthetic data, oppositely to how it is usually done on particular real or synthetic datasets. The usage of classes particularly allows for managing the effects of the No Free Lunch theorem for recommender systems. Furthermore, we implement the method in the form of a flexible framework (that we call SynEvaRec) for conducting comparison experiments under different scenarios of synthetic data behaviour. Our experimental study shows that SynEvaRec helps to determine scenarios (e.g. in terms of data classes) where one recommender system is more preferable than another by means of recommendation quality. Moreover, the results turn to be rather stable over several synthetic dataset instances based on the same real-world dataset indicating the robustness of our method. The datasets, the framework implementation and the results related to our study are publicly available on GitHub.

## Data
We use two datasets in this study (`/datasets`):
- Restaurants and Their Clients (source <a href='https://www.kaggle.com/uciml/restaurant-data-with-consumer-ratings'>Kaggle</a>)
- Book Recommendations (source <a href='https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset'>Kaggle</a>)

Datasets require pre-processing. The pre-processing is included in the corresponding notebooks ('restaurants_main.ipynb' in the case of Restaurants dataset, 'books_main.ipynb' in the case of Books dataset).

All of the synthetic data can be generated in our code using the jupyter notebooks (`/notebooks`) with experiments.
Example for the Restaurants data generation:
```
syn_data_generator_rests = fit_syn_generator_rests(rests_df)
syn_rests_df = syn_data_generator_rests.sample(100)
```
## Experiments
To run the experiments for a certain dataset you need to use the notebooks in `/notebooks`.

You can evaluate the quality of the following recommender systems now:
- NMF
- SVD
- kNN

If you want to enlarge this set by own model, you can add the desired model manually into `/modules/models.py`. If you want to enlarge this set by the existing model, you can add the process of its training end testing in `/modules/trainers.py`. 

The process of recommender systems quality evaluation on the parametric data is realized in `/modules/evaluator.py`.

## Main results
<p align="left">
  <img width="300"src="https://raw.githubusercontent.com/AlgoMathITMO/SynEvaRec/main/images/ss_0_1_rests.png">
  <img width="300"src="https://raw.githubusercontent.com/AlgoMathITMO/SynEvaRec/main/images/ss_0_5_rests.png">
  <img width="300"src="https://raw.githubusercontent.com/AlgoMathITMO/SynEvaRec/main/images/ss_0_9_rests.png">
</p>

<p align="center">
  The least RMSE values (the vertical axis) for the chosen target RSs for different $\alpha_1$, $\alpha_2$ (with $\alpha_3 = 1 - (\alpha_1 + \alpha2)$ and step $\delta = 0.05$), sample_size (from left to right: 0.1, 0.5, 0.9) and the synthetic response function in the case of the Restaurants and Their Clients dataset. Colours indicate the RS providing the best quality (blue is for NMF, red is for SVD, yellow is for kNN).
</p>
  
## Requirements
Python 3.8 + all of the required packages.

## Installation
```
pip install poetry
poetry shell
poetry install
```

## Cite
```yaml
@inproceedings{provalov2021synevarec,
  title={SynEvaRec: A Framework for Evaluating Recommender Systems on Synthetic Data Classes},
  author={Provalov, Vladimir and Stavinova, Elizaveta and Chunaev, Petr},
  booktitle={2021 International Conference on Data Mining Workshops (ICDMW)},
  pages={55--64},
  year={2021},
  organization={IEEE}
}
```
