# Lineaire_Haies_PACAGE
QGIS 3.x plugin to calculate the length of hedges linked to farmers's plots with "PACAGE" code


Lineaires_haies_pacage  
Ce plugin est conçu pour les agents du Service Economie Agricole et Environnement des Exploitations de la DDT souhaitant disposer dans Qgis_3
d'une fonctionnalité dédié à l'instruction des demandes de modifications des linéaires de haies, à partir des couches téléchargées sur ISIS (TELEPAC).
L'outil calcule la somme totale des longueurs de haies pour l'ensemble de parcelles ayant un certain numero PACAGE.
Les parcelles étant sélectionnées par intersection entre les polygones des deux couches:
Pour télécharger les données:                                                                 
https://isis.telepac.agriculture.gouv.fr/telepac/auth/accueil.action

Une fois login et mdp renseignés, on va dans Extractions de données.
Pour la campagne de l'année en cours on télécharge deux couches :
  - SURFACES ANNEE - PARCELLES GRAPHIQUES CONSTATEES 
qui contient les numéros de pacage attribut 'PACAGE'
  - SURFACES ANNEE - SNA de reference dont utilisera la table SNA-DE-REFERENCE-2024_021_VG.shp
qui contient les longueurs de haies - attribut 'LONGUEUR' 
et aussi les surfaces de haies - attribut 'SURF_ADM' dont on se servira quand LONGUEUR est null ! 
On décompresse dans 'W:/5_AUTRES_DONNEES/AGRICULTURE/TELECHARGEMENT_TELEPAC/
A partir de  de SNA-DE-REFERENCE-2024_021_VG.shp, on crée la couche SNA-DE-REFERENCE-2024_021_VG_HAIE_ONLY.shp"
pour l'attribut 'TYPE' like 'Haie' 
On crée encore dans SNA-DE-REFERENCE-2024_021_VG_HAIE_ONLY.shp avec QGIS un attribut 'long_m' avec to_real(LONGUEUR) 
On remplace enfin dans long_m les valeurs nulle par round($area/LARGEUR)
On utilise enfin encore la cocuhe Haies de la BDTOPO en vigueur
les chemins vers ces couches et la couche scan 25 qui permet les exports cartogreaphiques sont à renseigner dans le corps du plugin avant de pouvoir l'utiliser:
Il s'agit des lignes 97 à 102 du fichier dlgBox_LHP.py
