# Segmentation Stratégique Client par CLV et Risque d'Attrition — Secteur Télécom (Bénin)

> 20% des clients génèrent 46% du revenu total — ce projet transforme cette réalité en outil de priorisation actionnable pour les équipes de rétention.

##  Contexte

Les opérateurs télécoms traitent souvent tous leurs clients à risque de départ de la même façon, sans distinguer leur valeur réelle. Ce projet propose une approche combinant **profil actuel des clients** et **projection de leur valeur future (CLV)**, sur un dataset simulé représentatif du marché télécom béninois (1 million de clients).

##  Ce que couvre le projet

1. **Exploration des données (EDA)** — profil client, distribution de l'ARPU, analyse Pareto
2. **Feature Engineering** — construction de la tendance ARPU sur 6 mois, encodage des variables catégorielles
3. **Modélisation comparée** — Régression Logistique, Random Forest et XGBoost, avec recherche d'hyperparamètres (RandomizedSearchCV) et interprétabilité (SHAP)
4. **Calibration des probabilités** — correction du biais introduit par la pondération des classes, nécessaire pour un usage financier fiable
5. **Calcul de la Customer Lifetime Value (CLV)** — projection sur 12 mois pondérée par la probabilité cumulée de rétention
6. **Segmentation stratégique** — matrice CLV × Risque de churn (4 quadrants)
7. **Dashboard Power BI** — restitution en 4 pages (Vue d'ensemble, Analyse du Churn, Présent, Futur)

##  Stack technique

Python (pandas, numpy, scikit-learn, XGBoost, SHAP) · Power BI (DAX) · Google Colab

##  Résultats clés

| Indicateur | Valeur |
|---|---|
| Recall du modèle retenu (XGBoost) | 78,8% |
| AUC-ROC | 0,865 |
| CLV moyenne (12 mois) | ~21 800 FCFA |
| Concentration du revenu | 20% des clients → 46% du revenu |
| Segment prioritaire | Haute valeur - Haut risque : 10,6% des clients, 17,4% du revenu |

##  Aperçu du dashboard

![Vue d'ensemble](dashboard/dashboard_screenshots/01_vue_ensemble.png)
![Analyse du Churn](dashboard/dashboard_screenshots/02_analyse_churn.png)
![Présent](dashboard/dashboard_screenshots/03_present.png)
![Futur](dashboard/dashboard_screenshots/04_futur.png)

##  Limites du projet

- Dataset **synthétique**, faute d'accès à des données opérateur réelles (confidentielles) — les ordres de grandeur (ARPU, taux Mobile Money, disparité urbain/rural) sont calibrés pour être plausibles, pas vérifiés
- Le modèle est entraîné et validé sur un dataset "Historique" distinct du dataset "Production" scoré, pour reproduire fidèlement une logique de déploiement réel

##  Reproduire le projet

1. Ouvrir `notebook/analyse_clv_segmentation.ipynb` dans Google Colab
2. Exécuter les cellules dans l'ordre (génération du dataset → EDA → modélisation → CLV → segmentation → export)
3. Importer le CSV exporté dans Power BI Desktop pour explorer le dashboard

##  Auteure

AGO Parfaite Marie Immaculée — Master 2 Intelligence Artificielle et Big Data (PIGIER Bénin, mention très bien)
