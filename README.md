# K-means Clustering

Travail pratique sur l'algorithme de clustering non supervisé **K-means**.

## Objectifs

- Comprendre le fonctionnement de K-means
- Implémenter K-means avec Python et NumPy
- Étudier différentes valeurs de K
- Calculer l'inertie intra-cluster
- Étudier la cardinalité des clusters
- Étudier la stabilité avec les formes fortes
- Représenter les frontières de décision

## Dataset

Le fichier `Data1.txt` contient :

- 132 observations
- 2 caractéristiques
- données générées à partir de 3 distributions gaussiennes

## Expériences

K-means a été testé avec :

`K = 2, 3, 5, 10, 15, 20`

L'inertie diminue lorsque K augmente. Cependant, une inertie plus faible ne signifie pas nécessairement un meilleur clustering, car un grand K peut fragmenter les groupes naturels.

## Formes fortes

K-means a été exécuté 25 fois avec différentes initialisations.

| K | Nombre de formes fortes |
|---|---:|
| 2 | 15 |
| 3 | 10 |
| 4 | 34 |
| 5 | 43 |

K=3 présente le plus petit nombre de formes fortes parmi les valeurs testées.

## Frontières de décision

Les frontières de décision ont été représentées pour K=3.

Chaque point du plan est affecté au centroïde le plus proche.

## Technologies

- Python
- NumPy
- Matplotlib
- Jupyter Notebook