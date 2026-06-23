# Day 7 - LangChain & Production RAG

## 🎯 Objective

Understand how LangChain simplifies RAG application development by connecting multiple components into a pipeline.

---

## 📚 Topics Covered

### 🔹 LangChain
Framework used to build LLM applications using reusable components.

### 🔹 PromptTemplate
Reusable prompt structure with placeholders such as `{context}` and `{question}`.

### 🔹 Retriever
Fetches the most relevant chunks from the vector database.

### 🔹 Chain
A workflow where the output of one component becomes the input to the next component.

### 🔹 LCEL (LangChain Expression Language)
Modern syntax used to create pipelines in LangChain.

```python
chain = retriever | prompt | llm
```

### 🔹 Output Parser
Converts raw LLM output into a structured format.

---
## 🔹 Manual RAG vs LangChain RAG

```text
Load PDF
↓
Chunk
↓
Embedding
↓
Search
↓
Prompt
↓
LLM
↓
Answer

```
---

``` text
Components
↓
Chain
↓
Answer
```

---

## 🏗️ Production RAG Architecture

```text
PDF
 ↓
Loader
 ↓
Chunking
 ↓
Embeddings
 ↓
FAISS
 ↓
Retriever
 ↓
PromptTemplate
 ↓
LLM
 ↓
Answer
```

---

## 📝 Key Definitions

| Term | Definition |
|--------|------------|
| **LangChain** | Framework for building LLM-powered applications. |
| **PromptTemplate** | Reusable prompt with dynamic placeholders. |
| **Retriever** | Retrieves relevant chunks for a query. |
| **Chain** | Connects multiple components into a workflow. |
| **LCEL** | Modern pipeline syntax in LangChain. |
| **Output Parser** | Formats LLM responses into structured output. |

---

---
 n
```
