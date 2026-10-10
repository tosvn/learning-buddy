# Learning Buddy 🎓

**An AI-Powered Academic Assistant for Undergraduate Students**

Learning Buddy is an AI-powered academic assistant built to help undergraduate students improve their learning experience. It uses Python, Flask, and the Groq API to answer academic questions, explain complex concepts, and assist students with reviewing and understanding uploaded documents.

## Features

- **AI Academic Assistance:** Get explanations and answers to academic questions across different university courses and disciplines.
- **Document Upload:** Upload PDF and Microsoft Word (`.docx`) documents for text extraction and academic support.
- **Document-Based Learning:** Ask questions about uploaded documents using their extracted text as conversation context.
- **Conversation History:** Stores chat messages in JSON files associated with individual user sessions.
- **Academic-Focused Responses:** Uses a system prompt to guide the AI toward educational and study-related requests.
- **REST API:** Provides Flask endpoints for chat interactions and document uploads.

## Technologies Used

- Python
- Flask
- Groq API
- OpenAI GPT-OSS 20B model, accessed through Groq
- PyPDF2
- python-docx
- Werkzeug
- JSON
- HTML, CSS, and JavaScript for the frontend, where applicable

## Project Structure

```text
Learning-Buddy/
├── app.py
├── templates/
│   └── index.html
├── uploads/
├── histories/
├── requirements.txt
├── .gitignore
└── README.md
```

- `app.py` — Main Flask application, API routes, AI integration, document processing, and conversation management.
- `templates/` — Contains the HTML templates.
- `uploads/` — Configured directory for uploaded files; the current implementation processes files in memory.
- `histories/` — Stores conversation histories as JSON files.
- `requirements.txt` — Lists the Python dependencies.
- `.gitignore` — Specifies files and directories excluded from Git.

## Getting Started

### Prerequisites

- Python 3.10 or later
- pip
- A Groq API key

### Installation

1. Clone the repository:

   ```bash
   git clone <your-repository-url>
   cd Learning-Buddy
   ```

2. Create and activate a virtual environment:

   ```bash
   python -m venv venv
   ```

   On Windows:

   ```bash
   venv\Scripts\activate
   ```

   On macOS or Linux:

   ```bash
   source venv/bin/activate
   ```

3. Install the dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Configure your Groq API key as an environment variable named `GROQ_API_KEY`.

   Alternatively, if the application is configured to load a `.env` file using `python-dotenv`, create a `.env` file in the project root:

   ```env
   GROQ_API_KEY=your_groq_api_key
   SECRET_KEY=your_random_secret_key
   ```

   Never commit API keys or other secrets to GitHub.

5. Start the application:

   ```bash
   python app.py
   ```

6. Open your browser and visit:

   `http://127.0.0.1:5000`

## API Endpoints

### Home Page

**GET `/`**

Renders the application's main interface and initializes a session when necessary.

### Chat

**POST `/chat`**

Accepts a student's message, sends the conversation history to the Groq API, saves the response, and returns the AI-generated answer.

Example request:

```json
{
  "message": "Explain the difference between RAM and ROM."
}
```

Example response:

```json
{
  "reply": "RAM is volatile memory, while ROM is non-volatile memory..."
}
```

### Document Upload

**POST `/upload`**

Accepts PDF and DOCX files using `multipart/form-data`, extracts their text, and adds up to the first 3,000 characters to the conversation history.

The file must be submitted using the form field named `file`.

**Note:** The upload endpoint stores the extracted document content in the conversation history but does not call the AI directly. Students can ask questions about the uploaded content through the chat endpoint afterward.

## How It Works

1. A student opens the Learning Buddy web interface.
2. The Flask backend creates or retrieves the user's session.
3. The student submits an academic question or uploads a document.
4. The backend processes the request and retrieves the relevant conversation history.
5. For chat requests, the conversation and system prompt are sent to the Groq-hosted AI model.
6. For document uploads, text is extracted using PyPDF2 or python-docx.
7. Chat messages and AI responses are saved in JSON files.
8. The backend returns a response to the frontend.


## Project Objective

Learning Buddy aims to make academic support more accessible to undergraduate students by combining conversational AI with document processing. The project demonstrates the practical use of Python, Flask, API integration, file handling, and AI-assisted learning.

## Author

**Mudasiru Abdulsalam Oluwatosin**



