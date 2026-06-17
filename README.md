# RAG Pipeline for Scientific Literature Question Answering

Academic project focused on implementing a Retrieval-Augmented Generation (RAG) system for answering questions about scientific literature using abstracts retrieved from ArXiv.

## Overview

This project implements a complete Retrieval-Augmented Generation (RAG) pipeline capable of:

* Downloading scientific abstracts from ArXiv.
* Performing document chunking and preprocessing.
* Generating semantic embeddings using BGE.
* Indexing embeddings with FAISS.
* Retrieving the most relevant document fragments.
* Applying reranking using a Cross-Encoder model.
* Generating context-aware answers with FLAN-T5-Large.

The system was developed in Google Colab and is designed to support automated exploration of scientific literature.

## Architecture

```text
User Question
      │
      ▼
Question Embedding
      │
      ▼
FAISS Retrieval
      │
      ▼
Cross-Encoder Reranking
      │
      ▼
Context Construction
      │
      ▼
FLAN-T5-Large
      │
      ▼
Generated Answer
```

## Technologies

* Python
* Google Colab
* ArXiv API
* Pandas
* NumPy
* LangChain
* Sentence Transformers
* FAISS
* Hugging Face Transformers
* UMAP

## Models Used

### Embedding Model

* BAAI/bge-base-en-v1.5

### Reranking Model

* Cross-Encoder MiniLM

### Language Model

* Google FLAN-T5-Large

## Dataset

The document corpus is dynamically built by downloading scientific abstracts related to the topic:

```text
open cluster AND Gaia
```

from the ArXiv repository.

## Methodology

1. Retrieve scientific abstracts from ArXiv.
2. Clean and preprocess the collected text.
3. Split documents into overlapping chunks.
4. Generate semantic embeddings for each chunk.
5. Build a FAISS vector index using HNSW search.
6. Retrieve the most relevant chunks for a user query.
7. Apply Cross-Encoder reranking to improve relevance.
8. Build a contextual prompt from the top-ranked chunks.
9. Generate a final answer using FLAN-T5-Large.

## Results

The evaluation shows:

* Strong semantic retrieval performance using FAISS.
* Effective reranking of retrieved chunks.
* Reliable extraction of information contained in the retrieved documents.
* Robust behavior when handling out-of-domain or unrelated queries.

The main limitation lies in the generative stage, where FLAN-T5-Large tends to behave more as an information extraction and summarization model than as a reasoning-oriented large language model.

## Documentation

A detailed description of the implementation, experiments, evaluation methodology, and results can be found in:

* `Pipeline_de_RAG.pdf`

## Repository Structure

```text
├── RAG_pipeline_github_clean.ipynb
├── Pipeline_de_RAG.pdf
└── README.md
```

## Authors

* Esther Menéndez
* Ema Holinaty
* Guillermo García

## License

This repository is intended for academic and educational purposes.
