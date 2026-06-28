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

##Setup Instructions:
1. Clone the repository
git clone <your-repository-url>
cd rag

2. Create a virtual environment
python -m venv .venv

3. Activate the virtual environment
For Windows:
.venv\Scripts\activate
For macOS/Linux:
source .venv/bin/activate

4. Install dependencies
pip install -r rag/requirements.txt

5. Add your API key
Create a .env file in the root folder and add:
GROQ_API_KEY=your_groq_api_key_here

6. Run the project
python app.py

How It Works:
When the project runs, it loads documents from the rag/data folder.
If a FAISS vector store already exists, it loads the saved index. Otherwise, it creates a new vector store from the documents.

The current query is written inside app.py:
query = "What is attention mechanism?"

(You can change this question to ask something else based on your documents.)

Example Output:
Summary: The attention mechanism is a technique used in deep learning models...


Notes:
Do not upload your .env file to GitHub.
The faiss_store folder is generated automatically and can be recreated.
Add your own PDFs or text files inside the rag/data folder.

I also checked the project locally. `python app.py` currently fails only because the required packages
