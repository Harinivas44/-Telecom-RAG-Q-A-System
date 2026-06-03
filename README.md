# 📡 Telecom RAG Q&A System

A Retrieval-Augmented Generation (RAG) pipeline that answers telecom support questions by grounding an LLM in a private PDF knowledge base — built with LangChain, ChromaDB, HuggingFace Embeddings, and Groq (Qwen3-32B).


### 🧠 What It Does
This project builds a document-grounded Q&A system over a private telecom reference guide. Instead of relying on an LLM's general training knowledge, every answer is retrieved from and grounded in the actual PDF document — making responses accurate, traceable, and hallucination-resistant.


### 🔄 RAG Pipeline — Step by Step

PDF Document

     │
     ▼
     
[1] PDF Loader          →  Loads 9 pages using PyPDFLoader

     │
     ▼
     
[2] Text Splitter       →  Splits into 37 chunks (size=600, overlap=100)

     │
     ▼
     
[3] Embeddings          →  Encodes chunks via sentence-transformers/all-MiniLM-L6-v2

     │
     ▼
     
[4] Vector Store        →  Stores 37 vectors in ChromaDB (in-memory)

     │
     ▼
     
[5] Retriever           →  Fetches top-3 relevant chunks per query (k=3)

     │
     ▼
     
[6] LLM (Qwen3-32B)     →  Generates answer using ONLY retrieved context

     │
     ▼
     
Final Answer
