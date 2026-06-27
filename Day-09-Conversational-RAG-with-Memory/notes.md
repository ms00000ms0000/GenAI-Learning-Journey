# 📅 Day 09 – Conversational RAG with Memory

## 🎯 Objective

In Day 9, we upgraded our basic RAG pipeline into a **Conversational RAG** by adding **chat memory**. Now the chatbot can remember previous conversations and answer follow-up questions naturally.

---

# 📖 What We Learned

A normal RAG chatbot treats every question as a new query. It cannot remember previous interactions.

Example:

```text
User: What is CNN?

Bot: CNN is a Convolutional Neural Network.

User: Where is it used?

Bot: What is "it"?
```

To solve this problem, we introduced **Memory**.

---

# 🧠 What is Conversational RAG?

Conversational RAG is a Retrieval-Augmented Generation system that maintains conversation history so the LLM can understand follow-up questions.

Flow:

```text
User Question
        │
        ▼
Retriever
        │
        ▼
Relevant Chunks
        │
        ▼
Prompt
        │
        ▼
Chat Memory
        │
        ▼
LLM
        │
        ▼
Answer
```

---

# 🛠 New Concepts Learned

## InMemoryChatMessageHistory

Stores previous conversation inside RAM.

Example:

```python
chat_history = InMemoryChatMessageHistory()
```

---

## RunnableWithMessageHistory

Wraps the RAG chain with chat memory.

```python
RunnableWithMessageHistory(...)
```

---

## Session ID

Maintains separate memory for every user.

Example:

```text
User A → Session A

User B → Session B
```

Each user gets an independent conversation history.

---

# 📌 Updated RAG Flow

```text
PDF
│
▼
Loader
│
▼
Chunking
│
▼
Embeddings
│
▼
FAISS
│
▼
Retriever
│
▼
Prompt
│
▼
Memory
│
▼
Gemini
│
▼
Answer
```

---

# ✅ Advantages

* Supports follow-up questions.
* Maintains conversation context.
* Better user experience.
* Foundation for AI Assistants.
* Used in ChatGPT-like applications.

---

# 🔑 Keywords

* Conversational RAG
* Chat Memory
* InMemoryChatMessageHistory
* RunnableWithMessageHistory
* Session ID
* Conversation Context

---

# 📌 Summary

Day 9 transformed our basic RAG chatbot into a conversational assistant by introducing memory. Instead of treating every query independently, the chatbot now understands previous messages and generates context-aware responses.
