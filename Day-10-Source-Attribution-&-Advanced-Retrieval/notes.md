# 📅 Day 10 – Source Attribution & Advanced Retrieval

## 🎯 Objective

In Day 10, we improved our RAG system by making it **trustworthy**. Instead of only generating answers, the chatbot can now show **where the answer came from** using document metadata and better retrieval strategies.

---

# 📖 What We Learned

A normal RAG chatbot answers questions but cannot explain the source of the information.

Example:

```text
User:
What is CNN?

Bot:
CNN is used for image processing.
```

User asks:

```text
Which page contains this information?
```

To solve this, we introduced **Source Attribution**.

---

# 📚 Source Attribution

Source Attribution means displaying the document source along with the generated answer.

Example:

```text
Answer:
CNN is used in image processing.

Source:
DeepLearning.pdf
Page 8
```

This increases user trust and transparency.

---

# 📑 Metadata

Every document chunk contains additional information called **Metadata**.

Example:

```python
{
    "source": "DeepLearning.pdf",
    "page": 8
}
```

Metadata helps identify the origin of retrieved content.

---

# 🎯 Similarity Score

Retriever calculates how similar a document chunk is to the user's question.

```text
Lower Score
=
Better Match

Higher Score
=
Less Relevant
```

Similarity scores help filter weak retrieval results.

---

# 🚀 Maximum Marginal Relevance (MMR)

Instead of returning highly repetitive chunks, **MMR (Maximum Marginal Relevance)** retrieves documents that are both:

* Relevant
* Diverse

Example:

Without MMR

```text
CNN Definition
CNN Definition
CNN Definition
```

With MMR

```text
CNN Definition
CNN Applications
CNN Advantages
```

This provides richer context to the LLM.

---

# 📌 Updated Production RAG Flow

```text
User Question
        │
        ▼
MMR Retriever
        │
        ▼
Relevant Chunks
+
Metadata
        │
        ▼
Prompt
        │
        ▼
Gemini
        │
        ▼
Answer
+
Sources
```

---

# ✅ Advantages

* Explainable AI
* Better Retrieval Quality
* Higher User Trust
* Production-Ready RAG
* Reduced Hallucinations
* Source Verification

---

# 🔑 Keywords

* Metadata
* Source Attribution
* Similarity Score
* MMR (Maximum Marginal Relevance)
* Explainable AI
* Production RAG

---

# 📌 Summary

Day 10 focused on making our RAG system more reliable and production-ready. We learned how to attach document metadata, display citations, evaluate retrieval quality using similarity scores, and improve retrieval using MMR so the chatbot generates more trustworthy and explainable responses.
