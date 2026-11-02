# Reliable RAG Knowledge Assistant

Author: Aditya Siddaarth

AlmaBetter RAG Systems Engineering lab using the original Northstar classroom dataset.

[Open in Colab](https://colab.research.google.com/drive/1uaNun-sGTgSQ6WJ5G-08d2dJTnhZTom5) · [Executed notebook](Northstar_Reliable_RAG_Knowledge_Assistant.ipynb)

## Run

1. Open the notebook in Colab and connect a Python runtime.
2. Run the installation and configuration cells.
3. Run the dataset cell. It downloads the exact [instructor ZIP](https://drive.google.com/file/d/1cyOvaspGyuzbwnk9WKAguOZfzE2PWJED/view); manual upload is the fallback. Do not replace the data, manifest, or reference labels.
4. Run the 13 implemented functions, supplied integration harness, and stage comparison in order.
5. Read the final findings/reflection cell.

The core lab requires no API key. The optional DeepSeek cell was not executed.

## Pipeline

PDF/HTML/TXT parsing with labelled table rows → normalization → recursive chunks and deterministic IDs → trusted role/status filtering → scoped BM25 and normalized FAISS → RRF → cross-encoder reranking → whole cited snippets within 1,700 characters → grounded prompt and source-level evaluation.

Filters run before both retrieval methods. Unknown roles fail closed; employees cannot retrieve security-admin sources; superseded policies are excluded for every role. Only included snippets contribute source citations and evaluation IDs.

## Verified run — 2 November 2026

- Original dataset: seven documents, nine labeled questions, 30 chunks.
- All supplied structural, deterministic-ID, HTML-table, version, and role-scope assertions passed.
- All seven cases with nonempty expected-source sets: Hit@4 = 1.0 and source recall@4 = 1.0.
- Q2 included both IT and Finance evidence; its context was 1,687 characters.
- Q7 (restricted employee request) and Q9 (unsupported pet-insurance benefit) require manual evidence/security review and are excluded from ordinary coverage scoring.

Source coverage does not establish precision, truth, or generated-answer faithfulness. The notebook records limitations and actual stage comparisons. No generated answer was evaluated because the optional LLM call was skipped.

## Submission status

The executed notebook and reflections are saved here. The assignment also requires the original Northstar_RAG_Engineering_Dataset.zip in this repository; that file upload is pending before final AlmaBetter submission.

Do not commit API keys, model caches, generated index folders, or real employee records.
