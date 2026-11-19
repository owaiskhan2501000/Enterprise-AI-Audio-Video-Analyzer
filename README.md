# Enterprise AI Audio/Video Analyzer

An end-to-end multimodal RAG pipeline that processes local audio/video files or public Google Drive links to transcribe long media, generate structured summaries, and answer context-grounded questions through an interactive Gradio web interface.

## Key Features

- **Groq Whisper AI (Large-v3):** Transcribes and translates multilingual audio directly into English. Uses Pydub chunking to split long recordings into 10-minute segments to stay within API file size limits.
- **FAISS Vector Database:** Splits the transcript into overlapping 1,000-character chunks and indexes them in FAISS using HuggingFace embeddings (`BAAI/bge-small-en-v1.5`) for fast semantic retrieval.
- **Llama 3.1 (via ChatGroq):** Powers both context-aware Q&A retrieval and dynamic summarization.
- **Smart Map-Reduce Summarization:** Automatically switches to a Map-Reduce workflow for long media, handling API rate limits (HTTP 429) with retry and backoff logic before merging chunk summaries into a single master summary.
- **Interactive Gradio UI:** Provides dedicated tabs for the generated **Summary** and an interactive **Q&A Chatbot**.

## Tech Stack & Dependencies

- **Orchestration:** LangChain (`langchain`, `langchain-core`, `langchain-community`, `langchain-text-splitters`)
- **LLM & Transcription:** ChatGroq (Llama 3.1), Groq Whisper API (`large-v3`)
- **Vector Store & Embeddings:** FAISS (`faiss-cpu`), HuggingFace (`sentence-transformers`, `langchain-huggingface`)
- **Media Processing:** Pydub, `gdown`
- **User Interface:** Gradio

## Installation & Setup

To run this project locally or in Google Colab:

**1. Clone the Repository & Install Dependencies:**

```bash
git clone [https://github.com/owaiskhan2501000/Enterprise-AI-Audio-Video-Analyzer.git](https://github.com/owaiskhan2501000/Enterprise-AI-Audio-Video-Analyzer.git)
cd Enterprise-AI-Audio-Video-Analyzer
pip install -r requirements.txt
