https://sites.google.com/a/uah.edu/tommy-morris-uah/ics-data-sets


la particularité de ce dataset, c'est qu'il y en a 15. Une pour chaque simulation.
On peut donc faire plusieurs choses pour les étudier :
- choisir une simulation à étudier, établir des scores
- mélanger les simulations, établir des scores
- étudier une simulation à la fois, établir des scores moyens

Ce choix doit etre en phase avec les tests réalisés dans les publications existantes.
Nous, on va faire les trois.

En effet, on va dans un premier temps faire des tests sur une simulation uniquement.
Puis, on va faire des tests sur l'ensemble des datasets.
Et enfin, on faire des tests sur chaque dataset puis faire un moyenne comme les auteurs des publications existantes.

j'ai séparé les tests en plusieurs notebooks pour plus de clarté.
les noms des notebooks commencent par le scaler utilisé. Car celui-ci est très important vu la présence des outliers dans les datasets.

les notebooks qui ne contiennent que "analyseAvecScalerX.ipynb" sont l'analyse d'une seule simulation avec le scaler précisé dans le titre
les notebooks qui ne contiennent que "analyseAvecScalerXPlusdonnes.ipynb" sont l'analyse de toutes les simulations mélangées.

les notebooks qui ne contiennent que "analyseAvecScalerXPlusdonnesOutlier.ipynb.ipynb" sont l'analyse des algos de outlier detection sur toutes les simulations mélangées.


Enfin, le notebook qui contient "..15 datasets moyenne.ipynb" est l'analyse de chaque simulation et établit un score moyen.
=> on fit un modèle sur chaque simulation, on établit un score. et au final faire une moyenne. (même méthode que les autres publications)


Chose à noter : les scores sont moins élevés si on mélange les simulations. donc en utilisant la même de 1 modèle pour chaque simulation (comme dans les publications), on obtient des scores plus élevés.

####################
Visualisation.ipynb

dans ce fichier:
#pre processing
#visualisation :
-histogrammes
-box plots (min max scaler puis quantile scaler)
-correlation
-ki square distance

=>on peut séparer les attaques des non attaques
=>les outliers sont présents en grand nombre
=>il y a des valeurs infinies qu'il faut remplacer
####################

##############
pour tous les autres notebooks:
-on fait du preprocessing (Nan, Infs, scaler)
-on prépare les datasets PCA, FeatureSelection
-puis on fait de la classification sur ces datasets ou bien de l'outlier
#############


=> on a pas testé overSampling




