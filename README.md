# AI-Powered-Financial-Document-Analyst
A Q&amp;A system for financial documents (10-K reports) using a RAG architecture. Built with LangChain and powered by the Llama 3.1 8B model.


🤖 AI-Powered Financial Document Analyst
📜 Overview
This project is a sophisticated question-answering system designed to act as an expert financial analyst. It leverages a powerful 8-billion parameter language model (meta-llama/Llama-3.1-8B-Instruct) and a Retrieval-Augmented Generation (RAG) pipeline to analyze dense financial documents, such as annual 10-K reports. Users can upload a PDF and ask complex questions in natural language to receive precise, context-aware answers based solely on the document's contents.

The final application is deployed as an interactive web UI using Streamlit, running within a Google Colab environment to utilize its GPU capabilities.

✨ Features
PDF Document Ingestion: Upload any financial report in PDF format.

Advanced RAG Pipeline: The system chunks the document, creates vector embeddings, and stores them in a FAISS vector store for efficient similarity search.

Intelligent Q&A: Ask complex questions and receive accurate answers synthesized directly from the document's text.

High-Performance LLM: Powered by the Llama 3.1 8B Instruct model for superior reasoning and text generation.

Interactive Web UI: A user-friendly interface built with Streamlit for easy document upload and interaction.

🛠️ Tech Stack
Large Language Model: meta-llama/Llama-3.1-8B-Instruct

Frameworks: LangChain, Transformers

Vector Database: FAISS (Facebook AI Similarity Search)

Embeddings: sentence-transformers/all-MiniLM-L6-v2

UI & Deployment: Streamlit, Google Colab, ngrok

Core Libraries: PyTorch, Accelerate, PyPDF

🧠 How It Works
The application is built on a Retrieval-Augmented Generation (RAG) architecture:

Load & Chunk: The uploaded PDF is loaded and split into smaller, semantically meaningful chunks.

Embed & Store: Each chunk is converted into a numerical vector (embedding) and stored in a FAISS index, creating a searchable knowledge base.

Retrieve: When a user asks a question, the system searches the FAISS index to find the most relevant chunks of text from the original document.

Generate: The retrieved chunks (the context) are passed along with the user's question to the Llama 3.1 model, which then generates a precise answer based on the provided information.

💡 Challenges & Solutions
A key challenge was running the 16GB Llama 3.1 model and the embedding model on the memory-constrained T4 GPU in the free Google Colab environment. This initially caused CUDA out of memory errors.

Solution: I implemented a strategic memory management workflow. After the FAISS vector store is created, the embedding model is programmatically unloaded from the GPU cache. This frees up critical VRAM, allowing the primary LLM to have sufficient resources for the final, computationally intensive generation step.

🚀 Usage
The project is designed to be run within a Google Colab notebook to leverage the free GPU resources.

Clone the repository.

Open the Compelte_final_code.ipynb notebook in Google Colab.

Ensure your Colab runtime is set to T4 GPU.

Run the cells in order to launch the Streamlit application via an ngrok tunnel.
