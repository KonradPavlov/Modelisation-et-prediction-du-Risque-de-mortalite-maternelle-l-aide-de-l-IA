# MediRisk : Système de Prédiction du Risque Maternel

**PROJET 2 : Modélisation et Prédiction du Risque de Mortalité Maternelle à l'aide de l'IA**

Ecole d'Eté sur l'Intelligence Artificielle — EEIA BENIN EXCELLENCE
Fondation VALLET / BE / PNUD

> Utiliser l'Intelligence Artificielle pour prédire les grossesses à risque, aider le personnel médical à mieux décider, et réduire la mortalité maternelle.

## Sommaire

- [Objectifs](#objectifs)
- [Matériels](#matériels)
- [Méthodologie](#méthodologie)
- [Résultats](#résultats)
- [Structure du projet](#structure-du-projet)
- [Etape 1 — Entraîner et exporter le modèle](#etape-1--entraîner-et-exporter-le-modèle)
- [Etape 2 — Lancer l'interface web](#etape-2--lancer-linterface-web)
- [Etape 3 — Utiliser l'interface](#etape-3--utiliser-linterface)
- [Conclusion](#conclusion)
- [Technologies](#technologies)
- [Participants](#participants)

## Objectifs

- Utiliser l'Intelligence Artificielle pour prédire les grossesses à risque.
- Améliorer la prise de décision clinique pour le personnel médical.
- Réduire la mortalité maternelle.

## Matériels

**Source des données :** Kaggle

| Effectif | Nombre |
| --- | --- |
| Effectif brut | 679 données cliniques / 677 patients cliniques |
| Effectif final analysé | 337 (après suppression des doublons cliniques) |

## Méthodologie

**1. Préparation des données :** nettoyage d'une cohorte de patients (déduplication des enregistrements identiques, traitement des valeurs manquantes et aberrantes) sur les indicateurs cliniques : tension artérielle, glycémie, température, fréquence cardiaque.

**2. Feature engineering & split :** normalisation des variables cliniques (Min-Max Scaling) et séparation train/test stratifiée (80/20) pour préserver la proportion réelle des classes à risque et éviter toute fuite de données entre entraînement et évaluation.

**3. Analyse descriptive :** importance des variables.

**4. Modélisation :** deux modèles de classification (Régression Logistique, Random Forest) ont prédit le niveau de risque des patientes. Le Random Forest a surpassé la régression logistique avec 98,5% de précision sur le jeu de données test (AUC = 1,00), la glycémie (BS) étant le facteur le plus discriminant.

## Résultats

**Évaluation du Risque de Mortalité Maternelle**

| Paramètre | Valeur |
| --- | --- |
| Âge | 28 ans |
| Tension artérielle | 120 mmHg |
| Glycémie (BS) | 92 mg/dL |
| Température
