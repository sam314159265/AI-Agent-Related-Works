# AI Agent & RAG Pipeline Projects

Three small projects exploring different AI agent patterns using Google's Gemini API — from a simple self-critique loop, to a tool-calling agent, to a full agentic RAG (Retrieval-Augmented Generation) pipeline.

## Projects

### 1. Simple AI Agent (`simple_ai_agent.ipynb`)
A minimal example of an agent that improves its own output through self-critique:
- Generates an initial answer to a question
- Critiques its own answer
- Produces a final, revised answer based on that feedback

Also includes a simple stateful chatbot built on Gemini's chat session API, which keeps conversation memory across turns using a system-prompt persona.

### 2. Tool-Using Agent — Stock Market Assistant (`api_integration.ipynb`)
A Gemini agent that can call external tools:
- `get_stock_price` — fetches a live stock quote via the Financial Modeling Prep API
- `calculator` — evaluates basic math expressions

Demonstrates Gemini's function-calling / tool-use interface, with a system prompt that restricts the agent to using its tools and avoiding financial advice.

### 3. Agentic RAG Pipeline (`Design and Implementation of an Agentic RAG Pipeline using the Gemini API.ipynb`)
The most complete project here: a Retrieval-Augmented Generation pipeline with an iterative refine loop.
- Loads and chunks uploaded PDF/text documents
- Embeds each chunk with Gemini's embedding model and retrieves the most relevant chunks via cosine similarity
- Runs a 3-agent loop: a **planner** agent proposes a search query, an **answer** agent retrieves context and answers, and a **critic** agent scores the answer and either accepts it or feeds back an improved query for another round
- Demonstrated on a sample PDF (ARC Prize 2025 Technical Report)

## Tech stack
- Google Gemini API (`google-genai`), including `gemini-2.0-flash`, `gemini-2.5-flash`, and `gemini-embedding-001`
- `pypdf` for PDF text extraction
- `numpy` / `scikit-learn` for embeddings and cosine similarity
- Financial Modeling Prep API (stock price data)

## Running these notebooks
These were originally written in Google Colab and include some Colab-specific cells (file upload widgets, `!pip install`). To run them elsewhere:
1. Install the dependencies listed above
2. Set your own Gemini API key as an environment variable (`GEMINI_API_KEY`) rather than hardcoding it in the notebook
