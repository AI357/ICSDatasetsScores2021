
###################### pour les datasets ####

Dans ce répertoire, il y a de nombreux datasets:
-BATADAL_test_dataset => dataset de test dans labels  (contient des attaques)// dans les notebook, on appelle ce dataset le dataset competitif car on ne fit pas dessus
-BATADAL_test_dataset_label =>dataset de test avec labels (contient des attaques)// dans les notebook, on appelle ce dataset le dataset competitif car on ne fit pas dessus
-BATADAL_dataset03 => dataset de train (ne contient pas d'attaques)
-BATADAL_dataset04  => dataset de test (contient des attaques avec des labels et d'autres dans les labels)// dans les notebooks, on appelle ce dataset le dataset de test NON compétitif, car on peut éventuellement faire des fits dessus. Il n'est pas utilisé pour réaliser les scores.


-BATADAL_dataset04_FullyLabeledA  => le dataset "BATADAL_dataset04" n'ayant pas des labels sur toutes les attaques, j'ai labélisé à la main les attaques.
-BATADAL_dataset04_FullyLabeled   => il sagit de deux datasets de train, surtout pas de test



##principe des scores :
selon le site web des créateurs de ce dataset, on ne peut pas fit nos modèles sur le dataset de test compétitif (BATADAL_test_dataset), et on doit établir nos scores de détection sur ce dataset (BATADAL_test_dataset).
nous verrons au cours de l'étude de ces datasets que cela pose problème car la différence entre le dataset de train, de test non compétitif et compétitif est grande. (paramétres initiaux)


Les fichiers .csv qui contiennent le mot "result" (ex: resultT2.csv ) sont les prédictions des modèles sur le dataset de test compétitif.
dans le but d'avoir un score global (modèle ensembliste) de toutes les solutions, il faut extraire toutes les prédictions de tous les modèles pour ensuite les regrouper.
Une fois que l'on a créer tous ces datasets de résultats, on les transfère dans le dossier "resultModels", et dans le notebook "final result" de ce dossier, on rassemble tous ces datasets de scoring




#############################   Pour les notebooks :    ####################################
############################################################################################
Les fichiers  =====>   sont les notebooks génériques.

#!!! les étapes de visualisation du dataset sont principalement réalisées dans ces notebooks !!!#


Generique_batadalQuantileScaler.ipynb :

#on fait de la visualisation puis on applique de quantil scaler
#on fait du outlier detection et on obtiznt des scores moyens
#on fait de la classification et on obitent des scores nuls
=> car la différence entre le dataset de train et celui de test est trop forte
#on fait de l'over sampling => ne donne rien de mieux
#on fait du PCA mais cela ne donne rien non plus


Generique_batadalTestRobustScaler.ipynb


#on fait de la visualisation puis on applique de Robust scaler
#on fait du outlier detection et on obtiznt des scores moyens/bons (elliptic envelope)
#on fait de la classification et on obitent des scores nuls
=> bien que la visualisation soit moins bonne avec ce scaler, les scores sont mieux que avec le quantile scaler



Generique_batadalTestSansScaler.ipynb      

#on fait de la visualisation 
#on fait du outlier detection et on obtiznt des scores moyens
#on fait de la classification et on obitent des scores nuls


############################################################################################
les fichiers
batadal_fenetre_points_Large_FacilementContamine_RobustScaler.ipynb
batadal_fenetre_points_Large_RobustScaler.ipynb
batadal_fenetre_points_noscaler.ipynb
batadal_fenetre_points_RobustScaler.ipynb
batadal_fenetre_points_standartscaler.ipynb

pour ces fichiers, on assemble plusieurs points sur une fenetre temporelle pour avoir un grand nombre de features et ainsi, on espère baisser le taux de faux positifs.
Attention, dans ces fichiers, on fait pas de visualisation car on a déjà fait cette étape dans les notebooks génériques.

pour ces fichiers
#on fait du pre processing (robust scaler, standartscaler)
#on crée une fenetre plus ou moins grande en fonciton du notebook (contient le mot "large")
#on fait ensuite du outlier detection
#on fait ensuite de la classificaiton
#on fait ensuite de la réduction de dimention (pca, kernelpca, FactorAnalysis etc.) 

=> la réduction de dimention ne donne rien :/
=> fenetre large donne des bons résultats 


############################################################################################



############################################################################################
Prédiction des valeurs continues :
batadal_timeSeries.ipynb

#dans un premier temps, on charge les valeurs et on vérifie les nan etc ...
#on fait une courte étude des valeurs discrètes 
#on fait une étude des courbes (valeurs des variables sur une fenetre temporelle) pour savoir à quoi on a à faire
=>on observe qu'il est difficile de voir une difference entre attaque / on -attque juste avec les courbes
#on fait une étude sur la réduction de bruit (frequence smoothing)
#on regarde la saisonabilité des données => selon moi, pas exploitable


#on fait des groupes de varialbes qui sont sur le meme process physique (plus ou moins)
#on applique la meme méthode pour tous les groupes de données :
-on contruit un modèle MLP et on le test sur une attaque qui se produit sur son process physique
-on construit ensuite une méthode afin de lever une alerte si on pense que il y a une attaque,
pour cela, on regarde la différence de prédition avec la réalité. si cette différence est grande, il s'agit surement d'une attaque. en fonction de cette différence, on peut faire des prédictions.


############################################################################################



############################################################################################
pour ces fichiers, on réalise des matrices de correlation avec une fenetre de 15 20 35 points


batadalCorrelationFenetre20points.ipynb
batadalCorrelationFenetre35points.ipynb

#pour ces deux datasets, on applique un quantile scaler
#on crée ensuite trois datasets de correlation (train, test non compétitif, competitif)
#on fait ensuite de la classification et du outlier detection


batadalCorrelationFenetre15points.ipynb
#meme chose sans le scaler



la meilleure longueur pour appliquer cette méthode est 20


############################################################################################

############################################################################################
Dans ce notebook, on sépare les variables en fonction de leur répartition géographique pour faire de la détection d'outliers locaux
Batadal_noveltyDetection_Locaux.ipynb

#dans un premier temps, on cherche les valeurs nan, infs etc..
#on utilise un StandardScaler pour normaliser les valeurs

#on fait ensuite des groupes de valeurs par région géographique

#pour chaque groupe de variables, on fait une fenetre de 3 points puis on fait du outlier detection

############################################################################################




