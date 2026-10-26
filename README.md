# MediRisk — Système de Prédiction du Risque Maternel

Projet EEIA · Bénin Excellence / PNUD / Fondation Vallet

## Structure du projet

Projet EEIA/
├── projet eeia-Copy1.ipynb          ← Notebook d'entraînement du modèle
├── Maternal_Health_Risk_Data_Set_Modified.csv  ← Données d'entraînement
├── app.py                           ← Serveur Flask (optionnel)
└── interface/
    ├── index.html                   ← Interface web principale
    ├── app.js                       ← Logique frontend + inférence ML
    ├── style.css                    ← Styles
    └── model.json                   ← Modèle Random Forest exporté à régénérer

## Étape 1 — Entraîner et exporter le modèle (Jupyter)

À faire une seule fois (ou chaque fois que tu changes les données).

### 1.1 Ouvrir le notebook

Lance Jupyter Lab ou Jupyter Notebook, puis ouvre :

projet eeia-Copy1.ipynb

### 1.2 Exécuter toutes les cellules dans l'ordre

Utilise Kernel → Restart & Run All (ou Ctrl+Enter cellule par cellule).

Les cellules font dans l'ordre :

- Chargement des données CSV
- Nettoyage (valeurs manquantes, doublons, outliers)
- Visualisations (histogrammes, boxplots, pairplot)
- Normalisation MinMaxScaler
- Entraînement et évaluation du modèle

### 1.3 Exécuter la cellule d'export

La dernière cellule (section "Export du modèle Random Forest → interface/model.json") :

- Ré-entraîne le Random Forest sur toutes les données nettoyées
- Affiche l'accuracy de validation (~98.5%)
- Génère automatiquement interface/model.json

Tu dois voir dans la sortie :

Accuracy (validation 80/20) : 0.9853
...
model.json exporté → interface/model.json
Classes : ['high risk', 'low risk']
Arbres : 100
Features: ['Age', 'SystolicBP', 'DiastolicBP', 'BS', 'BodyTemp', 'HeartRate']

## Étape 2 — Lancer l'interface web

Il y a deux façons d'ouvrir l'interface. Choisis l'une ou l'autre.

### Option A — Directement dans le navigateur (le plus simple)

Ouvre simplement ce fichier dans ton navigateur :

interface/index.html

Double-clique dessus depuis l'explorateur de fichiers, ou fais glisser le fichier dans Chrome/Edge/Firefox.

Attention : Certains navigateurs bloquent le chargement de model.json depuis un fichier local.
Si la prédiction affiche une erreur, utilise l'Option B.

### Option B — Via le serveur Flask (recommandé)

Prérequis Python :

pip install flask

Lancer le serveur :

python app.py

Ouvrir dans le navigateur :

http://127.0.0.1:5000

## Étape 3 — Utiliser l'interface

### Onglet Analyse

Remplis les 6 paramètres vitaux de la patiente :

- Âge (années)
- Tension Systolique (mmHg)
- Tension Diastolique (mmHg)
- Glycémie (mmol/L)
- Température (°F)
- Fréquence cardiaque (bpm)

Les champs se colorent automatiquement :

- Vert = valeur normale
- Orange = attention
- Rouge = anomalie

Clique sur Lancer l'analyse → le résultat apparaît immédiatement :

LOW RISK = risque faible
HIGH RISK = risque élevé (avec %)

Clique sur Rapport pour générer un rapport clinique complet, ou Imprimer pour l'imprimer.

### Onglet Historique

Retrouve toutes les analyses effectuées pendant la session

### Onglet Dashboard

Statistiques globales de la session (KPIs, graphiques Low/High Risk, anomalies)

### MediBot

Bouton en bas à droite → chatbot d'assistance clinique (questions sur les paramètres, les risques, etc.)

## Résumé des commandes

| Action | Commande |
| --- | --- |
| Régénérer le modèle | Exécuter toute la cellule d'export dans le notebook |
| Lancer le serveur Flask | python app.py |
| URL de l'interface (Flask) | http://127.0.0.1:5000 |
| URL santé API | http://127.0.0.1:5000/health |
