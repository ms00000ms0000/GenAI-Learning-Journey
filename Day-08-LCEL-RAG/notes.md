# 🎯 Objective

Learn how to automate the RAG workflow using **LCEL (LangChain Expression Language)** and build a cleaner, reusable, and production-style RAG pipeline.

---

# 📚 What We Learned

Until Day 7, we manually performed each step of the RAG pipeline:

```text
User Query
↓
Retriever
↓
Retrieve Chunks
↓
Create Context
↓
Create Prompt
↓
Send to Gemini
↓
Generate Answer
```

This works but becomes difficult to manage as projects grow.

**LCEL solves this problem by connecting components into a pipeline.**

---

# 🚀 What is LCEL?

## Definition

**LCEL (LangChain Expression Language)** is a modern syntax used to connect LangChain components into a pipeline using the `|` operator.

### Example

```python
chain = prompt | llm
```

### Meaning

```text
Prompt
↓
LLM
```

The output of the prompt automatically becomes the input of the LLM.

---

# 🤔 Why Do We Need LCEL?

## Without LCEL

```text
Retrieve Documents
↓
Convert to Context
↓
Create Prompt
↓
Call LLM
↓
Extract Response
```

Multiple manual steps.

---

## With LCEL

```text
Question
↓
Chain
↓
Answer
```

Single reusable pipeline.

---

# 🏗️ Components Used in LCEL RAG

## 1️⃣ Document Loader

Loads data from PDFs and other files.

```python
PyPDFLoader()
```

---

## 2️⃣ Text Splitter

Creates chunks from large documents.

```python
RecursiveCharacterTextSplitter()
```

---

## 3️⃣ Embedding Model

Converts text into vector representations.

```python
HuggingFaceEmbeddings()
```

---

## 4️⃣ Vector Store

Stores embeddings.

### Examples

- FAISS
- ChromaDB
- Pinecone

---

## 5️⃣ Retriever

Retrieves the most relevant chunks.

```python
retriever = vector_store.as_retriever()
```

---

## 6️⃣ Prompt Template

Creates reusable prompts.

```python
ChatPromptTemplate
```

---

## 7️⃣ LLM

Generates answers.

### Example

```python
ChatGoogleGenerativeAI
```

---

## 8️⃣ Output Parser

Converts model output into a clean format.

```python
StrOutputParser()
```

---

# 🔍 What is RunnablePassthrough?

## Definition

A component that passes the user input unchanged to the next step.

### Example

```python
RunnablePassthrough()
```

### Flow

```text
User Question
↓
Pass Without Modification
↓
Prompt Template
```

---

# 📤 What is StrOutputParser?

## Definition

Converts the raw LLM response into a clean string.

### Example

#### Before

```python
AIMessage(
    content="Backpropagation is..."
)
```

#### After

```text
Backpropagation is...
```

---

# 🧩 Building an LCEL RAG Chain

## Traditional RAG

```text
Question
↓
Retriever
↓
Context
↓
Prompt
↓
LLM
↓
Answer
```

---

## LCEL RAG

```python
rag_chain = (
    {
        "context": retriever | format_docs,
        "question": RunnablePassthrough()
    }
    | prompt
    | llm
    | StrOutputParser()
)
```

---

# 🔄 Understanding the LCEL Pipeline

## Step 1

User asks a question.

```text
What is Backpropagation?
```

---

## Step 2

Retriever finds the most relevant chunks.

```text
Chunk 12
Chunk 24
Chunk 35
```

---

## Step 3

`format_docs()` converts retrieved chunks into a single context string.

```text
Chunk 12
+
Chunk 24
+
Chunk 35
```

---

## Step 4

Prompt Template receives:

```text
Context
+
Question
```

---

## Step 5

Gemini receives the final prompt.

---

## Step 6

StrOutputParser converts the output into clean text.

---

## Step 7

Final answer is returned.

---

# 📊 LCEL Architecture

```text
Question
↓
Retriever
↓
Relevant Chunks
↓
format_docs()
↓
Context
↓
PromptTemplate
↓
Gemini
↓
StrOutputParser
↓
Answer
```

---

# 🔥 Complete Automated RAG Flow

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
LCEL Chain
↓
Gemini
↓
Answer
```

---

# ⚖️ Manual RAG vs LCEL RAG

## Manual RAG

```text
Query
↓
Retrieve Chunks
↓
Build Context
↓
Create Prompt
↓
Generate Response
```

### Advantages

- Easy to understand
- Good for learning

### Disadvantages

- Repetitive code
- Difficult to scale

---

## LCEL RAG

```text
Query
↓
LCEL Chain
↓
Response
```

### Advantages

- Cleaner code
- Reusable
- Production-ready
- Easy to extend

---

# 🏢 Why Industry Uses LCEL

LCEL makes it easy to add:

```text
Memory
Chat History
Agents
Tools
Multiple Retrievers
Routing
Guardrails
```

without rewriting the entire application.

---

# 📌 Key Definitions (One-Liners)

## LCEL

A language for connecting LangChain components into pipelines using the `|` operator.

---

## RunnablePassthrough

A component that forwards input unchanged to the next component.

---

## StrOutputParser

Converts raw LLM output into a plain text string.

---

## ChatPromptTemplate

A reusable prompt template designed for chat models.

---

## Automated RAG

A RAG pipeline where retrieval, prompting, and generation are connected through chains.

---

## Pipeline

A sequence of connected components that process data step-by-step.
