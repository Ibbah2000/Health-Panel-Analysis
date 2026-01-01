# Analyse Économétrique : Déterminants de l'Espérance de Vie 🌍🏥

Ce projet réalise une analyse économétrique sur données de panel pour étudier l'impact des facteurs économiques et sanitaires sur l'espérance de vie à la naissance dans 193 pays.

## 📋 Description du Projet

L'objectif est de modéliser l'espérance de vie en fonction de variables clés comme le PIB, l'éducation et la prévalence de certaines maladies. L'étude couvre la période **2000-2015** et compare différentes approches économétriques (MCO poolés vs Effets Fixes).

Les données proviennent du *Global Health Observatory* (OMS) et des Nations Unies.

## 📂 Structure du Dépôt

* `Panel_sante.Rmd` : Le code source RMarkdown contenant l'intégralité de l'analyse (nettoyage, modélisation, tests).
* `Panel_sante.pdf` : Le rapport final généré (Output).
* `Life Expectancy Data.csv` : La base de données brute.
* `README.md` : Ce fichier de documentation.

## 📊 Variables de l'Étude

Voici les variables retenues et renommées pour l'analyse :

| Variable (Code R) | Définition | 
| :--- | :--- | :--- |
| **esp_vie** | Espérance de vie à la naissance |
| **Pib** | PIB par habitant  |
| **Educ** | Taux de scolarisation ) |
| **Hiv** | Prévalence du VIH/SIDA (15-49 ans)
| **Polio** | Couverture vaccinale Polio (1 an)  
| **Statut** | Niveau de développement | 0 = En développement, 1 = Développé |

> **Note technique :** La variable `Statut` (invariante dans le temps) est utilisée pour les statistiques descriptives mais est retirée du modèle à Effets Fixes (Within) pour éviter la collinéarité parfaite.

## 🛠️ Méthodologie

L'analyse suit les étapes suivantes :
1.  **Nettoyage des données :** Traitement des valeurs manquantes et renommage des variables.
2.  **Statistiques descriptives :** Analyse univariée et bivariée.
3.  **Modélisation :**
    * Estimation par MCO (Pooled OLS).
    * Estimation par Effets Fixes (Modèle Within via `plm`).
4.  **Tests de spécification :**
    * Test de Fisher (F-test) pour confirmer la présence d'effets individuels.
    * Test de Hausman pour l'arbitrage Effets Fixes vs Aléatoires.

## 💻 Prérequis et Installation

Pour reproduire cette analyse, vous avez besoin de **R** et **RStudio**.

Les packages R suivants sont nécessaires :
```r
install.packages(c("plm", "lmtest", "ggplot2", "rmarkdown", "knitr"))
