🎬 YouTube AI Transcript Assistant 🔍🤖
A Chrome Extension + AI Backend that allows users to ask questions about any YouTube video. It fetches the video's transcript, chunks it, embeds it with SentenceTransformers, stores it in FAISS, and uses Gemini AI to answer questions contextually.

🚀 Ask anything about the video — no need to scrub through the timeline!


📹 Demo

https://github.com/user-attachments/assets/8f6621a0-be92-4e76-be57-30b08d07680f


🧠 Tech Stack

🧩 Frontend: Chrome Extension (HTML, JS, CSS)
⚙️ Backend: FastAPI
📼 Transcript Fetching: yt-dlp, .vtt conversion
🧠 Embeddings: sentence-transformers
🔎 Vector Store: FAISS
🧠 LLM: langchain-google-genai using Gemini


🛠️ Features

🌐 Chrome Extension to interact with any YouTube video
📄 Automatic transcript download + parsing
🔍 Vector-based semantic search using FAISS
🧠 Context-aware AI answers via Gemini API
🪄 Seamless integration between frontend & backend
⚡ Real-time processing with loading states
🎨 Modern glassmorphism UI design
📱 Responsive extension popup interface


📁 Project Structure
yt-ai-extension/
│
├── extension/                 # Chrome Extension
│   ├── manifest.json
│   ├── popup.html
│   ├── popup.js
│   ├── styles.css
│   └── icon.png
│
├── backend/                   # FastAPI backend
│   ├── main.py
│   ├── transcript_utils.py
│   ├── vector_utils.py
│   ├── requirements.txt
│   └── .env                   # contains GOOGLE_API_KEY
│
├── README.md
└── LICENSE

🚀 Running the Project
🔧 1. Backend Setup
bashcd backend
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
uvicorn main:app --reload
Make sure .env contains:
envGOOGLE_API_KEY=your_google_gemini_api_key
🌐 2. Chrome Extension Setup

Open chrome://extensions/
Enable Developer mode
Click Load unpacked
Select the extension/ folder
Click the extension icon on YouTube, ask a question!


📋 Installation Requirements
Backend Dependencies (requirements.txt)
txtfastapi==0.104.1
uvicorn==0.24.0
langchain-google-genai==1.0.10
sentence-transformers==2.2.2
faiss-cpu==1.7.4
yt-dlp==2023.11.16
python-dotenv==1.0.0
pydantic==2.5.0
System Requirements

Python 3.8+
Chrome Browser
FFmpeg (for yt-dlp)


🔑 API Setup
Get Google Gemini API Key

Go to Google AI Studio
Create a new API key
Add to .env file in backend folder


🎯 Usage

Navigate to any YouTube video
Click the extension icon in your browser
Type your question about the video content
Get AI-powered answers based on the transcript!

Example Questions:

"What are the main points discussed?"
"Summarize the video in 3 bullet points"
"What does the speaker say about [specific topic]?"
"At what timestamp is [specific topic] mentioned?"


🏗️ Architecture Overview
mermaidgraph TB
    A[YouTube Video] --> B[Chrome Extension]
    B --> C[FastAPI Backend]
    C --> D[yt-dlp Transcript Fetcher]
    D --> E[Text Chunking]
    E --> F[SentenceTransformers Embedding]
    F --> G[FAISS Vector Store]
    G --> H[Semantic Search]
    H --> I[Gemini AI Processing]
    I --> B
    B --> J[User Interface]

🔧 Configuration
Extension Manifest (manifest.json)
json{
  "manifest_version": 3,
  "name": "YouTube AI Assistant",
  "version": "1.0",
  "description": "Ask AI questions about YouTube videos",
  "permissions": ["activeTab", "storage"],
  "action": {
    "default_popup": "popup.html",
    "default_title": "YouTube AI Assistant"
  },
  "host_permissions": ["https://*.youtube.com/*"],
  "icons": {
    "16": "icon.png",
    "48": "icon.png",
    "128": "icon.png"
  }
}
Backend Configuration

Host: localhost:8000 (development)
CORS: Enabled for extension origin
Rate Limiting: Optional (implement as needed)
