# Enterprise AI Audio/Video Analyzer

An advanced, production-ready AI pipeline designed to process, transcribe, summarize, and query long audio and video files using state-of-the-art machine learning models and cloud APIs.

## Core Features
* **Groq Whisper API (whisper-large-v3):** High-fidelity transcription and automatic English translation of media files with optimized speed.
* **Smart Audio Chunking:** Utilizes `pydub` and `AudioSegment` to intelligently divide long audio files into 10-minute segments, seamlessly bypassing API file size limits and ensuring robust processing.
* **Rate-Limit Guard:** Built-in pacing logic (`time.sleep`) during API calls to prevent "Rate Limit Exceeded" errors during heavy chunk transmissions.
* **Llama 3.1 (Map-Reduce Strategy):** Powered by the Groq API, this system employs a robust Map-Reduce chain with automatic retry mechanism to generate structured, section-by-section summaries for long-form videos.
* **FAISS Vector Database:** Converts text chunks into high-density vector embeddings using HuggingFace's `BAAI/bge-small-en-v1.5` model for fast, context-aware Retrieval-Augmented Generation (RAG).
* **Interactive Gradio UI:** A clean and modern user interface featuring a dedicated Summary tab and a live Q&A Chatbot for interactive querying.

## System Architecture & Flow
1. **Input:** Local media file upload or public Google Drive link extraction via `gdown`.
2. **Preprocessing:** Audio extraction and 10-minute chunking via `pydub`.
3. **Transcription:** Sequential API translation/transcription to English text via Groq Whisper.
4. **Indexing:** Overlapping character splitting and vector database generation using FAISS.
5. **Reasoning:** Dynamic map-reduce prompt orchestration powered by Llama 3.1 for comprehensive master summaries and context-retrieved chatbot interaction.

## Installation & Setup
1. Clone this repository to your workstation.
2. Install all core dependencies listed in the requirements file:
   ```bash
   pip install -r requirements.txt
