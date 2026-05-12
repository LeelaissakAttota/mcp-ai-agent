# 🤖 Multi-Server AI Agent with Model Context Protocol (MCP)

![Language](https://img.shields.io/badge/Language-Python%203.10+-3776AB?style=flat-square&logo=python&logoColor=white)
![Protocol](https://img.shields.io/badge/Protocol-Model%20Context%20Protocol-6A0DAD?style=flat-square)
![Agent](https://img.shields.io/badge/Agent-LangGraph%20ReAct-FF7C00?style=flat-square)
![LLM](https://img.shields.io/badge/LLM-GPT--5%20Nano-412991?style=flat-square&logo=openai&logoColor=white)
![Transport](https://img.shields.io/badge/Transport-STDIO%20%7C%20HTTP-00897B?style=flat-square)
![Memory](https://img.shields.io/badge/Memory-InMemorySaver-2E7D32?style=flat-square)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat-square)

---

## 📌 Project Overview

This project demonstrates a **production-ready Multi-Server Agentic AI 
system** built using the Model Context Protocol (MCP).

The agent acts as a **"Universal Interface"** — like a USB-C for AI — 
connecting simultaneously to multiple MCP servers across different 
transport protocols, with **persistent conversation memory** and 
**autonomous tool selection** powered by GPT-5 Nano.

**Domain:** Agentic AI — Multi-Server MCP Agent  
**Language:** Python 3.10+  
**LLM:** OpenAI GPT-5 Nano  
**Agent:** LangGraph ReAct with persistent memory  

---

## 🏗️ Architecture

```
┌──────────────────────────────────────────────────────┐
│           User (CLI Interface)                        │
│   "What paintings did Monet create?"                 │
│   "Show me LangChain documentation"                  │
└───────────────────────┬──────────────────────────────┘
                        │
┌───────────────────────▼──────────────────────────────┐
│         LangGraph ReAct Agent                         │
│   GPT-5 Nano — Reasoning + Acting                    │
│   InMemorySaver — thread_id conversation memory      │
│   Autonomously selects which MCP server to call      │
└──────────┬────────────────────────┬──────────────────┘
           │                        │
    HTTP Transport            STDIO Transport
           │                        │
┌──────────▼──────────┐   ┌─────────▼──────────────────┐
│   Context7 Server   │   │   MetMuseum-MCP Server      │
│   (Remote/Cloud)    │   │   (Local via npx)           │
│                     │   │                             │
│  LLM-optimized      │   │  400,000+ artworks          │
│  documentation      │   │  Metadata + images          │
│  search across      │   │  Metropolitan Museum        │
│  major frameworks   │   │  of Art collection          │
└─────────────────────┘   └─────────────────────────────┘
```

---

## 📂 Project Structure

```
mcp-ai-agent/
│
├── main.py          # Complete multi-server MCP agent
└── README.md
```

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| Language | Python 3.10+ |
| MCP Client | MultiServerMCPClient (langchain-mcp-adapters) |
| Agent Framework | LangGraph ReAct |
| LLM | OpenAI GPT-5 Nano |
| Memory | InMemorySaver (persistent conversation) |
| Async | asyncio |
| MCP Server 1 | Context7 (HTTP — remote cloud) |
| MCP Server 2 | MetMuseum-MCP (STDIO — local npx) |

---

## 🔌 Integrated MCP Servers

| Server | Transport | Capabilities |
|---|---|---|
| **Context7** | HTTP (`streamable_http`) | LLM-optimized docs search across major software frameworks & libraries |
| **MetMuseum-MCP** | STDIO (`npx metmuseum-mcp`) | Access to 400,000+ Metropolitan Museum artworks, metadata & images |

---

## 🌟 Key Features

### 🧠 LangGraph ReAct Agent
```python
agent = create_react_agent(
    model=openai_model,     # GPT-5 Nano reasoning engine
    tools=tools,            # All tools from both MCP servers
    checkpointer=checkpointer  # Persistent conversation memory
)
```

### 💾 Persistent Conversation Memory
```python
checkpointer = InMemorySaver()
config = {"configurable": {"thread_id": "conversation_id"}}
# Agent remembers full conversation history across all turns
```

### 🔗 Multi-Server Connection
```python
client = MultiServerMCPClient({
    "context7": {
        "url": "https://mcp.context7.com/mcp",
        "transport": "streamable_http",    # Remote HTTP
    },
    "met-museum": {
        "command": "npx",
        "args": ["-y", "metmuseum-mcp"],
        "transport": "stdio",              # Local STDIO
    }
})
tools = await client.get_tools()  # All tools from both servers
```

### 🤖 Autonomous Tool Selection
The agent intelligently decides which server to call:
```
User: "What is the LangChain documentation for agents?"
→ Agent calls Context7 tools → Returns LLM-optimized docs

User: "Show me Van Gogh paintings in the Met Museum"
→ Agent calls MetMuseum tools → Returns artwork metadata & images
```

---

## ⚙️ How to Run

**Step 1 — Install dependencies:**
```bash
pip install langchain-mcp-adapters langgraph langchain-openai
npm install -g npx   # For MetMuseum STDIO server
```

**Step 2 — Set OpenAI API key:**
```bash
export OPENAI_API_KEY="your-api-key-here"
```

**Step 3 — Run the agent:**
```bash
python main.py
```

**Step 4 — Interact:**
```
Agent introduces itself and available tools...

Menu:
1. Ask the agent a question
2. Quit
Enter your choice (1 or 2): 1

Your question
> What LangGraph tools are available for building agents?
→ Agent queries Context7 → Returns documentation

> Show me Impressionist paintings from the Met Museum
→ Agent queries MetMuseum → Returns artwork data
```

---

## 🔄 Agent Workflow

```
User Query
    │
    ▼
GPT-5 Nano Reasoning
"Which server has this information?"
    │
    ├─── Library/Code docs? → Context7 (HTTP)
    │
    └─── Art/Museum data? → MetMuseum (STDIO)
    │
    ▼
Tool Execution → Result returned to LLM
    │
    ▼
LLM generates natural language response
    │
    ▼
Stored in InMemorySaver (thread_id)
    │
    ▼
User receives response + context preserved
```

---

## 🎓 Skills Demonstrated

- Multi-server MCP client architecture
- Simultaneous STDIO + HTTP transport management
- LangGraph ReAct agent with tool calling
- GPT-5 Nano integration via OpenAI API
- Persistent conversation memory with InMemorySaver
- Thread-based conversation management
- Async Python — asyncio + await patterns
- Real external MCP server integration (Context7 + MetMuseum)
- Autonomous tool selection by LLM reasoning
- Natural language interface for multi-domain queries
- Node.js MCP server integration via npx

---

## 📜 Certifications

| Certification | Issuer | Platform |
|---|---|---|
| IBM Data Science Professional Certificate | IBM | Coursera |
| IBM Generative AI Professional Certificate | IBM | Coursera |
| IBM RAG and Agentic AI Professional Certificate | IBM | Coursera |

---

## 🤝 Connect with Me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Leela%20A-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/leela-a)
[![Gmail](https://img.shields.io/badge/Gmail-attotaleelaissak@gmail.com-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:attotaleelaissak@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-Leelaissakattaota-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Leelaissakattaota)
