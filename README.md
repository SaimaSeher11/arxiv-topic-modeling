# arXiv AI Research Trend Analysis (2021–2026)

A data mining and topic modeling project analyzing emerging trends in Artificial Intelligence research using **3,000 arXiv papers from 2021–2026**.

The project applies **BERTopic**, combining transformer-based sentence embeddings, UMAP dimensionality reduction, HDBSCAN clustering, and c-TF-IDF keyword extraction to discover latent research themes and analyze how they evolve over time.

**Course:** CMPE 255 – Data Mining, San José State University

## Project Overview

The rapid growth of AI research makes it increasingly difficult to identify emerging research areas using traditional keyword searches alone. This project uses semantic topic modeling to discover hidden themes within AI/CS research papers and analyze changes in research activity over time.

The analysis focuses on six arXiv categories:

- Artificial Intelligence (cs.AI)
- Computation & Language (cs.CL)
- Machine Learning (cs.LG)
- Computer Vision (cs.CV)
- Neural & Evolutionary Computing (cs.NE)
- Information Retrieval (cs.IR)

## Dataset

The project uses arXiv metadata containing paper titles, abstracts, authors, categories, and publication dates.

A balanced, time-stratified sample was created:

- **3,000 papers**
- **2021–2026**
- **500 papers per year**
- **6 AI-focused CS categories**
- `random_state = 42` for reproducibility

## Data Analysis & Preprocessing

The analysis pipeline included:

- Filtering papers by AI-focused categories and publication year
- Text cleaning and domain-specific stopword removal
- Exploratory analysis of paper categories and abstract lengths
- Analysis of yearly research-volume patterns
- Balanced temporal sampling
- Topic assignment and outlier analysis
- Visualization of topic trends over time

A custom domain-specific stopword list removed generic academic language while preserving meaningful AI terms such as `transformer`, `LLM`, `BERT`, `attention`, and `diffusion`.

## BERTopic Pipeline

The topic modeling pipeline consists of:

**Text Preprocessing → Sentence Embeddings → UMAP → HDBSCAN → c-TF-IDF → Topic Analysis**

### Sentence Embeddings

`all-MiniLM-L6-v2` converts paper abstracts into 384-dimensional semantic embeddings.

### UMAP

Reduces the high-dimensional embedding space while preserving semantic structure.

### HDBSCAN

Performs density-based clustering and identifies papers that do not strongly belong to a topic as outliers.

### c-TF-IDF

Extracts representative keywords from each discovered topic to support topic interpretation.

## Key Results

- **19 research topics discovered**
- **1,902 papers assigned to topics**
- **63.4% topic assignment rate**
- **0.847 topic diversity score**
- **0.503 coherence score**
- Largest discovered topic contained **410 papers**

Major discovered themes included:

- Computer Vision / Image / Video
- Language Models / LLMs / Reasoning
- Privacy / Federated Learning
- Graph Neural Networks
- Reinforcement Learning / Policy

## Research Trend Findings

The temporal analysis showed that:

- **Computer Vision dominated the earlier years** of the sampled period.
- **Language/LLM research grew rapidly and became dominant from 2025 onward** in the sampled data.
- Privacy and federated-learning research formed a distinct topic.
- Research-topic sizes followed a long-tail distribution, with several smaller specialized research areas alongside large dominant topics.

## Outlier Analysis

HDBSCAN classified **1,098 papers as outliers (Topic -1)**.

These papers did not form sufficiently dense semantic clusters and often represented interdisciplinary or less common research themes. Outlier assignment was treated as part of the density-based clustering behavior rather than simply as model failure.

## Technologies

- **Language:** Python
- **Data Analysis:** Pandas, NumPy
- **Machine Learning / NLP:** BERTopic, Sentence Transformers, UMAP, HDBSCAN, scikit-learn
- **Text Processing:** CountVectorizer, c-TF-IDF
- **Visualization:** Matplotlib
- **Environment:** Jupyter Notebook / Google Colab

## Repository Structure

```text
arxiv-topic-modeling/
├── Data_Mining_255_Project.ipynb
├── requirements.txt
└── README.md
```

## Author

**Saima Ashraf**  
San José State University  
