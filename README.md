
# 🔍 AI Investment Assistant using RAG

## 📘 Project Summary

This is a simple but powerful **Research-Augmented Generation (RAG)** based AI assistant that answers investment-related questions like:

> “Should I invest in Zomato?”

It retrieves real-time data from trusted financial websites, processes it using embeddings and large language models (LLMs), and gives a **data-backed investment suggestion**.

---

## ⚙️ How It Works

| Component             | Description                                                                                                      |
|----------------------|------------------------------------------------------------------------------------------------------------------|
| **Input**             | A user query such as `"Should I invest in Zomato?"`                                                              |
| **Entity Extraction** | Extracts the company name (`Zomato`) from the question using regex                                               |
| **Web Retrieval**     | Scrapes financial data from `Screener.in`, `Yahoo Finance`, and `Moneycontrol` using `WebBaseLoader`             |
| **Text Chunking**     | Splits large HTML documents into 1000-token chunks for improved semantic search                                  |
| **Embeddings**        | Converts text chunks into vector embeddings using `HuggingFaceEmbeddings`                                        |
| **Vector Store**      | Stores vectorized chunks in a persistent vector DB using `Chroma`                                                |
| **Retriever**         | Retrieves top-`k` semantically relevant chunks from the vector DB (e.g. `k=5`)                                    |
| **LLM + RAG Chain**   | Passes retrieved chunks to `Llama3` model via `Groq API` using LangChain's `retrieval_qa_chain` with custom prompt |
| **Answer**            | Returns a well-structured investment suggestion based on facts + reasoning                                       |

---

## 🧰 Tech Stack

| Tool                      | Purpose                              |
|---------------------------|--------------------------------------|
| **LangChain**             | Framework to orchestrate LLM chains  |
| **WebBaseLoader**         | Web scraper for live page content    |
| **Chroma**                | Local vector database for embeddings |
| **HuggingFaceEmbeddings** | Free, local sentence embedding model |
| **Groq (Llama3)**         | Ultra-fast, low-latency LLM backend  |
| **PromptTemplate**        | Custom prompt to shape model output  |

---

## 🧠 Example Question

```bash
Q: Should I currently invest in Zomato?
