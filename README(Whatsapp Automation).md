This n8n workflow turns WhatsApp into an AI-powered support ticket system.

It:

Receives WhatsApp messages via webhook

Classifies and generates solutions using an LLM

Stores tickets in Google Sheets

Generates unique Ticket IDs

Allows users to check ticket status using /status <ticketId>

Responds in proper Twilio-compatible XML format

This is not a chatbot. It’s a structured support automation system.

🧠 Architecture Flow:-
1️⃣ New Support Ticket Flow:

Webhook (Twilio WhatsApp)

Check if message starts with /status

If NOT → Treat as new issue

Send issue to LLM (OpenRouter GPT-3.5)

Force structured JSON output:

{
  "category": "...",
  "steps": "1)...\n2)...",
  "status": "..."
}


Generate 6-digit ticket ID

Append to Google Sheets

Respond back with:

Ticket ID

Category

Steps

Status

2️⃣ Ticket Status Check Flow:-

If user sends:

/status 123456

Flow:

Extract ticket ID

Lookup in Google Sheets

Send data to LLM for structured resolution response

Return formatted reply

📊 Google Sheets Structure:-

Your sheet must contain these columns:

Time	User	Issue	Category	AI Solution	Status	Ticket Id

If you change column names, the workflow will break.

🔧 Requirements:

n8n (v1+ recommended)

Twilio WhatsApp Sandbox

OpenRouter API key

Google Sheets OAuth credentials

Public webhook URL (ngrok / cloud hosted n8n)

⚙️ Key Design Decisions:

LLM forced to return JSON only (prevents parsing failures)

Code node parses JSON safely

Ticket ID generated via JS

XML response formatted for Twilio compatibility

Status lookup separated via conditional IF node

⚠️ Limitations:-

No authentication (anyone can query ticket ID)

No duplicate issue detection

No rate limiting

Google Sheets not scalable for high-volume production

Random ticket ID (possible collision at scale)

If you want production-grade: move to DB + UUID + auth.

💡 Possible Improvements:-

Add memory context

Add user identification via phone number

Add SLA tracking

Add priority classification

Add vector database for better solution recall

Move storage to PostgreSQL
