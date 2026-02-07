# CS 4412 Data Mining Project
## Discovering User Behavior Patterns and Discussion Topics in Reddit ChatGPT Communities

### Project Overview
This project investigates user behavior patterns and thematic structures within Reddit discussions about ChatGPT using unsupervised learning techniques. We apply clustering algorithms and text mining methods to discover natural user segments, identify emergent discussion topics, and characterize community-specific engagement patterns.

### Dataset
**Name:** Reddit ChatGPT Comments Dataset  
**Source:** [GitHub Repository](https://github.com/Armita84/ChatGPT-Dataset-Reddit)  
**Size:** ~50,000 comments from 4 subreddits  
**Format:** CSV file with comment_id, comment_parent_id, comment_body, and subreddit fields

**Dataset Description:**  
This dataset contains user-generated comments discussing ChatGPT across multiple Reddit communities, captured during the initial public release and adoption period of ChatGPT. The data represents authentic, unfiltered user discourse from diverse communities with varying technical backgrounds, interests, and perspectives on AI technology.

### Research Questions (Discovery-Focused)
1. **User Segment Discovery:** What are the natural user segments based on commenting behavior and content characteristics in ChatGPT discussions?

2. **Topic and Theme Emergence:** What topics and thematic discussions emerge from the ChatGPT comment corpus, and how do these topics distribute across different communities?

3. **Community-Specific Patterns:** What distinct patterns characterize user engagement and discussion styles across different subreddit communities?

### Planned Techniques
#### Clustering Methods
- **K-Means Clustering:** Partition users/comments into distinct segments
- **Hierarchical Clustering:** Build dendrograms revealing hierarchical relationships
- **DBSCAN:** Identify dense regions and detect outliers/anomalies

#### Text Mining Methods
- **TF-IDF Vectorization:** Transform text into numerical feature vectors
- **Latent Dirichlet Allocation (LDA):** Probabilistic topic modeling to discover latent themes

#### Supporting Techniques
- **Principal Component Analysis (PCA):** Dimensionality reduction for visualization

### Project Timeline
- **M2 (Weeks 3-6):** Data preprocessing and exploratory analysis
- **M3 (Weeks 7-10):** Clustering implementation and topic modeling
- **M4 (Weeks 11-15):** Analysis, interpretation, and final report

### Team Information
**Student:** Mahliq Obie 
**Course:** CS 4412 - Data Mining  
**Institution:** Kennesaw State University  
**Semester:** [Current Semester]

### Repository Structure
```
cs4412-project/
├── README.md
├── docs/
│   └── CS4412_M1_Proposal.pdf
├── data/
│   └── .gitignore
├── notebooks/
│   └── (Jupyter notebooks for analysis)
├── src/
│   └── (Python scripts)
└── results/
    └── (Output visualizations and reports)
```

### Technologies and Libraries
- **Python 3.x**
- **scikit-learn:** Clustering, TF-IDF, PCA
- **gensim:** Topic modeling (LDA)
- **pandas:** Data manipulation
- **matplotlib/seaborn:** Visualization
- **nltk/spacy:** Text preprocessing

### Getting Started
```bash
# Clone the repository
git clone https://github.com/MahliqO/cs4412-project.git
cd cs4412-project

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Download dataset
# Follow instructions in data/README.md
```

### Documentation
Full project proposal and detailed methodology can be found in `/docs/CS4412_M1_Proposal.pdf`

### License
This project is for academic purposes as part of CS 4412 coursework.


### Acknowledgments
- Dataset provided by: [Armita84/ChatGPT-Dataset-Reddit](https://github.com/Armita84/ChatGPT-Dataset-Reddit)
- LaTeX document preparation assisted by Claude (Anthropic AI)
- Course instructor and teaching assistants
- CS 4412 Data Mining course materials
---
*Last Updated: February 2026*
