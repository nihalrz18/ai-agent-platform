# 🆓 Free AI Models Setup Guide

This guide shows you how to add FREE alternatives to OpenAI.

## ⭐ Recommended: Groq (Fastest & Completely Free)

### Step 1: Get Groq API Key
1. Go to: https://console.groq.com/keys
2. Sign up (free, no credit card required)
3. Click "Create API Key"
4. Copy the key

### Step 2: Install Groq
```powershell
cd "c:\Users\RazaNiha\OneDrive - Unisys\Desktop\LLM + Agentic AI Projects\LLM Project\fastapi-langgraph-agent-production-ready-template"
& ".\.venv\Scripts\python.exe" -m pip install langchain-groq
```

### Step 3: Update `.env.development`
Add this line:
```bash
GROQ_API_KEY="gsk_your_groq_api_key_here"
```

### Step 4: Update `app/core/config.py`
Add after line with `OPENAI_API_KEY`:
```python
GROQ_API_KEY: str = Field(default="", description="Groq API Key")
```

### Step 5: Update `app/services/llm.py`
Add at the top (after `from langchain_openai import ChatOpenAI`):
```python
from langchain_groq import ChatGroq
```

Then in the `LLMS` list, add these FREE models:
```python
{
    "name": "llama-3.1-70b-versatile",
    "llm": ChatGroq(
        model="llama-3.1-70b-versatile",
        api_key=settings.GROQ_API_KEY,
        temperature=settings.DEFAULT_LLM_TEMPERATURE,
        max_tokens=settings.MAX_TOKENS,
    ),
},
{
    "name": "mixtral-8x7b-32768",
    "llm": ChatGroq(
        model="mixtral-8x7b-32768",
        api_key=settings.GROQ_API_KEY,
        temperature=settings.DEFAULT_LLM_TEMPERATURE,
        max_tokens=settings.MAX_TOKENS,
    ),
},
{
    "name": "gemma-7b-it",
    "llm": ChatGroq(
        model="gemma-7b-it",
        api_key=settings.GROQ_API_KEY,
        temperature=settings.DEFAULT_LLM_TEMPERATURE,
        max_tokens=settings.MAX_TOKENS,
    ),
},
```

### Step 6: Update `.env.development`
Change the default model:
```bash
DEFAULT_LLM_MODEL=llama-3.1-70b-versatile
```

### Step 7: Restart the application
Stop the current server (Ctrl+C) and restart:
```powershell
& "c:\Users\RazaNiha\OneDrive - Unisys\Desktop\LLM + Agentic AI Projects\LLM Project\fastapi-langgraph-agent-production-ready-template\.venv\Scripts\python.exe" -m uvicorn app.main:app --reload --port 8000
```

---

## 🌟 Alternative: Google Gemini (Also Free & High Quality)

### Step 1: Get Google API Key
1. Go to: https://aistudio.google.com/app/apikey
2. Sign in with Google account
3. Click "Create API Key"
4. Copy the key

### Step 2: Install Gemini
```powershell
& ".\.venv\Scripts\python.exe" -m pip install langchain-google-genai
```

### Step 3: Update `.env.development`
```bash
GOOGLE_API_KEY="AIza_your_google_api_key_here"
```

### Step 4: Add to `app/core/config.py`
```python
GOOGLE_API_KEY: str = Field(default="", description="Google API Key")
```

### Step 5: Add to `app/services/llm.py`
Import:
```python
from langchain_google_genai import ChatGoogleGenerativeAI
```

Add to LLMS list:
```python
{
    "name": "gemini-1.5-flash",
    "llm": ChatGoogleGenerativeAI(
        model="gemini-1.5-flash",
        google_api_key=settings.GOOGLE_API_KEY,
        temperature=settings.DEFAULT_LLM_TEMPERATURE,
        max_tokens=settings.MAX_TOKENS,
    ),
},
{
    "name": "gemini-1.5-pro",
    "llm": ChatGoogleGenerativeAI(
        model="gemini-1.5-pro",
        google_api_key=settings.GOOGLE_API_KEY,
        temperature=settings.DEFAULT_LLM_TEMPERATURE,
        max_tokens=settings.MAX_TOKENS,
    ),
},
```

---

## 💻 Ollama (100% Free - Runs Locally, No API Key)

### Step 1: Install Ollama
1. Download: https://ollama.com/download
2. Install and start Ollama

### Step 2: Pull a model
```powershell
ollama pull llama3.2
ollama pull phi3
```

### Step 3: Install package
```powershell
& ".\.venv\Scripts\python.exe" -m pip install langchain-ollama
```

### Step 4: Add to `app/services/llm.py`
Import:
```python
from langchain_ollama import ChatOllama
```

Add to LLMS list:
```python
{
    "name": "llama3.2",
    "llm": ChatOllama(
        model="llama3.2",
        base_url="http://localhost:11434",
        temperature=settings.DEFAULT_LLM_TEMPERATURE,
    ),
},
{
    "name": "phi3",
    "llm": ChatOllama(
        model="phi3",
        base_url="http://localhost:11434",
        temperature=settings.DEFAULT_LLM_TEMPERATURE,
    ),
},
```

---

## 📊 Comparison Table

| Provider | Free Tier | Speed | Quality | API Key Required | Best For |
|----------|-----------|-------|---------|------------------|----------|
| **Groq** | ✅ 30 req/min | ⚡⚡⚡ Fastest | ⭐⭐⭐⭐ | Yes (Free) | Speed & Quality |
| **Google Gemini** | ✅ 15 req/min | ⚡⚡ Fast | ⭐⭐⭐⭐⭐ | Yes (Free) | Best Quality |
| **Ollama** | ✅ Unlimited | ⚡ Medium | ⭐⭐⭐ | No | Privacy & Offline |
| OpenAI | ❌ Paid only | ⚡⚡ Fast | ⭐⭐⭐⭐⭐ | Yes (Paid) | - |

---

## 🎯 Quick Start - Just Use Groq

**Fastest way to get started (5 minutes):**

1. Get Groq key: https://console.groq.com/keys
2. Run:
   ```powershell
   & ".\.venv\Scripts\python.exe" -m pip install langchain-groq
   ```
3. Add to `.env.development`:
   ```
   GROQ_API_KEY="your_key_here"
   DEFAULT_LLM_MODEL=llama-3.1-70b-versatile
   ```
4. I'll help you update the code files!

**Need help?** Just let me know which provider you want to use and I'll make all the code changes for you! 🚀
