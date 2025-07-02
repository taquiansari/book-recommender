# 📚 Book Recommender

An intelligent AI-based book recommendation system that understands your query semantically and emotionally. It goes beyond keyword matching — factoring in categories, emotions, and context — to suggest books you’ll actually connect with.

---

## 🧠 Overview

This project leverages modern NLP techniques to recommend books based on their **description**, **emotional tone**, and **genre**. A clean **Gradio dashboard** allows users to enter a query, optionally filter by emotion and category, and receive personalized book suggestions.

---
![image](https://github.com/user-attachments/assets/42800a3d-9876-4953-90f1-a23db94f2e10)
![image](https://github.com/user-attachments/assets/a0d887e6-bb71-4e8f-b242-466c6c2977c9)

---

## 📊 Dataset

- **Source**: https://www.kaggle.com/datasets/dylanjcastillo/7k-books-with-metadata
- **Features**: Book **descriptions**, **ISBN13**, **categories**, and more.
- **Data Cleaning**:
  - Removed meaningless or generic descriptions.
  - Cleaned and standardized category labels.
  - Ensured that each entry was meaningful for semantic analysis and recommendation.

---

## 🔧 Key Components

### 🔹 Semantic Search with Embeddings

- **Chunking**: Used `LangChain`'s `CharacterTextSplitter` to divide book descriptions into meaningful chunks.
- **Embeddings**: Generated using **OpenAI Embeddings** (`text-embedding-ada-002`).
- **Vector Store**: Stored and queried using **ChromaDB**.
- **Search**: Compared user queries to description embeddings to retrieve relevant matches.

### 🔹 Zero-Shot Category Classification

- **Model**: `facebook/bart-large-mnli` (via Hugging Face Transformers)
- **Method**: Given only book descriptions, the model assigns the most likely category out of a predefined list without prior training on those specific categories.

### 🔹 Emotion Detection via Sentiment Analysis

- **Model**: `j-hartmann/emotion-english-distilroberta-base`
- **Emotions Supported**:
  - joy
  - sadness
  - anger
  - fear
  - disgust
  - surprise
  - neutral
- **Usage**: Helps filter or rank books based on emotional tone in their descriptions.

---

## 🖥️ Gradio Dashboard

A sleek interface built with **Gradio** for real-time recommendations:

### 🔸 Inputs:
- **User Query**: A short sentence or phrase describing what you're in the mood for.
- **Category Filter** *(optional)*: Genre selection (e.g., romance, thriller).
- **Emotion Filter** *(optional)*: Desired emotional tone (e.g., joy, sadness).

### 🔸 Output:
- A list of books whose descriptions semantically match your query, filtered by category and/or emotional tone.

---

## 🚀 How It Works

1. The user provides a natural language query (e.g., *"a suspenseful journey of self-discovery"*).
2. The query is embedded and compared against book description embeddings stored in ChromaDB.
3. Optional filters for category and emotion are applied.
4. The most relevant matches are displayed on the Gradio UI.

---

## 📦 Tech Stack

- **Python**
- **LangChain**
- **OpenAI Embeddings**
- **ChromaDB**
- **Hugging Face Transformers**
  - `facebook/bart-large-mnli`
  - `emotion-english-distilroberta-base`
- **Gradio**
- **Pandas / NumPy**

