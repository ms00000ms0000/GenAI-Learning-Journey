# Day 5 - Chunking

## What is Chunking?
Chunking is the process of splitting large documents into smaller meaningful sections for better embedding and retrieval.

## Why Chunking?
Chunking improves retrieval accuracy, reduces context size, and allows relevant information to be found more efficiently.

## Chunk Overlap
Chunk Overlap repeats a small portion of text between chunks to preserve context and prevent information loss.

## Document Loader
A Document Loader extracts text from files such as PDFs, Word documents, websites, and CSV files.

## Retriever
A Retriever searches the vector database and returns the most relevant chunks for a user query.

## FAISS vs Retriever
FAISS stores and searches embeddings, while a Retriever uses FAISS to fetch relevant chunks for the LLM.

## Complete RAG Pipeline
Document → Loader → Chunking → Embeddings → FAISS → Retriever → LLM → Final Answer.

## Key Learning
Chunking and retrieval ensure that only relevant information reaches the LLM, improving accuracy and reducing hallucinations.
