# Analyse de survie au cancer du sein (TCGA-BRCA)
lien vers le projet : https://rpubs.com/Mounadey/1399013
 

## Présentation du projet

Ce projet réalise une analyse de survie sur la cohorte publique TCGA-BRCA (The Cancer Genome Atlas - Breast Cancer), qui regroupe les données cliniques de plus de 1000 patients atteints d'un cancer du sein.
L'objectif est d'identifier les facteurs cliniques et biologiques qui influencent la survie des patients, en utilisant des méthodes statistiques adaptées aux données de survie et aussi de faire une première prise en main des outils d'analyse de survie comme les courbes de Kaplan et le modèle de Cox multivariée.

## Problématique de notre projet 

**Quels facteurs influencent la probabilité de survie des patients atteints d'un cancer du sein, et dans quelle mesure ?**

## Données

- **Source** : TCGA-BRCA via le package R `TCGAbiolinks`
- **Population** : 1035 patients (98.7% de femmes, 1.3% d'hommes)
- **Événement d'intérêt** : décès (103 décès observés, soit 10% de la cohorte)
- **Suivi** : de 1 jour à 232 mois (~19 ans)

## Méthodes utilisées

- **Kaplan-Meier** : estimation de la probabilité de survie au cours du temps, par groupes
- **Modèle de Cox multivarié** : identification des facteurs pronostiques indépendants

## Variables d'intérêt

### Stade tumoral (AJCC)
Le stade tumoral décrit l'étendue du cancer au moment du diagnostic. Il est classé de I à IV :
- **Stade I** : tumeur localisée, petite taille, pas d'atteinte ganglionnaire
- **Stade II** : tumeur plus grande ou légère atteinte ganglionnaire
- **Stade III** : atteinte ganglionnaire importante ou tumeur localement avancée
- **Stade IV** : présence de métastases à distance (os, poumons, foie...)

Plus le stade est élevé, plus le pronostic est sombre. C'est l'un des facteurs pronostiques les plus importants en oncologie.

### Statut ER (Récepteurs aux Œstrogènes)

> certaines cellules cancéreuses ont des "antennes" sensibles aux œstrogènes (une hormone féminine). Si la tumeur possède ces antennes, on dit qu'elle est ER+. On peut alors lui donner un médicament qui bloque ces antennes et ralentit sa croissance. Si elle n'en a pas (ER-), ce traitement ne fonctionne pas et la tumeur est souvent plus agressive.

- **ER+** : tumeur sensible aux œstrogènes, répond aux thérapies hormonales. Pronostic généralement meilleur.
- **ER-** : tumeur ne répondant pas aux thérapies hormonales. Souvent plus agressive.


### Statut HER2

>  HER2 est une protéine qui agit comme un "accélérateur" de croissance pour les cellules. Certaines tumeurs en produisent trop — on dit qu'elles sont HER2+. Ces tumeurs grandissent plus vite, mais il existe des médicaments spécifiques (comme l'Herceptin) qui bloquent cet accélérateur.

- **HER2+** : tumeur qui se développe rapidement, mais répond aux thérapies ciblées (ex. trastuzumab)
- **HER2-** : absence de surexpression, évolution généralement moins agressive


## Résultats principaux de notre analyse 

- La survie globale est favorable : médiane de survie ~125 mois (~10 ans)
- Le stade tumoral est le facteur le plus discriminant visuellement : les patients au stade IV survivent significativement moins longtemps
- Le statut ER+ est protecteur : réduit le risque de décès de 45%
- Le statut HER2+ est un facteur de risque : presque double le risque de décès
- L'âge au diagnostic est significatif : chaque année supplémentaire augmente légèrement le risque

## Outils

- **R** avec les packages : `TCGAbiolinks`, `survival`, `survminer`, `dplyr`, `ggplot2`


## Ressources

### Méthodes statistiques utilisées 

projet inspiré d'après une auto-formation au travers de ces différents canaux :
- [Webin-R #15 — Analyse de survie](https://youtu.be/3XLx1SHc2fw) 
- [STHDA — Survival Analysis Basics](http://www.sthda.com/english/wiki/survival-analysis-basics) 
- [STHDA — Cox Proportional Hazards Model](http://www.sthda.com/english/wiki/cox-proportional-hazards-model) 
- [DellaDara — Analyses de survie et modèles de Cox](https://delladata.fr/analyses-survie-modeles-de-cox/) 
- [Estimateur de Kaplan-Meier](https://fr.wikipedia.org/wiki/Estimateur_de_Kaplan-Meier)

### Variables biologiques
- [Récepteur des œstrogènes](https://fr.wikipedia.org/wiki/R%C3%A9cepteur_des_%C5%93strog%C3%A8nes)
- [HER2](https://fr.wikipedia.org/wiki/HER2)
- [Cancer du sein](https://fr.wikipedia.org/wiki/Cancer_du_sein)
