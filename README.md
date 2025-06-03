# Hybrid Legal Search Engine

## Overview

This repository contains a hybrid legal search engine that combines the speed and transparency of BM25 keyword search with the semantic power of a domain-adapted transformer model (LegalBERTSmall). The system is designed for efficient and context-aware retrieval of legal documents, supporting multiple legal datasets and offering a modern GUI interface.

---

## Table of Contents

- [Features](#features)
- [System Architecture](#system-architecture)
- [Sample Queries](#sample-queries)
- [How to Run](#how-to-run)
- [Requirements](#requirements)
- [Evaluation & Observations](#evaluation--observations)
- [Key Strengths & Future Plans](#key-strengths--future-plans)
- [Files](#files)
- [References](#references)

---

## Features

- **Hybrid Retrieval:** Combines BM25 (fast keyword-based) with LegalBERTSmall (semantic re-ranking).
- **Multi-Dataset Support:** Works with CaseHOLD, ECtHR A/B, EUR-Lex, and SCOTUS datasets via Hugging Face.
- **Modern GUI:** Intuitive Tkinter-based interface for dataset selection, query input, and result exploration.
- **Highlighting:** Query terms are highlighted in returned snippets for clarity.
- **Robust Error Handling:** Graceful handling of dataset issues and user feedback.

---

## System Architecture

1. **Query Handling:** User submits a legal query through the GUI (Tkinter app).
2. **Initial Retrieval:** BM25 retrieves the top K candidate documents from the selected dataset.
3. **Semantic Re-Ranking:** (Planned/Extendable) LegalBERTSmall re-ranks these candidates for deeper semantic relevance.
4. **Response:** Top N re-ranked results are displayed, with query highlights and scores.

---

## Sample Queries

Example queries for each dataset (see `Sample-Queries.txt`):

- **CaseHOLD:** Whether the police officer had probable cause to search the vehicle under the Fourth Amendment
- **ECtHR A:** Violation of Article 8 right to privacy due to unlawful surveillance
- **ECtHR B:** Cases involving torture under Article 3 of the European Convention
- **EUR-Lex:** Directive on renewable energy targets for 2030
- **SCOTUS:** First Amendment protections for social media content moderation

---

## How to Run

1. **Install requirements:**
```
pip install -r requirements.txt
```

2. **Run the GUI application:**
```
python legal_search.py
```

3. **Usage:**
- Select a legal domain/dataset from the dropdown.
- Click "Load Dataset" (downloads from Hugging Face if not cached).
- Enter your query and click "Search".
- Results will appear with query terms highlighted.

---

## Requirements

- Python 3.8+
- See `requirements.txt` for all dependencies:
- datasets
- pandas
- rank_bm25
- transformers
- torch
- numpy
- python-dateutil
- requests

---

## Evaluation & Observations

- **Relevance:** Results are more context-aware than BM25 alone when semantic re-ranking is enabled.
- **Legal Semantics:** Captures legal nuance and meaning, especially with transformer-based re-ranking.
- **User Interaction:** Designed for exploratory legal research, not just keyword matching.
- **Performance:** BM25 ensures fast response; transformer re-ranking is more computationally intensive.

_Current implementation outputs only the final ranked results. Automatic evaluation metrics (precision, recall) are planned for future releases._

---

## Key Strengths & Future Plans

- **Hybrid search:** Combines BM25 for speed and LegalBERT for semantic depth.
- **Domain adaptation:** Handles complex legal vocabulary.
- **Usability:** Simple interface with fast, interpretable results.
- **Planned improvements:** Add measurable evaluation, explainability features, and expand to new legal domains and languages.

---

## Files

- `legal_search.py` – Main GUI and search engine logic
- `requirements.txt` – Python dependencies
- `Sample-Queries.txt` – Example queries for each dataset
- `Search-Engine-PPT.pptx` – Project presentation slides
- `IR-VIDEO.mp4` – Video overview of the presentation provided
- `Demo-Video.mp4` - Video of how the search engine runs

---

## References

- [Hugging Face Datasets](https://huggingface.co/datasets)
- [BM25 (rank_bm25)](https://github.com/dorianbrown/rank_bm25)
- [LegalBERT](https://huggingface.co/nlpaueb/legal-bert-small-uncased)
- [Tkinter Documentation](https://docs.python.org/3/library/tkinter.html)

---

*For questions or contributions, please open an issue or pull request.*
