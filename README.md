# Chat_with_Local_Documents
This project is a Streamlit-based application that allows users to chat with their local documents using Retrieval-Augmented Generation (RAG). The app integrates LangChain, ChromaDB, and Ollama (with a local deepseek-r1:8b model) to retrieve relevant document chunks and generate contextual answers.
## 🚀 Features

Document ingestion: Automatically loads and chunks text files from the current working directory.

Vector database: Stores and retrieves embeddings using ChromaDB and SentenceTransformer embeddings.

RAG pipeline: Retrieves the most relevant document chunks for each query.

Local LLM: Uses Ollama with the deepseek-r1:8b model for answering questions.

Chat interface: Built with Streamlit’s chat UI for interactive Q&A.

Transparent reasoning: Separates the model’s <think> process (reasoning) from the final response, shown in an expandable section.

## 🛠️ Tech Stack

LangChain – framework for LLM-powered applications

Chroma – vector database for storing embeddings

SentenceTransformers – for generating embeddings (all-MiniLM-L6-v2)

Ollama – local LLM runner

Streamlit – frontend interface

Python standard libraries: datetime, json, os, time
## 📂 Project Structure
```
.
├── app.py                # Main Streamlit application (your code)
├── requirements.txt      # Dependencies (see below)
├── documents/            # Directory where your local documents should be stored
└── README.md             # Project documentation
```
## 📦 Installation

Clone the repository:
```
git clone https://github.com/yourusername/chat-with-local-docs.git
cd chat-with-local-docs
```
Create a virtual environment and install dependencies:
```
python -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```
Install Ollama and pull the required model:
```
ollama pull deepseek-r1:8b
```
## ▶️ Usage

Run the Streamlit app:
```
streamlit run app.py
```
Then, open the provided local URL (e.g., http://localhost:8501) in your browser.
## 💡 How it Works

Load Documents: The app scans the current directory for text-based documents.

Split & Embed: Documents are split into 1000-character chunks and embedded using all-MiniLM-L6-v2.

ChromaDB: Embeddings are stored in a local vector store.

RAG Query: When a user asks a question, the top 5 most similar document chunks are retrieved.

LLM Answer: The context and question are passed to Ollama (deepseek-r1:8b), which generates a response.

Chat UI: Streamlit displays the model’s thought process (if available) and final answer.

## ⚠️ Notes

Make sure Ollama is installed and running in the background.

Replace deepseek-r1:8b with any other locally available model in get_local_model().

The reasoning process (<think> ... </think>) may not always appear depending on the model used.
## 📌 Roadmap

 Support for PDF, DOCX, and CSV loaders

 Option to upload documents via UI

 Persistent vector store (instead of in-memory)

 Multi-model support (choose from different Ollama models)
