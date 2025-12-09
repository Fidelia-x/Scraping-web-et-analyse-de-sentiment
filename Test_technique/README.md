# Scraping web et analyse de sentiment

## Description du projet

Ce projet a pour objectif de :
- Extraire des données en ligne d'une source publique(web scraping)
- Nettoyer du texte (stopwords, normalisation, ponctuation, etc.)
- Appliquer une analyse de sentiment sans modèles LLM
- Produire une visualisation simple basée sur les données collectées

---

## Sources de données

Comme source de données j'ai utilisé Reddit qui fournit des données textuelles très riches. Un post contient souvent le titre,
un texte long, des commentaires, un score, un subreddit (thème), la date et pleins d'autres choses.
C’est donc bien pour l’analyse de sentiment parce qu'il y a beaucoup de texte et des opinions fortes.

---

## Fonctionnalités principales

Scraping web 

Nettoyage automatique du texte

Analyse de sentiment basée sur un lexique (sans intelligence artificielle avancée)

Visualisation simple (matplotlib)

Export des données au format CSV

---

## Installation

Clonez le projet puis installez les dépendances avec :

```bash
pip install -r requirements.txt
```
**Avoir au préalable Anaconda et Jupiter sur son poste pour pourvoir lire le notebook.**

---

## Utilisation

Le code se trouve dans le notebook pour tous les tests.

1. Exécuter le scraping

```python
Exemple

df = scrape_reddit_json("france", 50)
df.to_csv("reddit_data.csv", index=False)
```

3. Nettoyage du texte
```python
Exemple

df["clean_text"] = df["text"].apply(clean_text)
```

5. Analyse de sentiment

```python
Exemple

df["sentiment"] = df["clean_text"].apply(analyze_sentiment)
```

6. Visualisation

```pyhon
Exemple

plot_sentiment_distribution(df)
```
---

## Structure du projet

```bash

Test_technique/
├── README.md
├── Test technique OSINT.ipynb
├── data
│   ├── reddit_data.csv
│   ├── reddit_data_clean.csv
│   └── reddit_sentiment_results.csv
├── output
│   └── sentiment_plot.png
└── requirements.txt

```

## Limites et contraintes

### Limites du scraping Reddit

- risque de blocage temporaire (403 / 429)
- dépendance au User-Agent
- variations fortes d’activité selon les heures

### Limites des données

- textes courts → sentiment parfois ambigu
- opinions parfois ironiques ou sarcastiques
- biais liés au subreddit lui-même (actualité → tendance plutôt négative)

### Limites du modèle

- VADER reste un modèle lexical → pas d’interprétation profonde
- ne comprend pas toujours l’humour, le sarcasme ou le second degré

## Résultat final

-> 50 posts récents ont été extraits

-> Nettoyage effectué

-> Analyse VADER appliquée

-> Visualisation produite sous forme d’un graphique à barres

-> Résultats sauvegardés dans les répertoires data/ et outputs/
