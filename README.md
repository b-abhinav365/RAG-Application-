# RAG-Application-
A system that allows users to ask questions about their documents and get intelligent answers powered by a Large Language Model (LLM).

# RAG Application

## Project Aim

This project is a simple Retrieval-Augmented Generation (RAG) application.  
Its main aim is to allow users to ask questions about their own documents and get meaningful answers using an LLM.

Instead of the LLM guessing from general knowledge, the project first searches the uploaded/local documents, finds the most relevant content, and then uses that content to generate a better answer.

## What This Project Does

The project:

1. Loads documents from the `rag/data` folder.
2. Supports multiple file types like PDF, TXT, CSV, Excel, Word, and JSON.
3. Splits large documents into smaller text chunks.
4. Converts those chunks into embeddings using `sentence-transformers`.
5. Stores the embeddings in a FAISS vector database.
6. Searches the most relevant document chunks for a user query.
7. Uses Groq LLM to summarize the answer based on the retrieved content.

## Tech Stack

- Python
- LangChain
- FAISS
- Sentence Transformers
- Groq LLM
- Python Dotenv

## Project Structure

```text
rag/
├── app.py
├── src/
│   ├── data_loader.py
│   ├── embedding.py
│   ├── vector_store.py
│   └── search.py
├── rag/
│   ├── data/
│   │   ├── pdf/
│   │   └── text_files/
│   └── requirements.txt
├── faiss_store/
├── .env
└── README.md

## Setup Instructions

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd rag
```

### 2. Create a Virtual Environment

```bash
python -m venv .venv
```

### 3. Activate the Virtual Environment

For Windows:

```bash
.venv\Scripts\activate
```

For macOS/Linux:

```bash
source .venv/bin/activate
```

### 4. Install Dependencies

```bash
pip install -r rag/requirements.txt
```

### 5. Create a `.env` File

Create a `.env` file in the root folder and add your Groq API key:

```env
GROQ_API_KEY=your_groq_api_key_here
```

### 6. Add Documents

Place your documents inside the `rag/data` folder.

Supported file types include:

- PDF
- TXT
- CSV
- Excel
- Word
- JSON

### 7. Run the Application

```bash
python app.py
```

## Example Query

The query is currently written inside `app.py`:

```python
query = "What is attention mechanism?"
```

You can change this query to ask any question related to your documents.

## Example Output

```text
Summary: The attention mechanism is a technique used in deep learning models that helps the model focus on the most important parts of the input data while generating an output.
```he required packages
