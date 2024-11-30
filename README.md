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

## Partie 2 : Modèle Transformer (Fine-tuning et Génération de Texte)

### Étapes Réalisées

#### 1. **Chargement du modèle AraGPT2**
- Utilisation du modèle pré-entraîné `aubmindlab/aragpt2-medium`, spécialement optimisé pour l'arabe.
- Configuration du tokenizer avec ajout d'un token de padding pour gérer les séquences de différentes longueurs.

#### 2. **Collecte et Prétraitement des Données**
- Scraping de textes en arabe à partir de pages Wikipédia (par exemple, sur "intelligence artificielle" et "apprentissage automatique").
- Étapes de prétraitement :
  - Suppression des voyelles courtes (tashkeel).
  - Normalisation des hamzas.
  - Suppression des caractères de ponctuation.
  - Filtrage des paragraphes trop courts ou non pertinents.
- Les paragraphes prétraités sont sauvegardés dans un fichier texte.

#### 3. **Entraînement du Modèle**
- Conversion des données textuelles en un format adapté au modèle à l'aide d'un `DataLoader`.
- Utilisation des hyperparamètres suivants :
  - Époques : 3
  - Taux d'apprentissage : 5e-5
  - Optimiseur : AdamW
- Entraînement sur GPU (si disponible) avec rétropropagation.
- Le modèle fine-tuné est sauvegardé pour une utilisation ultérieure.

#### 4. **Génération de Texte**
- Chargement du modèle fine-tuné et génération de texte à partir d'une phrase de départ (`prompt`).
- Personnalisation des paramètres de génération (longueur maximale, température, top-p, etc.).
- Exemple de prompt : *"الذكاء الاصطناعي هو فرع من"*, produisant un texte cohérent en arabe.

---

## Synthèse des apprentissages
- **Scraping et prétraitement** : Maîtrise des techniques de collecte de données en ligne et de préparation de données textuelles.
- **Architecture séquentielle** : Compréhension des concepts derrière RNN, GRU et LSTM et leur application à des tâches de classification.
- **Transformer et génération de texte** : Exploration du fine-tuning de modèles pré-entraînés et des capacités de génération des Transformers.
- **Évaluation des performances** : Utilisation de métriques pour analyser et comparer les modèles de manière rigoureuse.

