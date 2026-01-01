# AI-Powered Assistant for Intelligent Legal Review

**Copyright (c) 2026 Shrikara Kaudambady. All rights reserved.**

## 1. Introduction

The legal profession involves analyzing vast amounts of unstructured text, from complex contracts to lengthy case law documents. This manual review process is time-consuming, labor-intensive, and carries the risk of human error. AI-powered tools can act as a powerful assistant for legal professionals, automating high-volume analysis and allowing attorneys to focus their expertise on high-level strategy and judgment.

This project provides a Jupyter Notebook that simulates a two-part **Intelligent Legal Review AI**. It demonstrates how Natural Language Processing (NLP) can be used to:
1.  **Analyze a contract** and automatically flag potentially risky clauses.
2.  **Summarize a dense legal document** to quickly provide its most salient points.

## 2. The Solution Explained: A Two-Tool AI Assistant

The notebook implements two distinct NLP tools, each designed for a specific legal task.

### 2.1. Tool 1: Contract Risk Analyzer
This tool helps an attorney quickly identify potential areas of concern in a legal agreement.
*   **Methodology:** The system uses a **knowledge-driven, pattern-matching approach**. We create a simple "knowledge base" that maps common risk categories (like `UNLIMITED_LIABILITY`) to a list of specific keywords and phrases that are often associated with that risk.
*   **Workflow:**
    1. The AI scans the contract document sentence by sentence.
    2. It checks each sentence against the list of risky phrases in its knowledge base.
    3. If a match is found, it flags the clause and identifies the corresponding risk category.
    4. The output is a list of all flagged clauses, allowing the attorney to immediately focus their attention on the most critical parts of the document.
*   **Technology:** This is implemented with simple string and regular expression matching, demonstrating how a targeted, rule-based system can be highly effective for specific compliance tasks.

### 2.2. Tool 2: Case Law Summarizer
This tool helps an attorney quickly grasp the essence of a long judicial opinion or legal brief.
*   **Methodology:** The system uses a classic **extractive summarization** algorithm. Instead of generating new text, it identifies and extracts the most important sentences from the original document.
*   **Workflow:**
    1. The document is first broken down into individual sentences using `spaCy`.
    2. A **TF-IDF (Term Frequency-Inverse Document Frequency)** vectorizer is used to calculate a score for every word, measuring its importance relative to the document.
    3. Each sentence is then given an "importance score" by summing the TF-IDF scores of the words it contains.
    4. The AI selects the top N (e.g., 3 or 4) highest-scoring sentences.
    5. These sentences are presented, in their original order, as the final summary.
*   **Technology:** This is implemented using `scikit-learn` for TF-IDF calculation and `spaCy` for robust sentence tokenization.

## 3. How to Use the Notebook

### 3.1. Prerequisites

This project uses `spaCy` and `scikit-learn`.

1.  **Install Libraries:**
    ```bash
    pip install pandas numpy scikit-learn spacy
    ```
2.  **Download NLP Model:**
    After installing spaCy, you need its pre-trained English model for sentence parsing.
    ```bash
    python -m spacy download en_core_web_sm
    ```

### 3.2. Running the Notebook

1.  Clone this repository:
    ```bash
    git clone https://github.com/shrikarak/intelligent-legal-review-ai.git
    cd intelligent-legal-review-ai
    ```
2.  Start the Jupyter server:
    ```bash
    jupyter notebook
    ```
3.  Open `legal_review_pipeline.ipynb` and run all cells. The notebook will first demonstrate the contract review tool and then the case law summarizer.

## 4. Real-World Application and Vision

This simulation is a template for a powerful legal tech tool. In a real-world scenario, its capabilities would be enhanced and integrated into an attorney's daily workflow.

1.  **Advanced Contract Analysis:**
    *   The simple keyword matching would be replaced by a **fine-tuned NLP classification model** trained on thousands of annotated legal contracts. Such a model could identify risk categories with much greater nuance and accuracy, even if the exact keywords are not present.

2.  **Abstractive Summarization:**
    *   The extractive summarization model would be upgraded to an **abstractive summarizer** using a large language model (LLM) like BART, T5, or a GPT-series model. An abstractive model can generate novel sentences, creating a more fluid and human-like summary that captures the essence of the document, rather than just re-stating its most important sentences.

3.  **Workflow Integration:**
    *   The entire system would be deployed as a **plugin for a word processor** (like Microsoft Word or Google Docs) or a legal practice management software.
    *   As an attorney drafts or reviews a contract, the AI would provide real-time highlighting of risky clauses. When reading a new case file, they could get an AI-generated summary with the click of a button, dramatically accelerating their research and review process.
