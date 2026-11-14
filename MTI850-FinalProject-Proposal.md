# Projet final : Analyse de Big Data

# **Titre du projet :** Demande et rééquilibrage du réseau BIXI à Montréal

## 1\. Membres de l'équipe

* **Étudiant 1 :** Fortin Laurine, FORL79360401, laurine.fortin.1@ens.etsmtl.ca  
* **Étudiant 2 :** Beaugeois Carole, BEAC66310401, carole.beaugeois.1@ens.etsmtl.ca  
* **Étudiant 3 :** Elfassi Ethan, ELFE74350401, ethan.elfassi.1@ens.etsmtl.ca


  ## 2\. Cas d'usage du projet

* **Énoncé du problème:** Estimer la demande aux stations et identifier les périodes de surplus ou de pénurie probables à partir des données locales de mobilité, afin d'optimiser le rééquilibrage des vélos.  
* **Pertinence pour les Big Data:** Volume élevé d'historiques de trajets, métadonnées des stations, données météorologiques et calendrier.

  ## 3\. Description des données

  **Nom des jeux de données:** Historique des trajets BIXI et Données ouvertes de la Ville de Montréal (Météo/Transport).


  **Sources:**

* BIXI: [https\://bixi.com/en/open-data/](https://bixi.com/en/open-data/)  
* Portail de Montréal : [https\://donnees.montreal.ca/group/transport?organization=bixi](https://donnees.montreal.ca/group/transport?organization=bixi)  
  **Type de données:** Structurées et semi-structurées (fichiers CSV pour les trajets, JSON/CSV pour les métadonnées des stations et la météo).  
  **Volume:** Plusieurs années d'historique de trajets comprenant plus de 30 à 40 millions d'enregistrements (échelle du Go).  
  **Caractéristiques clés:** Heures et dates de début et de fin de trajet, identifiants des stations de départ et d'arrivée, capacité des stations, coordonnées géographiques, conditions météorologiques (température, précipitations) et informations liées au calendrier (jours fériés, fins de semaine).


  ## 4\. Tâche d'analyse proposée et méthodologie

* **Tâche analytique:**  
  * Régression: Prédiction des départs et des arrivées par station.

  **Méthodologie proposée :**

* **Outils:** Apache Spark (notamment PySpark pour le traitement de données à grande échelle et Spark Structured Streaming pour la simulation des trajets en direct), Hadoop (HDFS) pour l'infrastructure du lac de données (data lake).  
* **Bibliothèques:** Spark MLlib (pour l'apprentissage automatique distribué), scikit-learn / XGBoost (pour les modèles de régression de référence), Pandas et Matplotlib (pour l'analyse exploratoire initiale des données en local).  
* **Étapes:**  
  1. **Ingestion et prétraitement des données:** Cette étape consiste à charger et nettoyer l'historique des trajets BIXI. Ceci comprend les jointures entre les trajets, les métadonnées des stations, la météo et les calendriers et le traitement des valeurs nulles et manquantes. Nous regrouperons également les données par intervalle d’une heure par exemple.  
  2. **Ingénierie des caractéristiques (Feature Engineering):** Nous créerons des variables temporelles (heure de la journée, jour de la semaine, indicateurs de jours fériés), des variables météorologiques et des variables décalées (ex. demande à une station spécifique durant l'heure précédente).  
  3. **Sélection et entraînement des modèles:** Lors de cette phase, nous allons entraîner des modèles de régression et de séries temporelles (tels que Random Forest ou autres modèles vus en cours) pour prédire les départs et arrivées au niveau des stations. Nous utiliserons une validation croisée basée sur le temps afin de respecter l'ordre chronologique.  
  4. **Évaluation et mise à jour en continu:** Nous évaluerons enfin les performances du modèle avec des métriques telles que la RMSE (Root Mean Squared Error) et la MAE (Mean Absolute Error). Nous mettrons également en place un pipeline de streaming pour rejouer les trajets par ordre chronologique, mettre à jour la capacité des stations en temps réel et déclencher des alertes de rééquilibrage lorsque des seuils critiques sont atteints.

  ## 5\. Résultats attendus

* **Résultats escomptés:** Nous projetons d’obtenir une faible valeur de MAE pour les prédictions horaires de la demande pour fournir des prévisions fiables. Nous espérons aussi déployer avec succès un pipeline de streaming capable de traiter les événements de trajet et d'émettre en temps réel des alertes de rééquilibrage avec une latence minimale.  
* **Impact et portée:** Un modèle prédictif précis associé à un système d'alerte en temps réel permettrait à BIXI de passer d'une stratégie de rééquilibrage réactive à une stratégie proactive. Cela réduit les coûts logistiques de déplacement des vélos, diminue l'empreinte carbone des camions de rééquilibrage, améliore nettement la satisfaction des usagers en garantissant la disponibilité des vélos et des points d'ancrage, tout en soutenant les initiatives de mobilité durable de Montréal.  
  