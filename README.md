# Discovering Voices in the AI Discourse
### CS 4412 — Data Mining | Kennesaw State University | Spring 2026

> **A data mining analysis of 49,428 Reddit comments discussing ChatGPT**, applying K-Means clustering and LDA topic modeling to discover user archetypes and thematic patterns in public AI discourse.

---

## Project Overview

This project investigates how different types of users engage with the topic of ChatGPT across Reddit communities. Rather than predicting outcomes, the goal is **pattern discovery**: who is talking about AI, what are they saying, and how does that differ across communities?

**Dataset:** 49,428 Reddit comments from r/ChatGPT, r/technology, r/Futurology, r/MachineLearning, and r/artificial, collected via the Reddit API (PRAW).

---

## Discovery Questions

| # | Question |
|---|----------|
| RQ1 | What natural user segments exist based on commenting behavior and content? |
| RQ2 | What topics and themes emerge from the ChatGPT comment corpus? |
| RQ3 | What distinct patterns characterize engagement across different subreddit communities? |

---

## Key Findings

### 4 User Archetypes (K-Means, k=4)

| Cluster | Label | Size | Characteristics |
|---------|-------|------|----------------|
| 0 | **Deep Technical Discussers** | 3.4% | Long posts, high scores, AI ethics/policy vocabulary |
| 1 | **Moderate Engagers** | 17.0% | Mid-length, practical use cases, productivity focus |
| 2 | **Niche Interest Group** | 5.9% | Domain-specific: education, creative writing, research |
| 3 | **Mainstream Majority** | 73.6% | Short casual reactions, typical Reddit behavior |

### 8 LDA Topics Discovered

Topics include: AI Ethics & Regulation, Practical Use Cases, Education & Plagiarism, Future of AI, Technical Capabilities, Creative Applications, Product & Company News, and General Reactions.

### Cross-Community Insight

Subreddit culture significantly shapes discourse. r/MachineLearning concentrates Deep Discussers; r/ChatGPT is dominated by Mainstream comments. Comment scores are consistently higher for Cluster 0 regardless of subreddit, confirming that depth earns recognition even when it's rare.

---

## Methods

```
Reddit API (PRAW)
      ↓
Text Preprocessing (NLTK: tokenize, lemmatize, stopword removal)
      ↓
Feature Engineering (TF-IDF 5K features + behavioral features)
      ↓
Dimensionality Reduction (PCA, 50 components)
      ↓
K-Means Clustering (k=4, Elbow + Silhouette selection)
      ↓
LDA Topic Modeling (8 topics, Gensim, coherence c_v = 0.47)
      ↓
Cluster Profiling & Cross-Community Analysis
```

**Key parameters:** k=4, 5,000 TF-IDF features, 50 PCA components, 8 LDA topics, silhouette ≈ 0.31, LDA coherence (c_v) = 0.47.

---

## Repository Structure

```
cs4412-project/
├── README.md                        ← You are here
├── requirements.txt                 ← Python dependencies
│
├── docs/
│   ├── CS4412_M1_Proposal.pdf      ← M1: Project proposal
│   ├── M2_Summary.pdf              ← M2: Exploratory analysis summary
│   └── CS4412_M4_Final_Report.pdf  ← M4: Final report (5-8 pages)
│
├── notebooks/
│   ├── M2_Analysis.ipynb           ← Exploratory data analysis
│   └── M3_M4_Analysis.ipynb        ← Clustering + topic modeling
│
├── src/
│   ├── collect_data.py             ← Reddit API data collection
│   ├── preprocess.py               ← Text cleaning pipeline
│   ├── clustering.py               ← K-Means + evaluation
│   └── topic_modeling.py           ← LDA implementation
│
├── data/
│   └── .gitignore                  ← Dataset not tracked (see below)
│
└── results/
    ├── cluster_profiles.csv        ← Cluster summary statistics
    └── figures/                    ← Visualizations
```

---

## Getting Started

### Prerequisites

- Python 3.9+
- Reddit API credentials (free at reddit.com/prefs/apps)

### Installation

```bash
git clone https://github.com/MahliqO/cs4412-project.git
cd cs4412-project

python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate

pip install -r requirements.txt
```

### Dataset Access

The full dataset (49,428 comments) is not included in this repository due to Reddit API terms of service. To reproduce:

```bash
# Add your Reddit API credentials to a .env file:
# CLIENT_ID=your_id
# CLIENT_SECRET=your_secret
# USER_AGENT=cs4412-project

python src/collect_data.py
```

Alternatively, a 1,000-comment sample for testing is available in `data/sample_comments.csv`.

---

## Requirements

See `requirements.txt`. Key libraries:

```
praw>=7.7.0          # Reddit API
pandas>=2.0.0        # Data manipulation
scikit-learn>=1.3.0  # K-Means, TF-IDF, PCA
gensim>=4.3.0        # LDA topic modeling
nltk>=3.8.0          # Text preprocessing
matplotlib>=3.7.0    # Visualization
seaborn>=0.12.0      # Statistical plots
jupyter>=1.0.0       # Notebooks
```

---

## Critical Assessment

**Validity:** Silhouette score of ~0.31 indicates real but moderate cluster separation. Cluster labels are interpretive and have face validity against known online participation patterns.

**Limitations:** Reddit users are not representative of the general public (sampling bias, English-only). TF-IDF misses semantic meaning; future work should apply SBERT embeddings. Temporal snapshot only.

**Ethics:** Data collected via public Reddit API. All author IDs anonymized. Analysis uses aggregate patterns only — no individual targeting possible or intended.

---

## Future Work

- Apply SBERT sentence embeddings for semantic clustering
- Longitudinal analysis to track how discourse shifts as AI evolves
- Human annotation study to validate cluster labels
- Expand to non-English subreddits
- Apply BERTopic as an alternative to LDA

---

## Course Information

| Field | Value |
|-------|-------|
| Course | CS 4412 — Data Mining |
| Institution | Kennesaw State University |
| Semester | Spring 2026 |
| Student | Mahliq Obie |
| Project | SP5-Blue-Grocery → Reddit ChatGPT Analysis |

---

*This project was completed as part of CS 4412 coursework. All findings are for academic purposes.*
