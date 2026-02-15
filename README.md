# Multi-Agentic HR System for Company Queries

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue)](https://python.org)
[![LangChain](https://img.shields.io/badge/LangChain-black)](https://langchain.com)
[![Groq](https://img.shields.io/badge/Groq-Fast-green)](https://groq.com)
[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

A multi-agent system built with LangGraph/LangChain that routes employee questions (e.g., leave, pay, travel) to specialist RAG agents using company policy PDFs. Handles internal policies via vector DB and web search for jobs/news. Demo UI with Gradio.

## Features
- Router agent directs queries to Leave, Travel, Pay specialists or web search.
- RAG over 40+ policy PDFs (ChromaDB + HuggingFace embeddings).
- LLMs: Groq (Llama3), supports Gemini.
- Gradio chat interface.

## Prerequisites
- Google account for Colab.
- **API Keys** (set as Colab secrets—**do not commit them!**):
  - Gemini API Key (via [Google AI Studio](https://aistudio.google.com)).
  - Groq API Key (free at [console.groq.com](https://console.groq.com)—add `llama-3.3-70b-versatile`).
  - Hugging Face token (for embeddings: [huggingface.co/settings/tokens](https://huggingface.co/settings/tokens)).
- GPU runtime in Colab (Runtime > Change runtime type > T4 GPU).

## Quickstart
1. **Download Sample Data**: Get the [Policy Guides ZIP](https://github.com/LeslieK-Lab/multi-agent-hr-rag/releases/latest) (or your Drive link). Unzip to Google Drive (e.g., `/MyDrive/module5assignment/`).
2. **Open Notebook in Colab**:
   - Download `Agentic_System_Multi_Agentic.ipynb` from this repo.
   - Go to https://colab.research.google.com → **File → Upload notebook**.
   - Select the downloaded `.ipynb` file and open it in your own Colab workspace.
3. **Mount Drive & Set Path**:
   ```python
   SOURCE_DATA_DIR = "/content/drive/MyDrive/module5assignment"
   # Paste your "Copy path" here
4. Add Secrets (Notebook sidebar → 🔑 Secrets):
   - GEMINI_API_KEY: your-key
   - GROQ_API_KEY: your-key
   - HF_TOKEN: your-token
5. Run All Cells: Installs dependencies, ingests PDFs (~7775 docs), builds agents, launches Gradio.
6. Test: Ask How many days of annual leave am I entitled to? → should route to the Leave specialist.
