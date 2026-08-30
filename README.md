# Deep Agent Work Flow

A demonstration of building **deep agents** using the `deepagents` library. This project shows how to create agents that can **plan**, **use subagents**, and **leverage file systems** for complex, multi-step tasks.

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [When to Use Deep Agents](#when-to-use-deep-agents)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration (API Keys)](#configuration-api-keys)
- [Usage](#usage)
  - [Running the Notebook](#running-the-notebook)
  - [Step-by-Step Walkthrough](#step-by-step-walkthrough)
- [Tools Used](#tools-used)
- [Model Selection](#model-selection)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

## Overview

The **Deep Agent Work Flow** project is a hands-on demonstration of the `deepagents` library. Built on top of **LangGraph**, deep agents extend standard agent capabilities with:

- **Planning** – agents can break down complex tasks into manageable steps.
- **Subagents** – the main agent can spawn specialized subagents for context isolation.
- **File systems** – virtual file systems let agents manage large contexts efficiently.
- **Persistence** – memory can be persisted across conversations and threads.

This repository contains an interactive Jupyter notebook that walks you through building a deep agent step-by-step, starting from a simple agent and evolving it into a fully-featured deep agent.

## Key Features

- **Simple Agent**: A basic LangChain agent with a model and a web search tool.
- **Deep Agent**: A full deep agent with planning, subagent support, file system access, and summarization middleware.
- **Web Search Integration**: Uses the Tavily API for reliable, real-time web search.
- **Multi-Provider Support**: The notebook includes automatic fallback between Groq and Google Gemini models.
- **Interactive**: Step-by-step code cells with clear explanations and visualizations of agent graphs.

## When to Use Deep Agents

Deep agents are ideal when you need agents to:

- Handle **complex, multi-step tasks** that require planning.
- Manage **large amounts of context** through file system tools.
- **Delegate work** to specialized subagents for context isolation.
- **Persist memory** across conversations and threads.

## Project Structure

```
.
├── README.md                       # Project documentation
├── requirements.txt                # Python dependencies
├── .gitignore                      # Git ignore rules
└── deep-agent-demo/                # Notebook directory
    └── 1-basic-deep-agent.ipynb    # Interactive deep agent demo
```

## Prerequisites

- **Python 3.10+**
- **Jupyter Notebook** (or JupyterLab, VS Code with Python extension)
- API keys for:
  - **Groq** (for the Llama model) – [Get one here](https://console.groq.com/)
  - **Tavily** (for web search) – [Get one here](https://tavily.com/)
  - **Google Gemini** (optional, for fallback) – [Get one here](https://ai.google.dev/)

## Installation

1. **Clone the repository**:

   ```bash
   git clone https://github.com/your-username/deep-agent-workflow.git
   cd deep-agent-workflow
   ```

2. **Create and activate a virtual environment** (recommended):

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows, use: venv\Scripts\activate
   ```

3. **Install dependencies**:

   ```bash
   pip install -r requirements.txt
   ```

## Configuration (API Keys)

1. **Create a `.env` file** in the project root (or inside `deep-agent-demo/`):

   ```bash
   GROQ_API_KEY=your_groq_api_key_here
   TAVILY_API_KEY=your_tavily_api_key_here
   GOOGLE_API_KEY=your_google_api_key_here  # Optional, for fallback
   ```

2. The notebook automatically loads the `.env` file from either the notebook's directory or the parent directory.

## Usage

### Running the Notebook

1. **Start Jupyter**:

   ```bash
   jupyter notebook
   ```

2. **Open the notebook**:

   Navigate to `deep-agent-demo/1-basic-deep-agent.ipynb` and open it.

3. **Run all cells**:

   Use `Kernel > Restart & Run All` to execute the entire notebook.

### Step-by-Step Walkthrough

The notebook covers the following steps:

1. **Environment setup** – Loads API keys from `.env`.
2. **Web search tool** – Defines a `web_search` function using Tavily.
3. **Model initialization** – Sets up a Groq Llama model (with Gemini fallback).
4. **Simple agent** – Creates a basic agent with the model and the web search tool.
5. **Deep agent** – Creates a full deep agent with:
   - Planning capabilities
   - File system middleware
   - Subagent support
   - Summarization middleware
   - Custom system prompt (`"Act as a researcher"`)
6. **Execution** – Invokes the deep agent with a sample question and displays the result.

## Tools Used

| Tool | Purpose |
|------|---------|
| [deepagents](https://pypi.org/project/deepagents/) | Core library for building deep agents |
| [LangGraph](https://www.langchain.com/langgraph) | Graph-based agent orchestration |
| [LangChain](https://www.langchain.com/) | Agent and tool abstractions |
| [Tavily](https://tavily.com/) | Web search API |

## Model Selection

The notebook uses:

- **Primary**: `groq:meta-llama/llama-4-scout-17b-16e-instruct`
- **Fallback**: `google_genai:gemini-2.5-flash`

If the Groq API key is invalid, the notebook automatically retries with Google Gemini. To change models, modify the `init_chat_model()` calls in the notebook.

## Troubleshooting

| Issue | Solution |
|-------|----------|
| `API key not valid` | Check your API keys in `.env` and ensure they are correctly set. |
| `ModuleNotFoundError` | Run `pip install -r requirements.txt` to install all dependencies. |
| Jupyter cell hangs | Ensure your API keys have sufficient quota/credits. |
| `dotenv` not found | Install `python-dotenv`: `pip install python-dotenv` |

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements, bug fixes, or new features.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.