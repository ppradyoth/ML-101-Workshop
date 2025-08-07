# ML-101-Workshop
This repo contains src code used during the ML - 101 workshop hosted by IEEE Bangalore Section as a part of ML 101

📘 StudyBuddy: Ask Your PDF Anything
🔧 Tech Stack
Frontend: Streamlit (runs in Google Colab)

Backend:

LLM API: Google Gemini Pro (generativeai)

PDF Parsing: PyMuPDF (fitz)

Embedding: sentence-transformers (MiniLM-L6-v2)

Semantic Search: FAISS (Flat Index)

Deployment Tunnel: Cloudflare (using cloudflared in Colab)

🧠 Core Functionality
1. PDF Upload & Parsing
Users upload a .pdf file (e.g., study material or notes).

Text is extracted from all pages using fitz (PyMuPDF).

2. Chunking & Embedding
Extracted text is split into overlapping chunks (300 words, 50-word overlap).

Chunks are converted into embeddings using MiniLM-L6-v2 from Sentence Transformers.

3. Semantic Indexing
FAISS builds an in-memory vector index from chunk embeddings.

Enables semantic search over the document using vector similarity.

4. LLM-Powered Q&A
User submits a query.

Top-k most relevant chunks are retrieved from FAISS.

A custom prompt is constructed with the question and context.

Google Gemini Pro is invoked with the prompt to generate an answer.

Answer is appended to chat history and shown on screen.

5. Auto Quiz Generator
Based on the uploaded document (limited to 3000 characters for prompt efficiency).

Generates 5 quiz questions with a mix of MCQs and short answers.

Gemini Pro handles the quiz generation via a carefully crafted prompt.

🖥️ Streamlit Interface
📂 PDF Upload Section

💬 Ask Questions Tab (Chat UI with query input & output history)

📝 Generate Quiz Tab (Single-click quiz generation)

✅ Status and Error Feedback

🔁 Real-time updates and history tracking

🧩 Future-Proofing
Modular architecture: easy to add support for other LLMs (OpenAI, Claude, etc.)

All processing is local (embeddings & indexing), only generation is API-based.

