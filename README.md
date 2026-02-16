# Movie Recommender System (MovieLens 100K)

## Project Overview
This project implements and compares multiple recommendation algorithms on the MovieLens-100K dataset.  
The objective is to understand how different recommender system paradigms learn user preferences and how they perform on rating prediction and top-K recommendation tasks.

Three approaches were implemented:
- Item-Item Collaborative Filtering
- Matrix Factorization with User Clustering
- Graph-Based Personalized PageRank

---

## Dataset
The project uses the MovieLens-100K dataset:
- 100,000 ratings
- 943 users
- 1,682 movies

Each user has rated at least 20 movies.  
The dataset includes:
- user ratings
- movie genres and metadata
- user demographic information

---

## Implemented Models

### 1) Item-Item Collaborative Filtering
A neighborhood-based recommendation method.  
Movies are recommended based on similarity to movies a user previously liked using adjusted cosine similarity.

### 2) Matrix Factorization + Clustering
A latent factor model trained using Stochastic Gradient Descent (SGD).

The user-item matrix is decomposed into:
- user preference vectors
- movie feature vectors

Users are then clustered using K-Means to stabilize predictions by blending individual predictions with cluster behavior.

### 3) Graph-Based Personalized PageRank
The dataset is modeled as a bipartite graph between users and movies.

A random walk algorithm (Personalized PageRank) is run from each user node.  
Movies with the highest PageRank scores are recommended, allowing discovery of indirect relationships between users and items.

---

## Evaluation Metrics
Two complementary metrics were used:

**RMSE (Root Mean Squared Error)**  
Measures rating prediction accuracy.

**HitRate@10**  
Checks whether the held-out movie appears in the top-10 recommendations.

---

## Results Summary

| Model | RMSE | HitRate@10 |
|------|------|------|
| Item-Item CF | ~1.06 | ~0.085 |
| Matrix Factorization | ~1.03 | ~0.03 |
| Personalized PageRank | N/A | ~0.117 |

Observations:
- Matrix Factorization gives the best rating prediction
- Personalized PageRank gives the best recommendations
- Different models optimize different objectives

---

## Conclusion
This project shows that no single recommender system is universally best.  
Neighborhood models, latent factor models, and graph-based models each capture different aspects of user preference.  
In practice, hybrid recommender systems combining multiple methods are often most effective.

---

## How to Run

### 1. Install dependencies
### 2. Run the notebook
Simply open and run:
The notebook automatically downloads the MovieLens-100K dataset on first execution.

It will:
- download and prepare the dataset
- train all three recommender models
- evaluate performance using RMSE and HitRate@10
- generate movie recommendations
