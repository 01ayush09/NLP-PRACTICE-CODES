# MiniRAG — Lightweight Retrieval-Augmented Generation 

**MiniRAG** is a compact, modular, and production-oriented **Retrieval-Augmented Generation (RAG)** system engineered for efficiency, clarity, and extensibility. It enables knowledge-grounded generation over custom corpora using a minimal yet powerful pipeline — ideal for ML engineers, researchers, and applied AI developers.

 *Built to demonstrate strong ML engineering practices with clean abstractions and practical RAG design.*

---

## Highlights

-  **Lightweight RAG pipeline** with minimal dependencies  
-  **Custom document ingestion** (text / PDFs / structured data)  
-  **Semantic chunking & dense embeddings**  
-  **Fast vector-based retrieval** (top-k similarity search)  
-  **Context-augmented generation** using LLMs  
-  **Modular, configurable & extensible architecture**

---

## Why Retrieval-Augmented Generation (RAG)?

Large Language Models alone lack access to:
- Private or domain-specific data  
- Up-to-date information  
- Source grounding  

RAG solves this by **retrieving relevant knowledge before generation**, significantly reducing hallucinations and improving factual accuracy.

MiniRAG implements this paradigm in a **lean, understandable, and hackable form**.



---

## System Architecture

<img width="1536" height="1024" alt="ChatGPT Image Dec 24, 2025, 12_19_02 PM" src="https://github.com/user-attachments/assets/8e762ff0-1f78-4040-9d24-c3a6cb79d58c" />


---

## 🔄 End-to-End Workflow

### 1️⃣ Document Ingestion & Chunking 
- Load documents from `data/`
- Clean & normalize text
- Split into semantic chunks to preserve contextual meaning

---

### 2️⃣ Embedding & Indexing 
- Convert text chunks into dense vector embeddings
- Store vectors in a similarity-search-friendly index (e.g., FAISS)

```python
embedding = embed_text(chunk)
index.add(embedding)
```
### 3️⃣ Retrieval 
- Encode the user query into an embedding  
- Perform nearest-neighbor similarity search in the vector store  
- Select the top-k most relevant document chunks  

```python
docs = retriever.search(query, top_k=5)
```
---

### 4️⃣ Augmented Generation 
- Combine retrieved context with the user query  
- Generate grounded, context-aware responses using a Large Language Model (LLM)  

```python
prompt = build_prompt(query, docs)
answer = generator.generate(prompt)
```

## Evaluation Considerations

-  **Retrieval Metrics**
  - Precision@K
  - Recall@K

-  **Generation Quality**
  - BLEU
  - ROUGE
  - Human evaluation

-  **Performance Profiling**
  - Latency
  - Memory usage
  - Throughput

---

## Design Philosophy

- 🔹 Minimal abstractions  
- 🔹 Clear separation of concerns  
- 🔹 Pluggable and extensible components  
- 🔹 ML-engineer-friendly readability  

**MiniRAG** is intentionally **simple yet powerful**, serving as a strong foundation for advanced RAG systems such as **hybrid search, re-ranking, and evaluation-aware pipelines**.




