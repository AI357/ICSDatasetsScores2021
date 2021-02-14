lien pour le dataset : https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/6C3JR1


Comme il s'agit du premier dataset que j'ai étudié, les choses sont un peu désorganisés

Il faut noter avant tout que les meilleurs tests se trouvent dans "harvardDatasetGenerique"
en effet, les autres notebooks de test sont intérressants mais les scores ne sont pas élevés.
Cependant, dans CourbesPrediction et clusteringOutlier, les scores sont bons.

c'est donc sur ces trois notebooks qu'il faut se concentrer :
-CourbesPrediction
-clusteringOutlier
-harvardDatasetGenerique

les autres notebooks sont interessants mais les scores ne sont pas très bons



Aussi, certains notebooks utilisent un dataset qui contient les données statistiques extraites du dataset original.
Il se trouve que c'était une bonne idée mais l'utilisation de ce dataset ne donnera rien d'exceptionnel:




#################################################### 
le fichier harvardDatasetGenerique.ipynb
contient les tests principaux et renvoit vers les autres fichiers pour des test plus poussés
il y a dans ce fichier :
-load et pre processing du dataset
-visualisation et statistique
-visualisation avec pca
-classification avec pca très courte
-classification pour prédire les 21 classes
-classification pour prédire les 2 classes

-extraction des features des courbes des sondes :
    ## cela va nous permettre d'établir des nouvelles features basées sur le comportement des sondes 
    ## un nouveau dataset sera donc construit à partir des données statistiques du dataset existant
-classification avec 1 modèle 

-test régression
-tests saisonability et prédiction courbes

-tests correlation des variables (normal vs anormal) 
-extraction d'une liste contenant les sondes dont la correlation change le plus

-clustering
####################################################


####################################################
CourbesPrediction.ipynb
-étude des courbes et l'impact des attaques sur les courbes
-utilisation de méthode de prédiction
-comparaison des prédictions lors d'une "anomalie" vs quand c'est normal
####################################################

####################################################
clusteringOutlier.ipynb

on fait du novelty detection avec le dataset original et des données PCA (15 dimensions)
on applique ensuite des algorithmes de novelty detection

puis on fait du clustering mais cela fontionne moins bien

####################################################

####################################################
GenerationDataSetCorrelation.ipynb
-étude de la correlation pour chaque anomalie => correlation plus forte lorsque anomalie
=> les variables correlés sont souvent reliés par un processus physique

-extraction des noms des variables qui ont la plus forte correlation lors des anomalies
=> on va se servir de ces données dans  :
-generationDatasetExtractedFeatureWithCorr.ipynb
-GenerationDataSetMixExtractedFeaturesAndPca.ipynb
-classificationWithExtractedFeatures.ipynb
-classificationWithExtractedFeaturesHybridMethod.ipynb
####################################################

####################################################
generationDatasetExtractedFeatureWithCorr.ipynb
dans ce fichier, on créer un nouveau dataset à des doonées statistiques sur les courbes des sondes
-on espère alors pouvoir d'écrire un comportement anormal grace aux stats
-les labels ne changent pas, car le dataset contruit correspond exactement à l'original.

=> on utilise ce dataset pour faire de la classification dans :
-classificationWithExtractedFeatures.ipynb
-classificationWithExtractedFeaturesHybridMethod.ipynb

####################################################
GenerationDataSetMixExtractedFeaturesAndPca.ipynb

dans ce fichier, on vient généré un dataset qui est
exactement le même que le dataset des données brutes, mais on a que 3 samples par simulation. Comme le dataset des statistiques
# voir GenerationDataSetMixExtractedFeaturesAndPca.ipynb

en effet, dans le dataset ALLDFStatsExtractedWithCorr, on a extrait des statistiques à partir des données des courbes sur une période de temps. Cette période de temps est de 3 par simulation.

si on veut utiliser du pca en meme temps que ce dataset, il faut avoir seulement 3 données par simulation
c'est la seule chose que l'on fait dans ce fichier.

####################################################




####################################################
classificationWithExtractedFeatures.ipynb

#on utilise le dataset créé  dans generationDatasetExtractedFeatureWithCorr
#on fait de la classification (21 sorties)
#puis de la classificaiton avec 2 sorties (normal / anormal) => les scores sont bons
#on fait 52 modèles (1 pour chaque variable) pour 21 sorties => les score sont très bofs
#on fait 52 modèles (1 pour chaque variable) pour 2 sorties => les score sont bons


#enfin, on fait 52 models, 1 pour chaque variable et un système de vote pour avoir 1 seul résultat
# pour 2 sorties => le score est très bon
# pour 21 sorties => le score est bof

####################################################


####################################################
classificationWithExtractedFeaturesHybridMethod.ipynb

dans ce notebook, on utilise deux datatsets:
-on utilise le dataset créé  dans generationDatasetExtractedFeatureWithCorr
-et on utilise un dataset identique à l'original mais qui contient que 3 observations par simulation

=> on essaye de trouver un modèle de clustering qui fonctionne bien avec le second datasetù
=> on créer 52 modèles de ML (1 par sonde) et un système de vote
=====>on combine les deux pour avoir un résultat

malheureusement ca fonctionne que bof


####################################################

