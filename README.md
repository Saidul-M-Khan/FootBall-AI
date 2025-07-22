# Football AI Assistant

An intelligent AI-powered system that provides football/soccer knowledge assistance using a curated collection of professional documents and research papers.

## Overview

Football AI Assistant is a FastAPI-based application that enables:
- Document management for football/soccer related PDFs
- Intelligent Q&A based on uploaded documents
- Semantic search across the knowledge base
- Session-based conversations with context awareness
- Strict adherence to document-based responses

## Features

### Document Management
- **Staff-Only Upload**: Only staff members can upload documents
- **Categorized Storage**: Documents are organized into 8 main categories:
  1. Nutrition
  2. Strength and Conditioning
  3. Training Program Scheduling
  4. General Player Advice
  5. Injury Prevention and Management
  6. Mental Well-Being
  7. Performance Analytics Tips
  8. Tactical Development
- **Public Access**: All registered users can access the knowledge from uploaded documents
- **Document Processing**: Automatic text extraction and semantic chunking

### AI Capabilities
- **Contextual Understanding**: Uses advanced embedding models for semantic search
- **Accurate Citations**: Every response includes specific document references
- **No External Knowledge**: Responses strictly based on uploaded documents
- **Session Management**: Maintains conversation context for better responses
- **Multi-Document Analysis**: Combines knowledge from multiple relevant sources

### Technical Features
- **Vector Search**: ChromaDB for efficient semantic search
- **Embeddings**: SentenceTransformer for text embeddings
- **PDF Processing**: PyPDF2 for text extraction
- **Database**: PostgreSQL with SQLAlchemy ORM
- **API**: FastAPI with automatic OpenAPI documentation
- **Authentication**: Email-based user authentication with staff privileges

## System Architecture

### Core Components
1. **FastAPI Backend**: Handles all HTTP requests and business logic
2. **AI Assistant**: Manages document processing and response generation
3. **Vector Store**: ChromaDB for semantic search capabilities
4. **Database**: PostgreSQL for structured data storage
5. **File Storage**: Local storage for PDF documents

---

## Architecture

![System Diagram](assets/diagram.svg)

---

## API Endpoints

### Document Management
- `POST /ai/upload/`: Upload new documents (staff only)
- `GET /ai/document_list/`: List all available documents
- `DELETE /ai/delete_documents/`: Delete documents (staff only)
- `POST /ai/reprocess_chunks/`: Reprocess document chunks (staff only)

### Chat & Sessions
- `POST /ai/chat_session/`: Create new chat session
- `POST /ai/chat/`: Send message and get AI response
- `GET /ai/all_chat/`: Get all messages in a session
- `GET /ai/all_sessions/`: List all user sessions
- `GET /ai/search/`: Search through sessions

## Setup & Installation

### Prerequisites
- Python 3.8+
- PostgreSQL
- Virtual Environment

### Installation Steps

1. Clone the repository:
```bash
git clone <repository-url>
cd football-ai
```

2. Create and activate virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Set up environment variables (.env):
```env
DATABASE_URL=postgresql://user:password@localhost/dbname
OPENAI_API_KEY=your-openai-api-key
ALLOWED_ORIGINS=http://localhost:3000,http://localhost:5173
```

5. Run database migrations:
```bash
alembic upgrade head
```

6. Start the application:
```bash
uvicorn main:app --reload
```

## Usage

### Document Upload
1. Ensure you have staff privileges
2. Use the upload endpoint with PDF documents
3. Documents are automatically processed and indexed

### Asking Questions
1. Create a new chat session
2. Send your football-related query
3. Receive responses with specific document citations

### Managing Documents
- Staff users can upload new documents
- Documents are automatically categorized
- All registered users can access document knowledge
- Staff can delete or reprocess documents as needed

## Development

### Key Files
- `main.py`: Application entry point
- `app/api.py`: API endpoints and routing
- `app/ai_assistant.py`: Core AI functionality
- `app/models.py`: Database models
- `app/database.py`: Database configuration

### Adding New Features
1. Update database models if needed
2. Create new migrations using Alembic
3. Add new endpoints in api.py
4. Update AI assistant functionality as required

## Maintenance

### Database Management
- Regular backups recommended
- Monitor database size and performance
- Use provided cleanup tools for orphaned data

### Vector Store Management
- Monitor ChromaDB performance
- Use reprocessing endpoint if needed
- Regular consistency checks recommended

## Troubleshooting

### Common Issues
1. **Upload Failures**: Check file size and format
2. **Processing Errors**: Verify PDF readability
3. **Search Issues**: Ensure ChromaDB is functioning
4. **Authentication Errors**: Verify user permissions

### Error Logs
- Application logs in standard output
- Database errors in PostgreSQL logs
- ChromaDB errors in vector store logs

## Contact

saidulmursalinkhan@gmail.com

## Acknowledgments

- OpenAI for GPT models
- ChromaDB for vector search
- SentenceTransformers for embeddings
- FastAPI team for the web framework