# Premier League Player Clustering

[![Python](https://img.shields.io/badge/Python-3-3776AB?logo=python&logoColor=white)](https://www.python.org)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-K--Means-F7931E?logo=scikitlearn&logoColor=white)](https://scikit-learn.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

Unsupervised clustering of Premier League 2024/25 player statistics to find performance profiles with K-Means.

## Table of Contents

- [About](#about)
- [Dataset](#dataset)
- [Method](#method)
- [Getting Started](#getting-started)
- [Documents](#documents)
- [Team](#team)
- [License](#license)

## About

Applied Project II of the Data Science program at Universidade Presbiteriana
Mackenzie (2025, second semester). The goal was to find patterns in individual player
performance and the factors behind it, grouping players with similar statistical
profiles regardless of their listed position. Part of a series with
[Applied Project I](https://github.com/EnzoFerroni/spotify-2024-eda),
[III](https://github.com/EnzoFerroni/tech-job-recommender) and
[IV](https://github.com/EnzoFerroni/projeto-aplicado-iv-energia-solar). The report and
notebook are in Portuguese.

## Dataset

[FBRef Premier League 2024/25 player stats](https://www.kaggle.com/datasets/siddhrajthakor/fbref-premier-league-202425-player-stats-dataset)
(Kaggle): one row per player with goals, assists, shots, expected goals (xG, xAG),
progressive passes and carries, tackles, interceptions and more. A copy is stored in
[`data/`](data/).

## Method

1. **Feature selection.** Keep only numeric performance metrics, dropping identifiers
   such as name, nation, squad, age and appearances. Missing values become 0, since an
   empty stat means the action did not happen.
2. **Scaling.** `StandardScaler`, so every metric weighs the same in K-Means.
3. **Exploration.** Goal distribution and a correlation heatmap of attacking metrics.
4. **Choosing k.** Elbow method, then K-Means (`k-means++`, `n_init=10`).
5. **Validation.** Silhouette, Calinski-Harabasz and Davies-Bouldin scores.
6. **Interpretation.** Centroids converted back to real units, an interactive Plotly
   radar chart comparing cluster profiles, and a PCA scatter plot showing how the
   clusters separate.

## Getting Started

The notebook was written for Google Colab and downloads the dataset with the Kaggle
API (it asks for your `kaggle.json`). To run it locally with the CSV in `data/`:

```bash
git clone https://github.com/EnzoFerroni/premier-league-player-clustering.git
cd premier-league-player-clustering
pip install pandas numpy scikit-learn matplotlib seaborn plotly jupyter
jupyter notebook notebooks/Analise_Clusterizacao_PremierLeague.ipynb
```

Then skip the Kaggle download cells and point the CSV path to
`data/fbref_PL_2024-25.csv`.

## Documents

- Report: [`reports/PROJETO APLICADO II.pdf`](reports/)
- Slides: [`reports/apresentacao_v1.pdf`](reports/apresentacao_v1.pdf)
- Presentation video: [YouTube](https://www.youtube.com/watch?v=_Lns3mSD3Bc)

## Team

| Name | GitHub |
| --- | --- |
| Daniel dos Santos da Silva | [@Daniels-S](https://github.com/Daniels-S) |
| Enzo Ferroni | [@EnzoFerroni](https://github.com/EnzoFerroni) |
| Fernanda Guanaes Aroca | [@FernandaAroca](https://github.com/FernandaAroca) |
| Vinícius de Souza Sabiá | [@viniciussabia](https://github.com/viniciussabia) |

Fork of the team repository [Daniels-S/Projeto_Aplicado_II](https://github.com/Daniels-S/Projeto_Aplicado_II).

## License

Code and documents are released under the [MIT License](LICENSE). Copyright (c) 2025
Daniel dos Santos da Silva, Enzo Ferroni, Fernanda Guanaes Aroca and Vinícius de Souza
Sabiá. The dataset belongs to its Kaggle author and is redistributed under its original
terms.
