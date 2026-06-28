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

Create a `.env` file in the root folder of the project and add your Groq API key:

```env
GROQ_API_KEY=your_groq_api_key_here
```

### 6. Add Your Documents

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

## Project Structure

```text
rag/
├── app.py
├── src/
│   ├── __init__.py
│   ├── data_loader.py
│   ├── embedding.py
│   ├── vector_store.py
│   └── search.py
├── rag/
│   ├── data/
│   │   ├── pdf/
│   │   └── text_files/
│   ├── notebook/
│   ├── requirements.txt
│   ├── pyproject.toml
│   └── main.py
├── faiss_store/
│   ├── faiss.index
│   └── metadata.pkl
├── .env
├── .gitignore
└── README.md
```

## How It Works

This project is a Retrieval-Augmented Generation, or RAG, application.

The aim of this project is to allow users to ask questions about their own documents and get meaningful answers using a Large Language Model, also known as an LLM.

Instead of directly asking the LLM to answer from general knowledge, this project first searches your documents and finds the most relevant content. Then it sends that content to the LLM so the answer is based on your document data.

The application works in the following steps:

1. Documents are added inside the `rag/data` folder.
2. The project loads supported files such as PDF, TXT, CSV, Excel, Word, and JSON.
3. The documents are split into smaller text chunks.
4. Each text chunk is converted into embeddings using a sentence transformer model.
5. These embeddings are stored in a FAISS vector database.
6. When a user asks a question, the question is also converted into an embedding.
7. FAISS compares the question embedding with the stored document embeddings.
8. FAISS retrieves the most relevant document chunks.
9. The retrieved chunks are passed to the Groq LLM.
10. The LLM generates a summarized answer using the retrieved document content.

In simple words, this project works like a smart document question-answering system. It searches your files first and then uses AI to generate an answer from the most useful information.

## Example Query

The query is currently written inside `app.py`:

```python
query = "What is attention mechanism?"
```

You can change this query to ask any question related to your documents.

For example:

```python
query = "What are the main points in the proposal?"
```

```python
query = "Explain machine learning in simple words."
```

```python
query = "Summarize the document content."
```

## Example Output

```text
Summary: The attention mechanism is a technique used in deep learning models that helps the model focus on the most important parts of the input data while generating an output.
```

## Notes

- Keep your `.env` file private and do not upload it to GitHub.
- The `faiss_store` folder stores the vector database files.
- If the FAISS index already exists, the project loads it directly.
- If the FAISS index does not exist, the project creates a new one from the documents.
- You can add more documents inside the `rag/data` folder and rebuild the vector store if needed.
