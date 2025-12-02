# 🤖 Multi-Agent AI Personal Assistant

A professional, multi-agent AI personal assistant built with Streamlit, featuring specialized agents for different tasks, persistent memory, and task management.

## ✨ Features

- **🤖 7 Specialized Agents**: Each agent handles specific types of requests
- **💬 Chat Agent**: Natural conversations and general questions
- **✅ Productivity Agent**: Task management, reminders, and scheduling
- **🎨 Creative Agent**: Content generation (poems, stories, summaries) + AI image generation
- **🧠 Memory Agent**: Remembers your preferences and context
- **🔍 Researcher Agent**: Live web search powered by Serper API
- **📚 Knowledge Base Agent**: RAG-based document Q&A (upload PDFs and ask questions)
- **🎯 Orchestrator**: Intelligently routes messages to the right agent
- **💾 Persistent Storage**: PostgreSQL/SQLite database for users, tasks, conversations, and memories
- **🔐 Secure Authentication**: Password-protected user accounts with session persistence
- **📊 LangSmith Tracking**: Complete observability and debugging
- **🎤 Voice Features**: FREE speech-to-text (local Whisper) + optional TTS
- **🔄 Multi-Provider LLM**: Primary Groq + Cerebras fallback for high availability

## 🎯 Agent Overview

### 1. Chat Agent 💬
**Purpose**: Handle casual conversations and general questions

**Use Cases**:
- Greetings and small talk
- General knowledge questions
- Friendly conversations
- Getting to know you

**Example**:
```
You: Hi! How are you today?
Agent: Hello! I'm doing great, thanks for asking! How can I help you today?
```

### 2. Productivity Agent ✅
**Purpose**: Manage tasks, reminders, and productivity

**Use Cases**:
- Creating tasks from natural language
- Viewing pending tasks
- Task prioritization
- Setting deadlines
- Productivity advice

**Examples**:
```
You: Remind me to finish the project report by Friday, high priority
Agent: ✅ Task created: finish the project report
       Priority: HIGH
       Due: 2024-11-29
       I've added this to your task list!

You: What are my pending tasks?
Agent: 📋 You have 3 pending tasks:
       1. 🔴 finish the project report (Due: 2024-11-29)
       2. 🟡 Review code changes
       3. 🟢 Update documentation
```

### 3. Creative Agent 🎨
**Purpose**: Generate creative content and ideas + AI images

**Use Cases**:
- Writing poems and stories
- Generating summaries
- Brainstorming ideas
- Creative writing assistance
- Content suggestions
- **AI Image Generation** (local SDXL or free APIs)

**Examples**:
```
You: Write me a haiku about AI
Agent: Silicon minds think
       Patterns emerge from the code
       Intelligence blooms

You: Summarize the key points from our last conversation
Agent: Here's a summary of our discussion:
       - We talked about your project deadline
       - You mentioned needing help with documentation
       - We discussed task prioritization strategies

You: Create an image of a sunset over mountains
Agent: [Generates and displays an AI image using local SDXL or Pollinations.ai]
```

### 4. Memory Agent 🧠
**Purpose**: Store and retrieve user context and preferences

**Use Cases**:
- Remembering user preferences
- Storing important information
- Retrieving past context
- Building user profile

**Examples**:
```
You: What do you remember about me?
Agent: Here's what I remember about you:
       - communication_style: friendly and casual
       - interests: AI and technology
       - current_project: multi-agent assistant
       - preferred_priority: high for work tasks
```

### 5. Researcher Agent 🔍
**Purpose**: Live web search for current information

**Use Cases**:
- Searching for current events
- Finding latest information
- Fact-checking
- Research with citations

**Examples**:
```
You: What's the latest news about AI developments?
Agent: Based on recent web search:
       
       1. **Microsoft announces new AI features**
          Major tech companies are integrating AI into productivity tools...
          Source: https://example.com/news
          
       2. **OpenAI releases updated model**
          Recent improvements in language understanding...
          Source: https://example.com/tech
```

### 6. Knowledge Base Agent 📚
**Purpose**: Query uploaded documents using RAG (Retrieval Augmented Generation)

**Use Cases**:
- Upload PDFs and ask questions
- Extract information from documents
- Document-based Q&A
- Research paper analysis

**Examples**:
```
You: [Upload a PDF about machine learning]
Agent: ✅ Successfully ingested document (42 chunks)

You: What does the document say about neural networks?
Agent: Based on your document:
       
       > "Neural networks are computational models inspired by 
       > biological neurons that can learn from data..."
       
       The document explains that neural networks consist of 
       interconnected layers that process information hierarchically.
```

### 7. Orchestrator 🎯
**Purpose**: Route messages to the appropriate agent(s)

**How it works**:
1. Analyzes your message
2. Determines which agent is best suited
3. Routes to primary agent
4. Optionally involves secondary agents
5. Automatically extracts memories

**Routing Logic**:
- Uses LLM-based decision making
- Falls back to keyword matching
- Considers user context and history

## 🚀 Quick Start

### Prerequisites
- Python 3.11+ or Conda
- Free API keys:
  - [Groq API](https://console.groq.com) - For LLM inference (required)
  - [LangSmith](https://smith.langchain.com) - For tracking (required)
  - [Cerebras API](https://cerebras.ai) - Fallback LLM provider (optional but recommended)
  - [Serper API](https://serper.dev) - For web search in Researcher Agent (optional)
  - [OpenAI API](https://platform.openai.com) - Optional, only for voice OUTPUT (TTS)

**Note**: Voice INPUT (speech-to-text) is FREE using local Whisper - no API key needed!

### Installation

#### Option 1: Using Conda (Recommended)
```bash
# Clone or navigate to the project
cd AgenticAssistant

# Create environment
conda env create -f environment.yml

# Activate environment
conda activate ai-assistant
```

#### Option 2: Using pip
```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Configuration

1. **Copy the example environment file**:
```bash
cp .env.example .env
```

2. **Edit `.env` and add your API keys**:
```bash
# Required
GROQ_API_KEY=gsk_your_groq_api_key_here
LANGSMITH_API_KEY=lsv2_pt_your_langsmith_key_here

# Optional but recommended (for fallback and enhanced features)
CEREBRAS_API_KEY=your_cerebras_key_here  # Fallback LLM provider
SERPER_API_KEY=your_serper_key_here      # For web search
OPENAI_API_KEY=sk_your_openai_key_here   # For voice output only
```

3. **Get your free API keys**:
   - **Groq**: https://console.groq.com → Create API Key
   - **LangSmith**: https://smith.langchain.com → Settings → API Keys
   - **Cerebras** (optional): https://cerebras.ai → Sign up for free tier
   - **Serper** (optional): https://serper.dev → Get API key (free tier: 2,500 searches)
   - **OpenAI** (optional): https://platform.openai.com → Only for TTS voice output

### Run the Application

```bash
streamlit run app.py
```

The app will open at `http://localhost:8501`

## 📖 Usage Guide

### First Time Setup

1. **Register an Account**:
   - Click the "Register" tab
   - Choose a username and password (min 6 characters)
   - Click "Create Account"

2. **Login**:
   - Enter your username and password
   - Click "Login"
   - Your credentials are stored securely in the database

### Using the Chat Interface

The chat interface automatically routes your messages to the right agent:

**For Tasks**:
```
"Create a task to review the code by tomorrow"
"Remind me to call John at 3pm"
"What are my pending tasks?"
```

**For Creative Content & Images**:
```
"Write a poem about nature"
"Summarize our conversation"
"Give me 5 ideas for a blog post"
"Create an image of a futuristic city"
"Draw a picture of a cat wearing a hat"
```

**For Web Research**:
```
"What's the latest news about SpaceX?"
"Search for recent AI breakthroughs"
"Find information about climate change policies"
```

**For Document Q&A**:
```
"Upload a PDF and ask questions"
[After uploading]: "What are the key findings in this paper?"
[After uploading]: "Summarize the introduction section"
```

**For General Chat**:
```
"Hi! How are you?"
"What's the weather like?"
"Tell me a joke"
```

**For Memory**:
```
"Remember that I prefer morning meetings"
"What do you know about my preferences?"
```

### Using the Task Dashboard

1. **Create Tasks**:
   - Click "➕ Create New Task"
   - Fill in title, description, priority, and due date
   - Click "Create Task"

2. **Manage Tasks**:
   - Filter by status or priority
   - Click "Start" to begin a task
   - Click "Done" to complete a task
   - Click "🗑️" to delete a task

3. **View Tasks**:
   - See all your tasks with color-coded priorities
   - 🔴 High priority
   - 🟡 Medium priority
   - 🟢 Low priority

## 🏗️ Architecture

### Project Structure
```
AgenticAssistant/
├── app.py                      # Main Streamlit application
├── config.py                   # Configuration management
├── agents/                     # Agent implementations
│   ├── base_agent.py          # Base class for all agents
│   ├── chat_agent.py          # Casual conversation
│   ├── productivity_agent.py  # Task management
│   ├── creative_agent.py      # Content + image generation
│   ├── memory_agent.py        # User context management
│   ├── researcher_agent.py    # Live web search (Serper API)
│   ├── knowledge_agent.py     # RAG-based document Q&A
│   └── orchestrator.py        # Agent coordination
├── llm/                       # LLM integration
│   ├── llm_client.py          # Groq + Cerebras clients
│   └── prompts.py             # System prompts
├── database/                  # Data persistence
│   ├── models.py              # Database schema
│   └── db_manager.py          # CRUD operations
├── utils/                     # Utilities
│   ├── langsmith_tracker.py   # LangSmith integration
│   └── voice_utils.py         # Voice I/O
├── models/                    # Downloaded AI models (SDXL, etc.)
└── data/                      # SQLite database (if using local)
    └── assistant.db
```

### Database Schema

**Supports both SQLite (local) and PostgreSQL (cloud/production)**

**Users Table**:
- `user_id`: Primary key
- `username`: Unique username
- `password_hash`: SHA-256 hashed password
- `created_at`: Account creation timestamp
- `preferences`: JSON preferences

**Tasks Table**:
- `task_id`: Primary key
- `user_id`: Foreign key to users
- `title`: Task title
- `description`: Optional details
- `priority`: low, medium, high
- `status`: pending, in_progress, completed, cancelled
- `due_date`: Optional deadline
- `created_at`: Creation timestamp

**Conversations Table**:
- `conversation_id`: Primary key
- `user_id`: Foreign key to users
- `agent_type`: Which agent handled it
- `message`: User message
- `response`: Agent response
- `timestamp`: When it occurred

**Memory Table**:
- `memory_id`: Primary key
- `user_id`: Foreign key to users
- `key`: Memory key (e.g., "preferred_time")
- `value`: Memory value
- `context`: Additional context
- `created_at`: When stored

## 🎤 Voice Features

### Voice Input (Speech-to-Text) - FREE! 🎉

Uses local Whisper model via Hugging Face - no API key needed!

```env
ENABLE_VOICE_INPUT=true  # FREE - uses local Whisper
```

First run will download the Whisper model (~150MB). Works on CPU or GPU.

### Voice Output (Text-to-Speech) - Requires OpenAI API

```env
OPENAI_API_KEY=your_openai_key
ENABLE_VOICE_OUTPUT=true  # Requires OpenAI API credits
```

**Summary**: 
- ✅ Voice INPUT is completely FREE (local Whisper)
- 💰 Voice OUTPUT requires OpenAI API key (paid)


## 🔧 Configuration Options

Edit `.env` to customize:

```bash
# Required API Keys
GROQ_API_KEY=your_groq_key_here
LANGSMITH_API_KEY=your_langsmith_key_here

# Optional API Keys
CEREBRAS_API_KEY=your_cerebras_key_here  # Fallback LLM provider
SERPER_API_KEY=your_serper_key_here      # Web search capability
OPENAI_API_KEY=your_openai_key_here      # Voice output (TTS) only

# LLM Settings
DEFAULT_MODEL=llama-3.3-70b-versatile  # Groq model to use
TEMPERATURE=0.7                         # 0.0-1.0 (higher = more creative)
MAX_TOKENS=2048                         # Maximum response length

# Database (choose one)
DATABASE_PATH=data/assistant.db                    # Local SQLite
# OR
DATABASE_PATH=postgresql://user:password@host:5432/dbname  # PostgreSQL

# Voice Features
ENABLE_VOICE_INPUT=true   # FREE - local Whisper
ENABLE_VOICE_OUTPUT=false # Requires OpenAI API

# LangSmith Tracking
LANGSMITH_PROJECT=multi-agent-assistant
LANGSMITH_TRACING=true
```

### Available Features by Configuration:

| Feature | Required API Keys | Notes |
|---------|------------------|-------|
| **Chat Agent** | GROQ_API_KEY, LANGSMITH_API_KEY | Core functionality |
| **Productivity Agent** | GROQ_API_KEY, LANGSMITH_API_KEY | Task management |
| **Creative Agent** | GROQ_API_KEY, LANGSMITH_API_KEY | Poems, stories, summaries |
| **Image Generation** | None (uses free APIs) | Local SDXL or Pollinations.ai |
| **Memory Agent** | GROQ_API_KEY, LANGSMITH_API_KEY | Context storage |
| **Researcher Agent** | + SERPER_API_KEY | Web search with citations |
| **Knowledge Base** | None extra | RAG-based PDF Q&A |
| **Voice Input (STT)** | None | Free local Whisper |
| **Voice Output (TTS)** | + OPENAI_API_KEY | OpenAI TTS |
| **LLM Fallback** | + CEREBRAS_API_KEY | Automatic failover |

