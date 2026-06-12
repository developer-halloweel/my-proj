# Hugging Face LLM Website Scraping RAG

A Retrieval-Augmented Generation (RAG) project that scrapes content from multiple websites, converts the content into embeddings using Hugging Face models, stores them in a vector database, and answers user queries using a Hugging Face Language Model.

This project demonstrates the complete RAG pipeline:

1. Web Scraping
2. Document Chunking
3. Embedding Generation
4. Vector Database Storage
5. Semantic Retrieval
6. LLM-Based Question Answering

---

## Project Overview

Traditional LLMs are limited to their training data and cannot access newly published information. Retrieval-Augmented Generation (RAG) solves this problem by retrieving relevant external documents and providing them as context to the language model before generating an answer.

In this project, articles related to the Indian Union Budget 2024 are scraped from multiple websites and indexed into a vector database. When a user asks a question, the system retrieves the most relevant document chunks and generates an answer using a Hugging Face LLM.

---

## Features

* Website content extraction using LangChain URL Loader
* Automatic document chunking
* Semantic embeddings using Sentence Transformers
* Chroma Vector Database integration
* Similarity-based document retrieval
* Hugging Face LLM integration
* End-to-end RAG pipeline
* Fully open-source implementation

---

## Architecture

```text
Web URLs
    │
    ▼
Website Scraping
    │
    ▼
Document Loading
    │
    ▼
Text Chunking
    │
    ▼
Embedding Generation
    │
    ▼
Chroma Vector Store
    │
    ▼
Retriever
    │
    ▼
Relevant Context
    │
    ▼
Hugging Face LLM
    │
    ▼
Generated Answer
```

---

## Tech Stack

| Technology                | Purpose                    |
| ------------------------- | -------------------------- |
| Python                    | Core Programming Language  |
| LangChain                 | RAG Pipeline Framework     |
| Hugging Face Transformers | Language Models            |
| Sentence Transformers     | Embedding Generation       |
| ChromaDB                  | Vector Database            |
| Unstructured              | Website Content Extraction |
| PyTorch                   | Deep Learning Backend      |

---

## Project Structure

```text
Huggingface-llm-Websitescrap-Rag/
│
├── huggingface_llm_RAG.ipynb
├── requirement.txt
└── README.md
```

---

## Installation

### Clone the Repository

```bash
git clone https://github.com/your-username/Huggingface-llm-Websitescrap-Rag.git
cd Huggingface-llm-Websitescrap-Rag
```

### Create a Virtual Environment

```bash
python -m venv venv
```

#### Windows

```bash
venv\Scripts\activate
```

#### Linux / Mac

```bash
source venv/bin/activate
```

### Install Dependencies

```bash
pip install -r requirement.txt
```

---

## Dependencies

```text
torch
transformers
sentence-transformers
langchain
langchain_community
langchain-huggingface
langchain_experimental
langchain_chroma
langchainhub
streamlit
unstructured
```

---

## How It Works

### 1. Load Website Data

```python
loader = UnstructuredURLLoader(urls=urls)
data = loader.load()
```

### 2. Split Documents

```python
text_splitter = RecursiveCharacterTextSplitter(
    chunk_size=1000
)

docs = text_splitter.split_documents(data)
```

### 3. Generate Embeddings

Embedding model:

```text
sentence-transformers/all-mpnet-base-v2
```

```python
embedding_model = HuggingFaceEmbeddings(
    model_name="sentence-transformers/all-mpnet-base-v2"
)
```

### 4. Store Embeddings in ChromaDB

```python
vectorstore = Chroma.from_documents(
    documents=docs,
    embedding=embedding_model
)
```

### 5. Retrieve Relevant Chunks

```python
retriever = vectorstore.as_retriever(
    search_type="similarity",
    search_kwargs={"k": 3}
)
```

### 6. Generate Answers

Language Model:

```text
distilgpt2
```

```python
rag_chain.invoke(question)
```

---

## Example Query

### Input

```text
What is the Union Budget?
```

### Output

```text
The Union Budget is the annual financial statement of the Government of India that outlines expected revenue and expenditure for the upcoming fiscal year.
```

---

## Models Used

### Embedding Model

**sentence-transformers/all-mpnet-base-v2**

Purpose:

* Semantic embeddings
* High-quality retrieval
* Efficient vector search

### Language Model

**distilgpt2**

Purpose:

* Lightweight text generation
* Fast inference
* Suitable for educational RAG implementations

---

## Applications

* AI Chatbots
* Knowledge Base Assistants
* Document Question Answering
* Research Assistants
* Financial Report Analysis
* Enterprise Search Systems
* Educational AI Tools

---

## Future Improvements

* Upgrade to Llama 3
* Upgrade to Mistral 7B
* Add Streamlit Frontend
* Add PDF Support
* Persistent Vector Storage
* Conversation Memory
* Source Attribution
* Hybrid Search (BM25 + Vector Search)
* Deploy on Hugging Face Spaces

---

## Learning Outcomes

This project demonstrates:

* Retrieval-Augmented Generation (RAG)
* LangChain Framework
* Hugging Face Ecosystem
* Vector Databases
* Semantic Search
* Embedding Models
* Information Retrieval
* LLM Integration

---

## Author

**Ronak Das**

B.Tech, National Institute of Technology Silchar

Areas of Interest:

* Machine Learning
* Data Science
* Generative AI
* Software Development

GitHub: https://github.com/developer-halloweel

---

## License

This project is licensed under the MIT License.

Feel free to use, modify, and distribute this project for educational and research purposes.
