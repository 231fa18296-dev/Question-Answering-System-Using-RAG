# Question-Answering-System-Using-RAG

An interactive Retrieval-Augmented Generation (RAG) system that allows users to upload research papers in PDF format and receive context-grounded answers to specific queries along with page-level source citations.

---

## 📌 Overview

Research papers contain large amounts of complex information, making manual searching inefficient. Direct language model queries without document retrieval often lead to hallucinations or inaccuracies.

This application extracts text from uploaded papers, generates vector embeddings, stores them in a **FAISS** vector database, and uses **FLAN-T5** to synthesize accurate, cited responses using top-k semantic retrieval.

---

## ✨ Features

* **PDF Ingestion & Cleaning:** Extracts and processes text from research paper PDFs.


* **Document Chunking:** Splits documents into ~500-word segments with 100-word overlaps to preserve local context.


* **Semantic Vector Search:** Employs Sentence Transformers and FAISS to execute similarity searches for user questions.


* **Context-Grounded Answers:** Feeds top-5 retrieved chunks into FLAN-T5 to minimize hallucinations.


* **Source Citations:** Returns page-level citations for every answered query.



---

## 🛠️ Tech Stack

* **Language:** Python


* **Environment:** Google Colab


* **PDF Extraction:** PyPDF


* **Embeddings:** Sentence Transformers


* **Vector Store:** FAISS (Facebook AI Similarity Search)


* **LLM:** FLAN-T5



---

## ⚙️ Architecture & Workflow

```text
[ Research Paper PDF ]
          │
          ▼
  [ Text Extraction ]
          │
          ▼
  [ Chunking (500 words / 100 overlap) ]
          │
          ▼
  [ Vector Embeddings ]
          │
          ▼
 [ FAISS Vector Database ]
          │
  ┌───────┴────────┐
  ▼                ▼
[ User Question ] ──► [ Semantic Retrieval (Top-5) ]
                           │
                           ▼
                  [ Retrieved Context ]
                           │
                           ▼
                      [ FLAN-T5 ]
                           │
                           ▼
               [ Answer + Page Citations ]

```

---

## 🚀 Getting Started

### Prerequisites

Install the required packages:

```bash
pip install pypdf sentence-transformers faiss-cpu transformers torch

```

### Running the System

1. Open the project notebook in Google Colab.


2. Run the pipeline setup cells to initialize PyPDF, Sentence Transformers, FAISS, and FLAN-T5.


3. Upload your research paper in PDF format.


4. Submit queries against the uploaded document to receive answers with source page references.



---

## 📊 Sample Results

| Question | Generated Answer / Result |
| --- | --- |
| **What is the objective of the paper?** | To improve language models

 |
| **What methodology was used?** | Beam search was used, without checkpoint averaging

 |
| **What datasets were used?** | English-to-German translation development set, newstest2013, Penn Treebank and related datasets

 |
| **What are the limitations?** | Identifies positional encoding and restricted self-attention for long sequences as key limitations

 |

---

## ⚖️ Pros & Cons

### Advantages

* Performs semantic, context-aware vector retrieval.


* Grounds response generation to reduce model hallucinations.


* Provides exact page citations to trace source information.



### Limitations

* Extraction quality depends on PDF text layout (complex tables may degrade).


* Answer depth is limited by the underlying FLAN-T5 base model.



---

## 👤 Author

* **K. Sri Lakshmi** (Reg No: 231FA18296)


* Department of Advanced Computer Science and Engineering


* Vignan's Foundation for Science, Technology & Research
