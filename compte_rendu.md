# TP — Clustering avec K-means

## 1. Principe de K-means

K-means est un algorithme de **clustering non supervisé**.

Son objectif est de répartir les données en **K clusters** de manière à regrouper les points les plus proches.

### Étapes de K-means

1. Choisir le nombre de clusters **K**.
2. Initialiser **K centroïdes**.
3. Affecter chaque point au **centroïde le plus proche**.
4. Recalculer les centroïdes comme la moyenne des points de chaque cluster.
5. Répéter les étapes 3 et 4 jusqu'à convergence.

---

## 2. Inertie intra-cluster

L'inertie mesure la dispersion des points autour de leur centroïde.

$$
I = \sum_{k=1}^{K}\sum_{x_i \in C_k}
||x_i-\mu_k||^2
$$

Une inertie faible signifie que les points sont proches de leur centroïde.

Lorsqu'on augmente K, l'inertie diminue naturellement.

Cependant :

**Une inertie plus faible ne signifie pas forcément que le clustering est meilleur.**

Un K trop grand peut simplement découper les groupes naturels en plusieurs petits clusters.

Dans notre expérience, K=3 représente bien les trois groupes naturels présents dans les données.

---

## 3. Cardinalité des clusters

La cardinalité correspond au **nombre de points dans chaque cluster**.

Pour K=3, nous obtenons :

- Cluster 0 : 41 points
- Cluster 1 : 44 points
- Cluster 2 : 47 points

Total :

$$
41 + 44 + 47 = 132
$$

Tous les points du dataset sont donc affectés à un cluster.

---

## 4. Matrice de confusion

Une matrice de confusion nécessite de connaître les **classes réelles** des observations afin de les comparer aux classes prédites.

Le fichier `Data1.txt` contient 132 observations et seulement deux caractéristiques, sans colonne contenant les classes réelles.

Il n'est donc pas possible de calculer une véritable matrice de confusion avec les données fournies.

---

## 5. Formes fortes

Une **forme forte** est un ensemble de points qui restent toujours classés ensemble lorsque K-means est exécuté plusieurs fois avec différentes initialisations.

Nous avons exécuté K-means **25 fois** pour chaque valeur de K.

Résultats :

| K | Nombre de formes fortes |
|---|---:|
| 2 | 15 |
| 3 | **10** |
| 4 | 34 |
| 5 | 43 |

Le plus petit nombre de formes fortes est obtenu pour :

$$
K = 3
$$

avec **10 formes fortes**.

Les cardinalités obtenues pour K=3 sont :

`[36, 16, 24, 19, 11, 18, 3, 3, 1, 1]`

La somme des cardinalités est :

$$
36+16+24+19+11+18+3+3+1+1=132
$$

K=3 donne donc la partition la plus stable parmi les valeurs testées.

---

## 6. Frontières de décision

Comme K=3 présente le moins de formes fortes, les frontières de décision ont été représentées pour **K=3**.

Une grille de points a été créée entre **-1.8 et 1.8** avec un pas de **0.05**.

Chaque point de la grille est affecté au centroïde le plus proche.

Les zones obtenues représentent les différentes régions associées aux trois clusters.

Les frontières correspondent aux endroits où le centroïde le plus proche change.

---

## Conclusion

K-means est un algorithme de clustering non supervisé qui affecte chaque observation au centroïde le plus proche.

Dans notre dataset, K=3 est un choix adapté car :

- les données présentent trois groupes naturels ;
- K=3 donne une inertie nettement plus faible que K=2 ;
- augmenter davantage K réduit encore l'inertie mais fragmente les groupes ;
- K=3 présente le plus petit nombre de formes fortes parmi K=2,3,4,5 ;
- les frontières de décision obtenues avec K=3 séparent clairement les trois régions.

### À retenir

**K-means :**

K → Initialisation des centroïdes → Affectation des points → Recalcul des centroïdes → Répétition → Convergence

**Inertie :** mesure la dispersion des points dans les clusters.

**Cardinalité :** nombre de points dans un cluster.

**Forme forte :** ensemble de points toujours classés ensemble malgré différentes initialisations.

**Frontière de décision :** limite où le centroïde le plus proche change.