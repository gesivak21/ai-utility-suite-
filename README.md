# AI Utility Dashboard

## Overview
The **AI Utility Dashboard** is a full-stack AI-powered productivity application built with **Streamlit (frontend)** and **FastAPI (backend)**. It provides authenticated users with tools for:

- 🎙️ Meeting transcription, summarization, and actionable insights
- 📄 Single and bulk document summarization
- 📖 Document-based Question & Answering (RAG)

The application is designed with secure authentication, scalable backend services, and cloud-ready configuration.

---

## 🌐 Live Application

The application is deployed on GCP Cloud Run and can be accessed here:

👉 https://ai-utility-suite-754273589848.us-central1.run.app/

---

## 🎥 Demo Preview <p align="center"> 
<img src="https://github.com/gesivak21/meeting-summarizer-ai/blob/master/demo.gif" width="500" alt="Meeting Summarizer Demo">
</p> 🎯 *Watch how the app converts a audio/video meeting into a transcript, summary, and actionable insights — all in one click!*

👉 **[🎬 View Full Demo](https://gesivak21.github.io/MyPortfolio/projects/meeting-summarizer-demo.html)**

---

## 🧩 Tech Stack

| Component                        | Description                                    |
| -------------------------------- | ---------------------------------------------- |
| **Python 3.9+**                  | Core language                                  |
| **Streamlit**                    | Interactive web UI                             |
| **yt-dlp / ffmpeg**              | YouTube video and audio processing             |
| **Whisper / Speech-to-Text API** | Transcription engine                           |
| **LLM (e.g., GPT-4)**            | Summarization and insight extraction           |
| **Assembly AI**                  | URL based transcriptions                       |

---

## High-Level Architecture

```
┌─────────────┐        ┌──────────────┐
│  Frontend   │  HTTP  │   Backend    |
│  Streamlit  |──────>>|   Fastapi    |
└─────────────┘        └──────────────┘
                              │
                              ├── Firebase (Auth, Users, Subscriptions)
                              ├── OpenAI / LLM APIs
                              ├── AssemblyAI (Transcription)
                              ├── FAISS (Vector Store)
                              └── Redis (API key & JWT caching)
```

---

## Features

### Authentication & Security
- Google OAuth 2.0 login
- Backend-issued JWT tokens
- API key validation and rate limiting
- Secure credential storage (Firebase + KMS)

### Meeting Summarizer
- Upload audio/video files **or** paste cloud recording URLs
- Multi-language transcription support
- AI-generated summaries and actionable insights
- Usage tracking by minutes and plan limits
- Export results as TXT or PDF

### Document Summarizer
- Single and bulk PDF summarization (1–5 files)
- Page-aware summarization
- Export combined summaries as TXT or PDF

### Document Q&A (RAG)
- Upload 1–3 PDFs
- FAISS-based vector search
- Strict vs Flexible answer modes
- Source citations with page numbers

### Subscription & Billing
- Plan-based access control
- Usage limits enforced server-side
- Firebase-backed subscription management

---

## Project Structure

```
|── Summarizer/
|
├── frontend/
│   ├── app.py                     # Main dashboard entry point
│   ├── pages/                     # Streamlit multi-page UI
│   │   ├── 1_login.py
│   │   ├── 2_payment.py
│   │   ├── 3_meeting_summarizer.py
│   │   ├── 4_document_summarizer.py
│   │   ├── 5_document_qa.py
│   │   ├── 6_help.py
│   │   └── 7_settings.py
│   ├── helper/                    # Frontend helpers
│   │   ├── login_utils/
│   │   └── meeting_summarizer_utils/
│   ├── export_utils.py
│   ├── .streamlit/config.toml
│   └── .env
│
├── backend/
│   ├── main.py                    # FastAPI entry point
│   ├── auth_utils/                # Auth, JWT, API keys
│   ├── document_summarizer/       # Document summarization logic
│   ├── document_qa/               # RAG pipeline (FAISS)
│   ├── meeting_summarize_ai_utils/# Transcription & meeting AI
│   ├── firebase_utils/            # Firebase integration
│   ├── requirements.txt
│   └── .env
└── README.md
```

---

## Environment Variables

### Frontend (`frontend/.env`)

```
BACKEND_URL=https://<your-backend-url>
GOOGLE_CLIENT_ID=...
GOOGLE_CLIENT_SECRET=...
GOOGLE_REDIRECT_URI=...
```

### Backend (`backend/.env`)

```
OPENAI_API_KEY=...
ASSEMBLYAI_API_KEY=...
FIREBASE_PROJECT_ID=...
REDIS_URL=...
JWT_SECRET=...
```
---

## Local Development

### Backend

```bash
cd backend
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
uvicorn main:app --host 0.0.0.0 --port 8000
```

### Frontend

```bash
cd frontend
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
streamlit run app.py
```

---

## License

This project is proprietary. Redistribution or commercial use requires explicit authorization from the owner.

---

## 👩‍💻 Author

**G. Siva Kumar** | 📧 [gesivak21@example.com](mailto:gesivak21@gmail.com) | 🌐 [GitHub](https://github.com/gesivak21/Portfolio)

