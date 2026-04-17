# Netflix Movie Recommendation Engine

[![Python](https://img.shields.io/badge/Python-3.12-blue.svg)](https://www.python.org/)
[![ML](https://img.shields.io/badge/Machine%20Learning-SVD-orange.svg)](https://en.wikipedia.org/wiki/Singular_value_decomposition)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

An end-to-end recommendation pipeline capable of processing **21.8 million ratings** to deliver personalized movie suggestions in under 1 second. This project demonstrates advanced data engineering, memory optimization, and collaborative filtering.

---

## Project Structure

```text
.
├── data/
│   └── full_movie_metadata.parquet   # Optimized 17,770 movie catalog + Genres
├── models/
│   └── netflix_model_final.pkl       # Serialized SVD Model (Latent Factors)
├── notebooks/
│   └── Netflix_recommendation.ipynb  # Full Training & Inference Pipeline
├── README.md                         # Project Documentation
└── requirements.txt                  # Environment Dependencies

```

Key Features
------------

*   **Matrix Factorization (SVD):** Implements Singular Value Decomposition to identify latent features in user-movie interactions.
    
*   **Massive Scale:** Engineered to handle the "Netflix Prize" dataset (21M+ rows) on consumer-grade hardware (12GB RAM).
    
*   **Hybrid Metadata:** Integrates original Netflix titles with scraped genre data for enriched user results.
    
*   **Vectorized Inference:** Dictionary-based hash-map lookups ensure millisecond response times for a catalog of 17,770+ movies.
    

🧠 Technical Architecture
-------------------------

### 1\. Data Engineering (Memory Optimization)

Handling 21 million rows in standard RAM is challenging. This project utilizes:

*   **Chunk-based Ingestion:** Data is processed in blocks of 1 million rows to prevent OOM (Out of Memory) errors.
    
*   **Schema Downcasting:** Converted int64 to int32 and int8, reducing memory footprint by **75%**.
    
*   **Parquet Storage:** Utilizes columnar storage for the 17k movie catalog to ensure fast I/O.
    

### 2\. The Algorithm

The core engine uses **SVD**, which decomposes the rating matrix **R** into three matrices:

$$`R = U \Sigma V^T`$$


This allows the model to "predict" ratings for movies a user has never seen based on the behavior of similar users.

⚙️ Setup & Installation
-----------------------

### 1\. Clone the Repository

```Bash

git clone https://github.com/pulaksaha143/netflix-recommendation-system.git  
cd netflix-recommendation 

```
### 2\. Environment Setup

It is recommended to use a virtual environment or Google Colab.

```Bash

pip3 install -r requirements.txt   `

```

### 3\. Usage

1.  Open notebooks/Netflix\_recommendation.ipynb.
    
2.  Ensure models/netflix\_model\_final.pkl and data/full\_movie\_metadata.parquet are in their respective folders.
    
3.  Run the "Inference" cells to generate recommendations for any UserID.
    

📊 Results & Performance
------------------------

*   **Dataset Size:** 21,869,525 ratings.
    
*   **Catalog Size:** 17,770 movies.
    
*   **Inference Speed:** ~0.8 seconds to scan the entire catalog for a single user.
    
*   **Accuracy:** Optimized with n\_factors=50 to balance bias and variance.
    
👤 Author
---------

**Pulak Saha**   
_Student at PW Institute of Innovation_ 

_Disclaimer: This project is for educational purposes using the Netflix Prize dataset._
