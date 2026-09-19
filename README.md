# 🤖 AI-Powered RAG Customer Support System
An end-to-end **Retrieval-Augmented Generation (RAG)** system built with **n8n** that automates customer support using a company's own knowledge base.

The project consists of two connected workflows:

1. **Knowledge Base Ingestion** — processes PDF/DOCX documents from Google Drive and stores their embeddings in Qdrant.
2. **AI Customer Support** — receives customer emails, retrieves relevant knowledge, generates grounded responses, and automatically replies through Gmail.

## 📸 Workflow Output

The following output shows the system in action, including the **AI-generated customer response and Google Sheets conversation logging**.

![Workflow Output](https://raw.githubusercontent.com/Waariha-Asim/AI-Powered-RAG-Customer-Support-System/main/Workflow_Output.png)

## ✨ Key Features

📚 Automated PDF & DOCX knowledge-base ingestion
🔍 Document extraction and text chunking
🧠 Google Gemini embeddings
🗄️ Qdrant vector database for semantic retrieval
🤖 AI-powered customer support agent
📩 Automated Gmail customer replies
🔄 Conversation memory using email thread IDs
📊 Customer conversation logging in Google Sheets
⚠️ Unsupported-file and workflow error logging
🛡️ Grounded responses based on retrieved knowledge
⏱️ Scheduled knowledge-base processing

## 🏗️ Architecture

### 📚 Workflow 1 — Knowledge Base Ingestion

```text
Google Drive
     ↓
Download Documents
     ↓
File Type Detection
     ↓
PDF / DOCX Extraction
     ↓
Document Metadata
     ↓
Text Chunking
     ↓
Google Gemini Embeddings
     ↓
Qdrant Vector Database
```

The workflow runs on a schedule, retrieves documents from Google Drive, accepts only **PDF and DOCX** files, extracts their content, splits the content into chunks, generates embeddings, and stores them in the `customer-support` Qdrant collection.

Unsupported files and processing errors are logged in Google Sheets.

### 🤖 Workflow 2 — AI Customer Support

```text
Incoming Gmail
     ↓
Email Normalization
     ↓
AI Customer Support Agent
     ↓
Qdrant Knowledge Base
     ↓
Relevant Information Retrieval
     ↓
Grounded AI Response
     ↓
Automatic Gmail Reply
     ↓
Conversation Logging
```

The AI agent uses the Qdrant knowledge base as its source of truth and is instructed not to fabricate information when the required information is unavailable.

## 🧠 RAG Pipeline

**Ingestion → Chunking → Embeddings → Vector Storage → Retrieval → Generation**

When a customer asks a question, the system retrieves relevant document chunks from Qdrant and provides them to the AI agent before generating the response.

## 🛠️ Tech Stack

**n8n • Google Drive • Google Gemini • Qdrant • Groq • Gmail • Google Sheets • RAG • AI Agents • Vector Embeddings**

## 📁 Project Structure

```text
AI-Powered-RAG-Customer-Support-System/
│
├── Workflow.json
├── Workflow_Output.png
└── README.md
```

## ⚙️ Setup

### 1. Import the Workflow

Import `Workflow.json` into your n8n instance.

### 2. Configure Credentials

Connect your own:

* Google Drive
* Gmail
* Google Gemini
* Qdrant
* Groq
* Google Sheets

### 3. Configure IDs

Update the required Google Drive folder ID, Google Sheets IDs, and Qdrant collection according to your environment.

### 4. Replace Credentials

> ⚠️ **Important:** Replace all placeholder credentials, IDs, and configuration values in `Workflow.json` with your own n8n credentials before running the workflows.

### 5. Prepare the Knowledge Base

Place supported **PDF or DOCX** customer-support documents inside the configured Google Drive folder.

### 6. Run & Test

Run the ingestion workflow first to populate Qdrant. Then send a customer question to the connected Gmail account to test the automated support workflow.

## 🔐 AI Grounding

The AI agent is configured to:

* Use retrieved knowledge as its source of information.
* Avoid fabricating answers.
* Clearly state when information is unavailable.
* Keep responses concise and professional.
* Mention source documents when relevant.

## 🎯 Use Cases

* Returns & refunds
* Shipping policies
* Orders
* Payments
* Account-related questions
* Product information
* Company FAQs
* Internal documentation

---

### 👩‍💻 Author

**Waariha Asim**

AI Engineer | Generative AI | RAG | AI Automation
