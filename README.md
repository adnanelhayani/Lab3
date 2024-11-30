# Rapport du Lab 3 : Traitement du langage naturel avec PyTorch

## Objectif
Ce laboratoire vise à se familiariser avec PyTorch et à construire des architectures de réseaux neuronaux profonds pour le traitement du langage naturel (NLP) à l'aide de modèles séquentiels.

---

## Partie 1 : Tâche de Classification

### Étapes Réalisées
1. **Collecte des données** :
   - Utilisation des bibliothèques de scraping (`BeautifulSoup`) pour collecter des textes en arabe à partir de sites web sur le thème de l'intelligence artificielle.
   - Attribution d'un score (entre 0 et 10) à chaque texte pour représenter sa pertinence.

2. **Prétraitement des données** :
   - Pipeline NLP comprenant :
     - Tokenisation, lemmatisation et stemming.
     - Suppression des stopwords et ponctuations.
     - Normalisation des textes pour améliorer la qualité des données.

3. **Entraînement des modèles** :
   - Implémentation et entraînement de plusieurs architectures : 
     - RNN, RNN bidirectionnel, GRU, LSTM.
   - Ajustement des hyperparamètres pour obtenir de meilleures performances.

4. **Évaluation des modèles** :
   - Utilisation de métriques standards (MSE, MAE) et de métriques spécifiques comme le score BLEU pour évaluer les performances des modèles.

### Résultats
Les performances des modèles sont résumées dans le tableau ci-dessous :

| Modèle              | MAE       | MSE       |
|---------------------|-----------|-----------|
| RNN                | 0.032953  | 0.001485  |
| RNN Bidirectionnel | 0.037008  | 0.001848  |
| GRU                | 0.051932  | 0.005300  |
| LSTM               | 0.028761  | 0.002299  |

- **Observations** :
  - LSTM a obtenu la meilleure performance globale en termes de MAE et de MSE, surpassant les autres modèles.
  - Les modèles GRU et RNN bidirectionnel ont montré des performances légèrement inférieures, mais restent compétitifs.

---

## Partie 2 : Modèle Transformer (Génération de texte)

### Étapes Réalisées
1. **Fine-tuning d'un modèle pré-entraîné GPT-2** :
   - Utilisation de `pytorch-transformers` pour charger le modèle GPT-2.
   - Fine-tuning du modèle sur un dataset personnalisé collecté via scraping.

2. **Génération de texte** :
   - Création d'une fonction pour générer des textes en arabe à partir d'une phrase donnée.
   - Utilisation de stratégies avancées comme `top-p` et `temperature` pour diversifier la génération.

### Exemple de Résultat
À partir de la phrase donnée **"الذكاء الاصطناعي هو فرع من"**, le modèle génère un paragraphe cohérent expliquant le sujet.

---

## Synthèse des apprentissages
- **Scraping et prétraitement** : Maîtrise des techniques de collecte de données en ligne et de préparation de données textuelles.
- **Architecture séquentielle** : Compréhension des concepts derrière RNN, GRU et LSTM et leur application à des tâches de classification.
- **Transformer et génération de texte** : Exploration du fine-tuning de modèles pré-entraînés et des capacités de génération des Transformers.
- **Évaluation des performances** : Utilisation de métriques pour analyser et comparer les modèles de manière rigoureuse.

---

## Dépôt GitHub
Le code complet et les fichiers générés sont disponibles dans ce dépôt. Les fichiers incluent :
- Scripts de scraping et prétraitement.
- Modèles d'entraînement et évaluation.
- Fine-tuning de GPT-2 et génération de texte.
