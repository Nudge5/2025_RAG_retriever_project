
# A Quantitative Performance Comparison Study Between Graph-Based Multi-Retriever and Single-Retriever RAG Models  
# グラフベース型マルチリトリーバRAGモデルとシングルリトリーバRAGモデルの定量的性能比較研究

**Jin Bum Joo**  
Department of Data Engineering, The Graduate School  
Pukyong National University  

**朱 晋範**  
釜慶大学校 大学院 データ工学科  

---

# Abstract  
# 要旨

Large Language Models (LLMs) demonstrate strong performance across natural language processing tasks but remain limited in reflecting up-to-date information and domain-specific knowledge. Retrieval-Augmented Generation (RAG) mitigates these issues; however, most systems rely on a single retriever, which can cause context omission or information bias when heterogeneous knowledge sources are required.

大規模言語モデル（LLM）は多くの自然言語処理タスクにおいて高い性能を示すが、最新情報や特定ドメイン知識の反映には依然として限界がある。Retrieval-Augmented Generation（RAG）はこの問題を緩和する手法として利用されているが、多くの既存システムは単一のリトリーバに依存しており、異種の知識源を扱う場合に文脈の欠落や情報バイアスが発生する可能性がある。

To address this limitation, this study implements a graph-based multi-retriever architecture using the LangGraph framework, enabling dynamic selection and combination of retrievers based on query characteristics.

本研究ではこの問題を解決するため、LangGraphフレームワークを用いたグラフベース型マルチリトリーバアーキテクチャを実装し、クエリ特性に応じてリトリーバを動的に選択・統合する仕組みを構築した。

Experiments were conducted on two domains: the Personal Information Protection Act and the Consumer Dispute Resolution Standards.

実験は「個人情報保護法」と「消費者紛争解決基準」の2つのドメインを対象として実施した。

Single-retriever and multi-retriever models were built, and answer quality was evaluated using the Answer Relevance and Faithfulness metrics from RAGAS.

単一リトリーバモデルとマルチリトリーバモデルを構築し、RAGASのAnswer RelevanceおよびFaithfulness指標を用いて回答品質を評価した。

Bootstrap confidence intervals and the Mann–Whitney U test were additionally applied for statistical validation.

さらにBootstrap信頼区間およびMann–Whitney U検定を用いて統計的検証を行った。

Results show that the graph-based multi-retriever significantly improves Answer Relevance across both domains, while Faithfulness remains largely comparable.

実験結果から、グラフベース型マルチリトリーバは両ドメインにおいてAnswer Relevanceを有意に向上させることが確認された。一方でFaithfulnessは両モデル間で大きな差は見られなかった。

These findings suggest that structurally integrating document relationships and multiple retrievers provides stable and meaningful performance improvements beyond conventional single-retriever RAG architectures.

これらの結果は、文書間の構造的関係と複数リトリーバを統合することで、従来の単一リトリーバRAGアーキテクチャを超える安定した性能向上が可能であることを示している。

---

# Repository Overview  
# リポジトリ概要

This repository contains the experimental implementation and datasets used in the comparative study between single-retriever and graph-based multi-retriever RAG architectures.

本リポジトリは、シングルリトリーバRAGとグラフベース型マルチリトリーバRAGの性能比較研究に使用された実験コードおよびデータセットを含む。

Two legal knowledge domains were used in the experiments.

本研究では以下の2つの法知識ドメインを対象とした。

- Personal Information Protection Act  
- Consumer Dispute Resolution Standards  

- 個人情報保護法  
- 消費者紛争解決基準  

The experiments include model implementation, response generation, and RAGAS-based evaluation.

実験ではモデル実装、回答生成、およびRAGASによる性能評価を実施した。

---

# Repository Structure  
# リポジトリ構造

```
2025_RAG_retriever_project

├── Rag_data
│   ├── 개인정보보호법_데이터 자료
│   └── 소비자분쟁해결_데이터 자료
│
├── Rag_main
│   ├── Cus_graph.ipynb
│   ├── Cus_single.ipynb
│   ├── PIPA_graph.ipynb
│   └── PIPA_single.ipynb
│
├── Rag_question
│   ├── Cus_question
│   └── PIPA_question
│
├── Rag_report
│   ├── Cus_report
│   └── PIPA_report
│
└── Rag_result
    ├── Cus_result
    └── PIPA_result
```

---

# Directory Description  
# ディレクトリ説明

## Rag_data

Contains the legal knowledge datasets used for building the RAG knowledge base.

RAG知識ベース構築に使用された法令データセットを含む。

- Personal Information Protection Act data  
- Consumer Dispute Resolution Standards data  

- 個人情報保護法データ  
- 消費者紛争解決基準データ  

---

## Rag_main

Contains the Jupyter Notebook implementations for each retriever architecture and domain.

各ドメインおよびリトリーバ構造ごとの実験コード（Jupyter Notebook）を含む。

- PIPA_single.ipynb — Single-retriever RAG for Personal Information Protection Act  
- PIPA_graph.ipynb — Graph-based multi-retriever RAG for Personal Information Protection Act  

- Cus_single.ipynb — Single-retriever RAG for Consumer Dispute Resolution  
- Cus_graph.ipynb — Graph-based multi-retriever RAG for Consumer Dispute Resolution  

---

## Rag_question

Contains the evaluation question datasets used for testing the RAG systems.

RAGシステム評価に使用された質問データセット。

---

## Rag_result

Contains the generated LLM responses collected in JSON format.

LLMが生成した回答をJSON形式で収集したデータ。

- PIPA_result — Responses for Personal Information Protection Act questions  
- Cus_result — Responses for Consumer Dispute Resolution questions  

---

## Rag_report

Contains the RAGAS evaluation results for the generated answers.

生成回答に対するRAGAS評価結果を含む。

Evaluation metrics include:

評価指標

- Answer Relevance  
- Faithfulness  
