

Objective
Simulate customer support interactions using AI for FAQs and escalation scenarios.

Scope of Work

Input: FAQs dataset & customer queries
Contextual memory to retain previous conversation
Escalation simulation when query not answered
Optional frontend chat interface

Technical Expectations

Backend API with REST endpoints
LLM integration for response generation
Database for session tracking

LLM Usage Guidance

Generate responses
Summarize conversations
Suggest next actions

Features

RAG Pipeline: Loads FAQs from faqs.json, embeds with SentenceTransformer, stores in Chroma vector DB, retrieves relevant chunks for Gemini LLM responses.
Context-Aware: Conversation history from MongoDB is injected into prompts for follow-ups (e.g., "tell me more about this" references prior topics).
Escalation Handling: Low similarity scores trigger human handover simulation (log/email).
Simple UI: EJS-based chat interface with real-time messaging via Fetch API.
Modular Backend: Separated into models, helpers (session/history/RAG), routes for easy maintenance.

Tech Stack

Backend: Node.js/Express (API), Mongoose (MongoDB ODM)
AI/ML: Python/LangChain (RAG chain), SentenceTransformer (embeddings), Chroma (vectorstore), Google Gemini (LLM)
Database: MongoDB Atlas (cloud sessions)
Frontend: EJS templates, vanilla JS
Deployment Ready: Dockerizable; tested on localhost.

Prerequisites

Node.js ≥18
Python ≥3.10 (with venv)
MongoDB Atlas account (free tier)
Google AI Studio API key (for Gemini)

Installation

1. Clone the Repo
git clone https://github.com/yourusername/ai-customer-support-bot.git
cd ai-customer-support-bot

2. Set Up Python (RAG Core)
From project root:
python -m venv venv
# Windows: venv\Scripts\activate
# macOS/Linux: source venv/bin/activate
pip install -r requirements.txt  # Includes langchain, chromadb, sentence-transformers, etc.

Add to root .env: GOOGLE_API_KEY=your-gemini-api-key
Run notebook: jupyter notebook rag.ipynb → Execute all cells to persist ./chroma_db.
Test RAG: echo '{"query": "What is delivery modes?"}' | python rag_query.py


