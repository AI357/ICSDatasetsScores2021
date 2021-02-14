

##########
#########   dans wadi.ipynb
###########

dans un premier temps, on observe les valeurs du dataset sans scaler mais cela ne donne rien donc on passe directement à un 
quantiletransformer scaler qui semble etre très adapté.

visualisation :
=> donne des bons résultats, on peut voir une différence entre les observations normales et les attaques
=> deplus, l'utilisation du scaler semble etre bonne


#outlier detection

=> donne des scores corrects surtout LOF

#classification

=> donne des scores très bons



####### 
on essaye de faire des tests avec robust scaler
=> LOF obtient un bon score
=> classificaiton est la même
=> clustering fonctionne pas 

##########
#########   dans WadiPcaTests.ipynb
###########

dans ce fichier on fait juste du outlier detection et de la classification avec PCA
=> ca ne donne rien de mieux que sans le PCA


