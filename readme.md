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
git clone https://github.com/owaiskhan2501000/Enterprise-AI-Audio-Video-Analyzer.git
cd Enterprise-AI-Audio-Video-Analyzer
pip install -r requirements.txt
```

**2. Configure API Key:**

Set your Groq API key as an environment variable (or store it in Google Colab **Secrets** as `GROQ_API_KEY`):

```python
import os
os.environ["GROQ_API_KEY"] = "your_groq_api_key_here"
```

**3. Run the Notebook:**

Open `Enterprise_AI_Audio_Video_Analyzer.ipynb` in Google Colab or Jupyter Notebook and run all cells to launch the Gradio interface.

## System Architecture / Workflow

1. **Media Input:** Upload a local audio/video file or paste a public Google Drive link.
2. **Audio Extraction & Chunking:** Extract audio and split long files into 10-minute segments via Pydub.
3. **Transcription:** Transcribe and translate each segment into English using Groq Whisper (`large-v3`).
4. **Vectorization:** Chunk the full transcript and store embeddings in a FAISS vector index.
5. **Summarization:** Generate a direct summary for shorter transcripts or run Map-Reduce summarization for long recordings.
6. **Interactive Q&A:** Retrieve top relevant transcript chunks from FAISS and generate grounded answers with Llama 3.1.

## Important Note

For best transcription accuracy, use recordings with clear human speech. Heavily synthesized or distorted audio may reduce transcription quality.

## License

This project is licensed under the [MIT License](https://www.google.com/search?q=LICENSE).

## Developer

**Mohammad Owais** — AI & Full-Stack Software Developer

- **Email:** owaiskhan2501000@gmail.com
- **Portfolio:** https://owais-portfolio-web.vercel.app/
- **LinkedIn:** https://www.google.com/search?q=https://linkedin.com/in/mohammad-owais-cs-13607ai/
- **GitHub:** https://github.com/owaiskhan2501000
