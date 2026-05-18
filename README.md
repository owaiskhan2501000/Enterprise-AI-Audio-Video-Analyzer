# Enterprise AI Audio/Video Analyzer

This project is a complete AI pipeline designed to process any audio or video file, or public Google Drive link. The primary goal of this system is to analyze long videos or audios, generate comprehensive summaries, and answer questions based on their content using RAG (Retrieval-Augmented Generation).

## Key Features

* **Groq Whisper AI (Large-v3)**: Automatically transcribes and translates audio from any language directly into English. It utilizes Pydub chunking to divide long files into 10-minute segments, effectively bypassing API file size limits.
* **FAISS Vector Database**: Divides the complete transcription into small, overlapping chunks (1000 characters) and stores them in a FAISS vector database using HuggingFace embeddings (`BAAI/bge-small-en-v1.5`). This ensures fast and accurate context retrieval.
* **Llama 3.1 (via ChatGroq)**: Serves as the core reasoning engine that handles both the Q&A retrieval and the dynamic summarization tasks.
* **Smart Map-Reduce Summarization**: If the media is exceptionally long, the system automatically shifts to a Map-Reduce strategy. It creates separate summaries for smaller chunks, gracefully handles API rate limits (Error 429) using auto-retry and wait-time logic, and ultimately merges them into a single cohesive "Master Summary".
* **Interactive Web UI**: Built with the Gradio framework, the application features a user-friendly interface containing dedicated tabs for the generated "Summary" and an interactive "Q&A Chatbot".

## Tech Stack & Dependencies

This project leverages the following modern AI frameworks and libraries:

* **Orchestration**: LangChain (`langchain`, `langchain-core`, `langchain-community`)
* **LLM & Transcription**: ChatGroq (Llama 3.1), Groq Whisper API
* **Vector Store & Embeddings**: FAISS (`faiss-cpu`), HuggingFace (`sentence-transformers`, `langchain-huggingface`)
* **Media Processing**: Pydub (for audio chunking)
* **User Interface**: Gradio

## Installation & Setup

To run this project in your local environment or Google Colab, follow these steps:

**1. Install Core Dependencies:**

```bash
pip install -q --upgrade langchain langchain-core langchain-community langchain-groq langchain-huggingface langchain-text-splitters faiss-cpu gradio sentence-transformers pydub gdown
```

**2. Configure API Keys:**

This project requires a Groq API key for fast LLM inference. In Google Colab, configure this using 'Secrets' or set it as an environment variable in your script:

```python
import os
os.environ["GROQ_API_KEY"] = "your_groq_api_key_here"
```

## System Architecture / Workflow

1. **Media Upload**: The user uploads a local media file or provides a public Google Drive link.
2. **Audio Extraction & Chunking**: The media is processed and divided into 10-minute audio chunks to optimize API payload.
3. **Transcription**: Each chunk is sent to the Groq API (Whisper-Large-v3) to be transcribed and translated into English.
4. **Vectorization**: The full text is split via LangChain text splitters and embedded into a FAISS database.
5. **Summarization**: Based on the transcript's length, the AI determines whether to generate a direct summary or utilize the Map-Reduce workflow.
6. **Chatbot Interaction**: The user queries the system, and the retriever extracts relevant context for Llama 3.1 to generate accurate, context-aware answers.

## Important Note

For optimal transcription accuracy and the best overall results, please ensure the input media contains original, human voices. AI-generated voices or heavily synthesized audio may negatively impact the transcription quality.

## Developer

**Mohammad Owais**
AI Integration Engineer | RAG & LLM Specialist | Full-Stack Developer (Next.js) | 
