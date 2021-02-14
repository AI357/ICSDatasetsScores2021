lien du dataset : https://sites.google.com/a/uah.edu/tommy-morris-uah/ics-data-sets


dans un premier temps, on régle les soucis des valeurs Nan. 
on vérifie aussi les valeurs infs, etc.

On observe ensuite le dataset sans scaler mais cela n'est pas possible donc on applique un quantile scaler.

### quantile scaler
on peut observer les valeurs en fonction de (attaque/non attaque) mais il est difficile de les séparer à l'oeil nu.


si on applique les aglo de classification, on obtient des bons résultats avec des algos simples
mais c'est avec le stackingboosting classifier qu'on obtient des très bon résultats 

-outlier detection ne donne rien


## quantile scaler

##quantile min max

on observe pas vraiment des améliorations dans la visualisation des valeurs 
les scores sont bons mais plus faibles que avec le scaler quantile

les algos Outlier detection ne fonctionnent pas
le clustering non plus

on essaye de remplacer les valeurs Nan par des valeurs aléatoire mais cela ne boost pas les scores

## quantile min max






nous n'avons pas essayé :
-pca
-oversampling
-undersampling
-feature engineering => avec 20 variables c'est inutile
