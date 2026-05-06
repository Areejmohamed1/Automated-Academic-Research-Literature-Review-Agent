# 📚 Automated Literature Review System using LLMs

## 🚀 Overview

This project presents an **end-to-end automated pipeline** for generating academic literature reviews using Large Language Models (LLMs).

The system retrieves research papers from multiple academic sources, processes and ranks them using semantic similarity, and finally generates a **structured literature review** using an AI agent.

---

## Key Features

* 🔍 Automated paper retrieval from **arXiv** and **Semantic Scholar**
* 🧹 Text preprocessing and deduplication
* 🤖 Semantic similarity using transformer embeddings
* 📊 Intelligent paper ranking (similarity + citations + recency)
* ✍️ AI-powered literature review generation using LLM (Groq + LLaMA)
* 📄 Export results as a downloadable Markdown file

---

## Pipeline Architecture

### 1. Data Loading

* Fetch papers using:

  * arXiv API
  * Semantic Scholar API
* Extract:

  * Title
  * Authors
  * Abstract
  * Year
  * Citation count

---

### 2. Preprocessing

* Clean text (lowercase, remove special characters)
* Remove duplicates based on titles
* Combine title + abstract into a unified text representation

---

### 3. Feature Extraction

* Use `SentenceTransformer (all-MiniLM-L6-v2)`
* Convert:

  * Research topic → embedding
  * Papers → embeddings
* Compute semantic similarity using cosine similarity

---

### 4. Modeling & Ranking

Each paper is scored using:

* Semantic similarity (main factor)
* Citation count (importance)
* Publication year (recency)

Top-N most relevant papers are selected.

---

### 5. LLM-Based Writing

* Uses **AutoGen Agent**
* Connected to **Groq API (LLaMA 3.3 70B)**
* Generates a structured academic literature review with:

  * Introduction
  * Methodology
  * Thematic analysis
  * Trends
  * Research gaps
  * Conclusion
  * References (APA format)

---

## Tech Stack

* Python
* Sentence Transformers (HuggingFace)
* AutoGen (Agent-based LLM framework)
* Groq API (LLM inference)
* arXiv API
* Semantic Scholar API
* AsyncIO

---

## Installation

```bash
pip install autogen-agentchat autogen-ext[openai] arxiv requests nest_asyncio sentence-transformers
```

---

## API Setup

### Groq API

1. Get your API key from:
   👉 https://console.groq.com
2. Add it in Colab:

```python
from google.colab import userdata
GROQ_API_KEY = userdata.get('GROQ_API_KEY')
```

---

### Semantic Scholar API (Optional but recommended)

* Add your API key in headers:

```python
headers = {'x-api-key': 'YOUR_API_KEY'}
```

---

## How to Run

1. Set your research topic:

```python
RESEARCH_TOPIC = "Self-Attention Transformer BERT NLP"
```

2. Run the full pipeline:

* Data Loading
* Preprocessing
* Feature Extraction
* Ranking
* LLM Writing

3. Output:

* Generated literature review (~1000+ words)
* Saved as `.md` file
* Downloadable from Colab

---

## Example Output

* ~1400 words literature review
* Based on top 7 ranked papers
* Includes evaluation metrics (similarity scores)

---

## Notes

This project demonstrates:

* Real-world NLP pipeline design
* Integration of APIs + LLMs
* Applied Machine Learning workflow
* Research automation using AI
