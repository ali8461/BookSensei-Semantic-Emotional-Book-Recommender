# 📚 **BookSensei — Semantic + Emotion-Aware Book Recommendation System**

BookSensei is an end-to-end AI pipeline that transforms a raw books dataset into an intelligent recommender system powered by:

* 🔍 **Semantic search** (Langchain + OpenAI embeddings + Chroma DB)
* 😊 **Emotion extraction from descriptions**
* 🏷️ **Zero-shot category classification**
* 📊 **Data cleaning and feature engineering**
* 🎛️ **Interactive Gradio dashboard for real-time recommendations**

This project takes 7,000 books and builds a recommendation engine that understands **what a book is about** and **how it feels**, not just keywords.

---

## 🌟 Features

### ✔ Fully automated end-to-end pipeline

From raw CSV → cleaned data → categorized → emotion-scored → embedded → searchable.

### ✔ Zero-shot genre classification

Assigns simplified categories using transformers — no training required.

### ✔ Emotion-aware recommendations

Extracts emotions from descriptions:

* joy
* fear
* anger
* sadness
* surprise
* disgust
* neutral

Users can filter by desired **tone**.

### ✔ Semantic vector search

Query books using natural language:

> “A story about learning forgiveness”

And return the most semantically similar books.

### ✔ Gradio web dashboard

Beautiful, interactive book recommendation UI with:

* category filters
* emotion-tone filters
* high-resolution cover images
* semantic search suggestions

---

# 🏗️ Project Architecture

```
📦 BookSensei
│
├── data-exploration.py         # Load + clean Kaggle dataset
├── text-classification.py      # Zero-shot category simplifier
├── sentiment-analysis.py        # Emotion scoring for each book
├── vector-search.py            # Semantic search engine (Chroma + embeddings)
├── gradio-dashboard.py         # Interactive recommendation UI
│
├── books_cleaned.csv
├── books_with_categories.csv
├── books_with_emotions.csv
├── tagged_description.txt
├── requirements.txt
│
└── README.md
```

---

# 🧠 Pipeline Overview

### **1. `data-exploration.py` — Data Cleaning & Feature Engineering**

* Downloads & loads 7k-book Kaggle dataset
* Removes missing values
* Cleans descriptions
* Tags descriptions with ISBN
* Exports:

  ```
  books_cleaned.csv
  ```

---

### **2. `text-classification.py` — Zero Shot Category Simplification**

* Reduces 500+ noisy categories → 10–12 clean ones
* Fills in missing labels using zero-shot classification
* Exports:

  ```
  books_with_categories.csv
  ```

---

### **3. `sentiment-analysis.py` — Emotion Extraction**

Uses `"j-hartmann/emotion-english-distilroberta-base"` to compute max emotion intensities for each description.

Exports:

```
books_with_emotions.csv
```

Now each book has rich emotional metadata.

---

### **4. `vector-search.py` — Semantic Search Engine**

* Converts descriptions to embedding vectors
* Stores them in a Chroma database
* Supports similarity search queries like:

  > “A book about climate awareness for kids”

---

### **5. `gradio-dashboard.py` — Interactive Recommender UI**

* Loads emotion-scored dataset
* Loads vector search DB
* Lets users filter by:

  * semantic relevance
  * category
  * emotional tone
* Displays 16 best matches with thumbnails + summaries

---

# 🚀 Getting Started

## 1. Clone the repository

```bash
git clone https://github.com/ali8461997/booksensei.git
cd booksensei
```

## 2. Install dependencies

```bash
pip install -r requirements.txt
```


## 3. Add your environment variables

Create a `.env` file:

```
OPENAI_API_KEY=your_key_here
```

## 4. Run the dashboard

After generating the final CSVs:

```bash
python gradio-dashboard.py
```

Gradio will launch at:

```
http://127.0.0.1:7860
```

---


# 🛠️ Tech Stack

| Component               | Technology                  |
| ----------------------- | --------------------------- |
| Data analysis           | pandas, numpy, seaborn      |
| NLP models              | HuggingFace Transformers    |
| Category classification | Zero-shot classification    |
| Emotion scoring         | DistilRoBERTa emotion model |
| Vector search           | Chroma DB                   |
| Embeddings              | OpenAIEmbeddings            |
| Web UI                  | Gradio                      |
| Storage                 | CSV + local Chroma instance |

---

# 📄 License

MIT License (or your preferred license)

