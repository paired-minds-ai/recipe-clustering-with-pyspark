# Recipe Clustering with Apache Spark: One-Hot Encoding vs. Word2Vec

A data processing and unsupervised learning project exploring ingredient-based recipe clustering using Apache Spark and two different feature representation techniques: One-Hot Encoding and Word2Vec.

## Project Overview

The goal of this project is to group recipes based on their ingredients and investigate how different ingredient representations affect the resulting clusters.

Using the **What's Cooking?** dataset, two approaches are implemented and compared:

### 1. One-Hot Encoding + K-Means

Each recipe is represented as a binary vector indicating the presence or absence of each ingredient. Rare ingredients are filtered out, and K-Means is applied to group recipes with similar ingredient combinations.

- Binary ingredient representation
- Rare ingredient filtering
- Vector assembly using Spark MLlib
- K-Means clustering with 35 clusters
- Identification of the 10 most frequent ingredients in each cluster

### 2. Word2Vec + K-Means

In this approach, ingredient words are represented using dense vector embeddings learned through Word2Vec. Each recipe is represented by an aggregated ingredient embedding, which is then used for clustering.

- Word2Vec ingredient embeddings
- 100-dimensional feature vectors
- K-Means clustering with 24 clusters
- Identification of the 10 most frequent ingredients in each cluster

## Methodology

Both approaches share a common preprocessing pipeline:

1. Convert ingredient names to lowercase.
2. Remove non-alphabetical characters.
3. Convert plural words to singular forms.
4. Remove selected stopwords and descriptive terms.
5. Split multi-word ingredients into individual words.

The Elbow Method is used to investigate suitable cluster counts for both approaches.

## Key Techniques

- Distributed data processing with Apache Spark
- Text preprocessing and normalization
- One-Hot Encoding
- Word2Vec embeddings
- Feature engineering
- K-Means clustering
- Elbow Method
- Cluster analysis and ingredient frequency ranking

## Technologies

- Python
- Apache Spark / PySpark
- Spark MLlib
- Word2Vec
- NumPy
- Matplotlib
- Inflect

## Dataset

The project uses the **What's Cooking?** dataset, which contains recipes represented by their ingredient lists, along with recipe IDs and cuisine labels.

Dataset: [What's Cooking? on Kaggle](https://www.kaggle.com/competitions/whats-cooking)

## Repository Structure

```text
recipe-clustering-spark-word2vec/
├── README.md
└── recipe_clustering.ipynb
```

## Learning Outcomes and Limitations

This project provided practical experience with distributed data processing, text-based feature engineering, and unsupervised learning using Apache Spark.

Some important lessons and limitations identified during the experiments include:

- **Feature representation matters:** One-Hot Encoding captures ingredient presence, while Word2Vec provides dense representations based on relationships learned between ingredient words.
- **Preprocessing affects clustering:** Removing descriptive words and infrequent ingredients simplifies the feature space, but may also remove information that could help distinguish recipes.
- **Choosing the number of clusters is not straightforward:** The Elbow Method provides a useful heuristic, but the selected cluster counts are not necessarily optimal.
- **Evaluation is important:** The experiments focus on unsupervised clustering and descriptive cluster analysis. No independent holdout evaluation or quantitative comparison against known cuisine labels is included.

The original notebooks are preserved as coursework experiments. Their results should be interpreted within the scope of the implemented methodology.

## Acknowledging the Work

This project was developed as part of a graduate-level course in data processing and unsupervised learning, taken during undergraduate studies.
