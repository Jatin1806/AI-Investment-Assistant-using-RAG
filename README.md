# AI-Investment-Assistant-using-RAG
It is a lightweight RAG (Retrieval-Augmented Generation) application designed to answer investment-related queries using real-time financial data. It retrieves real-time financial data from trusted websites like Screener.in, Yahoo Finance, and Moneycontrol, processes it using LLMs, and gives data-driven investment suggestions.


#How It Works

| Component             | Description                                                                                                      |
| --------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **Input**             | A user query such as "Should I invest in Zomato?"                                                                |
| **Entity Extraction** | Extracted the company name (`Zomato`) from the question using regex                                              |
| **Web Retrieval**     | Scraped financial data from `Screener.in`, `Yahoo Finance`, and `Moneycontrol` using `WebBaseLoader`             |
| **Text Chunking**     | Split large HTML pages into small 1000-token chunks for better semantic retrieval                                |
| **Embeddings**        | Converted text chunks into numerical vectors using `HuggingFaceEmbeddings`                                       |
| **Vector Store**      | Stored vectorized documents in a local persistent DB using `Chroma`                                              |
| **Retriever**         | On query, pulled top relevant chunks using semantic similarity (`k=5`)                                           |
| **LLM + RAG Chain**   | Passed those chunks to `Llama3` via `Groq API` using a custom prompt and LangChain's modern `retrieval_qa_chain` |
| **Answer**            | Returned a well-structured investment suggestion with reasoning                                                  |



#Tech Stack
| Tool                      | Purpose                              |
| ------------------------- | ------------------------------------ |
| **LangChain**             | Framework to orchestrate LLM chains  |
| **WebBaseLoader**         | Web scraper for live page content    |
| **Chroma**                | Local vector database for embeddings |
| **HuggingFaceEmbeddings** | Free, local sentence embedding model |
| **Groq (Llama3)**         | Ultra-fast, low-latency LLM backend  |
| **PromptTemplate**        | Custom prompt to shape model output  |
