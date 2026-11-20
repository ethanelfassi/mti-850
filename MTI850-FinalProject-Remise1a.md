# **MTI850 – Analytique des données massives Projet final A26 Livrable partiel 1 : Compréhension et préparation des données** 

Un _notebook Jupyter_ comprenant l'ingestion de données, le nettoyage, l'analyse exploratoire, la visualisation et la préparation des fonctionnalités avec des cellules de code fonctionnelles, précédées de cellules _markdown_ expliquant ce qui est fait dans chaque cellule/étape. 

[ _S'il vous plaît, essayez de structurer votre notebook comme ceux que vous avez complétés dans les PD_ 1 _à_ 4.] 

# **Structure suggérée** 

## **1. Présentation du problème et description des données** 

Vous devriez brièvement reformuler le contenu de leur proposition : 

- **Énoncé du problème :** Décrivez la question d'affaires ou de recherche abordée. 

- **Pertinence pour le Big Data :** pourquoi ce problème bénéficie de l'analyse des mégadonnées (par exemple, volume de données, hétérogénéité). 

- **Description de l'ensemble de données :** 

   - Nom et source du jeu de données (Kaggle, API, etc.) 

   - Type et taille des données 

   - Variables clés et colonne(s) cible(s) 

## **2. Ingestion de données** 

Chargez les données à partir de fichiers locaux, HDFS ou cloud **Tâches :** 

- Démarrer la session Spark 

- Chargez l'ensemble de données en utilisant `spark.read` 

- Inspectez le schéma et quelques lignes 

- Version brute stockée dans HDFS (optionnel) 

[ _S'il vous plaît, souvenez-vous que vous devez me donner accès à vos données. Veuillez inclure dans le notebook une URL (Google Drive, One Drive, etc.) pour télécharger vos données sur ma machine._ ] 

## **3. Nettoyage et prétraitement des données** 

Traitez les questions de qualité des données : 

- Gérer les valeurs manquantes ( `na.fill, dropna` ou imputation) 

- Supprimer les doublons 

- Types de corrections ou étiquettes incohérentes 

- Identifier les valeurs aberrantes (optionnel) 

- Etc. 

## **4. Analyse exploratoire des données** 

Prenez de petits échantillons ( `toPandas()` ) et visualisez des motifs ou corrélations. Créer des graphiques et des visualisations 

## **5. Sélection des caractéristiques et ingénierie** 

- Sélectionnez les variables pertinentes pour résoudre votre problème d'affaires ou de recherche. 

- Créer des caractéristiques dérivées (par exemple, ratios, agrégats, transformations de texte) 

- Encoder des variables catégorielles (par exemple, `StringIndexer` ) 

- Assembler des caractéristiques en un seul vecteur 

## **6. Sauvegarder les données préparées** 

Sauvegardez les données de caractéristiques prétraitées pour la prochaine phase (dans `parquet` ). 

## **Artéfacts attendus livrables** 

1. _Notebook Jupyter_ avec le code et les cellules de _markdown_ expliquant le problème, l'ensemble de données et les étapes de prétraitement. 

2. Sortie attendue de votre _notebook_ : Un DataFrame Spark ( `df_features` ) contenant toutes les fonctionnalités pertinentes, prétraitées et conçues. Ce DataFrame servira d'entrée pour la prochaine phase (modélisation et évaluation). 

3. Dossier de sortie HDFS : `df_features.parquet` 

