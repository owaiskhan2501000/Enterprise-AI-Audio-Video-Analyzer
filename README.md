# Enterprise AI Audio/Video Analyzer

An advanced AI pipeline for processing, analyzing, and chatting with long audio and video content.

## Overview
This repository provides a powerful solution that leverages state-of-the-art AI models to transcribe, index, and query lengthy audio and video files. It is designed to help enterprises and individuals extract meaningful insights and interact seamlessly with multimedia data.

## Features
- **High-Accuracy Transcription:** Uses **Whisper large-v3** for robust and accurate speech-to-text conversion.
- **Efficient Vector Search:** Implements **FAISS** (Facebook AI Similarity Search) to index transcriptions for incredibly fast semantic retrieval.
- **Intelligent Chat & Summarization:** Powered by **Llama 3.1** using a Map-Reduce approach to handle large contexts, enabling you to effectively "chat" with your media.
- **Interactive Environment:** Built entirely as a Jupyter Notebook for easy experimentation, visualization, and execution.

## Tech Stack
- **Whisper large-v3** (Audio Transcription)
- **FAISS** (Vector Database)
- **Llama 3.1 Map-Reduce** (LLM for Summarization and Q&A)
- **Jupyter Notebook** (Development Environment)

## Getting Started

1. **Clone the repository:**
   ```bash
   git clone https://github.com/owaiskhan2501000/Enterprise-AI-Audio-Video-Analyzer.git
   cd Enterprise-AI-Audio-Video-Analyzer
   ```

2. **Open the Notebook:**
   Launch Jupyter Notebook or Jupyter Lab to open and run the provided `.ipynb` file.
   ```bash
   jupyter notebook
   ```

3. **Install Dependencies:**
   Make sure to install the required Python packages mentioned inside the notebook (e.g., `openai-whisper`, `faiss-cpu`, `langchain`, etc.) before running the cells.

## Usage
- Upload or link your long audio/video file.
- Run the pipeline to transcribe the media.
- Index the transcript using FAISS.
- Ask questions and chat with the content utilizing Llama 3.1.

## Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the issues page.
