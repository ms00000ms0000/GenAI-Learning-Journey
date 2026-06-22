# Day 6 - Complete RAG Architecture

## What is RAG?

RAG (Retrieval-Augmented Generation) is a technique that combines information retrieval and LLM generation. Instead of answering only from model memory, the LLM first retrieves relevant information from external documents and then generates an answer.

---

## Why RAG is Needed?

Problems with normal LLMs:

- Hallucination
- Outdated knowledge
- Cannot access private documents
- Limited domain-specific knowledge

RAG solves these problems by providing relevant context before answer generation.

---

# RAG = Retrieval + Augmentation + Generation

## Retrieval

Find relevant chunks from the knowledge base.

Example:

User Query:
What is CNN?

Retriever finds:
CNN related chunks from documents.

---

## Augmentation

Retrieved chunks are added to the prompt.

Example:

Context:
CNN is a deep learning architecture used for image processing.

Question:
What is CNN?

---

## Generation

The LLM uses the retrieved context to generate the final answer.

---

# Phase 1: Indexing Phase

One-time process.

Flow:

PDF
↓
Loader
↓
Chunking
↓
Embeddings
↓
FAISS

Output:
Vector Database Ready

---

## Step 1: Document Loader

Extracts text from PDF files.

Example:
PyPDFLoader

---

## Step 2: Chunking

Large documents are split into smaller chunks.

Benefits:

- Better retrieval
- Reduced token usage
- Improved accuracy

---

## Step 3: Embeddings

Convert chunks into vectors.

Example:

"Machine Learning"
↓
[0.23, 0.54, 0.81, ...]

---

## Step 4: FAISS

Stores embeddings and enables fast similarity search.

---

# Phase 2: Retrieval and Generation

Runs for every user query.

Flow:

User Query
↓
Query Embedding
↓
FAISS Search
↓
Top-K Chunks
↓
LLM
↓
Answer

---

## Query Embedding

User question is converted into vector form.

Example:

"What is CNN?"
↓
Embedding Vector

---

## Retrieval

FAISS finds nearest chunks using vector similarity.

Example:

Top 3 Relevant Chunks

Chunk 15
Chunk 28
Chunk 42

---

## Generation

Retrieved chunks are sent to Gemini/GPT.

Prompt:

Context:
<Retrieved Chunks>

Question:
<User Query>

The LLM generates an answer using the provided context.

---

# Retriever vs LLM

Retriever:
Finds relevant information.

LLM:
Explains and generates answers from retrieved information.

---

# Complete RAG Pipeline

Document
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
LLM
↓
Answer

---

# Key Takeaways

- RAG reduces hallucination.
- RAG allows private document question answering.
- FAISS stores and searches embeddings.
- Retriever finds relevant chunks.
- LLM generates answers using retrieved context.
- RAG combines retrieval and generation into a single workflow.
