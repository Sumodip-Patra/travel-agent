# ✈️ AI Travel Agent

A **multi-agent AI travel planner** built with LangChain, LangGraph, and Google Gemini. Just describe your trip in plain English — the agent searches for real flights, hotels, and tour packages and presents you options with links.

---

## 🎬 Demo

```
User:  "Book a trip to Tokyo on 5 August 2026 for 4 days and 3 nights,
        2 people, departure from Mumbai."

Agent: Here are your options:

       ✈️  Flight Options (Round Trip)
           • Japan Airlines (Direct)       — $2,900 total
           • Singapore Airlines (1 stop)   — $2,200 total

       🏨  Hotel Options (3 Nights)
           • Hotel Gracery Shinjuku (4★)   — $600 total
           • The Tokyo Station Hotel (5★)  — $1,200 total

       Which combination would you like?
```

---

## 🧠 Architecture

```
User Query
    │
    ▼
┌─────────────────────────────────────┐
│           Master Agent              │
│  (Gemini 2.0 Flash + LangGraph)     │
└────────────┬───────────┬────────────┘
             │           │           │
             ▼           ▼           ▼
       Hotel Agent  Flight Agent  Tour Package Agent
       (Tavily)     (Tavily)      (Tavily)
```

- **Master Agent** — Understands the user's request, delegates tasks, and maintains multi-turn memory across the conversation
- **Hotel Agent** — Searches for hotels matching dates, location, and guest count
- **Flight Agent** — Searches for available flights between cities on given dates
- **Tour Package Agent** — Finds bundled tour packages with descriptions and booking links

---

## ✨ Features

- 🗣️ Natural language trip planning
- 🔄 Multi-turn conversation memory (remembers your previous choices)
- 🏨 Hotel search with links
- ✈️ Flight search with pricing
- 📦 Tour package recommendations
- 🧒 Handles family trips (children, group sizes)
- 🌏 Works for domestic and international destinations

---

## 🚀 Getting Started

### Run on Google Colab (Recommended)

**Step 1 — Open the notebook in Colab**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_USERNAME/travel-agent/blob/main/TravelAgent.ipynb)

> Replace `YOUR_USERNAME` with your GitHub username after uploading.

**Step 2 — Add your API keys via Colab Secrets**

1. Click the 🔑 **key icon** in the left sidebar
2. Add `GOOGLE_API_KEY` → paste your Google Gemini key
3. Add `TAVILY_API_KEY` → paste your Tavily key
4. Toggle both to **Notebook access: ON**

**Step 3 — Run all cells** (`Runtime → Run all`)

---

### Run Locally

```bash
# 1. Clone the repo
git clone https://github.com/YOUR_USERNAME/travel-agent.git
cd travel-agent

# 2. Install dependencies
pip install -r requirements.txt

# 3. Set up your API keys
cp .env.example .env
# Edit .env and add your real keys

# 4. Open the notebook
jupyter notebook TravelAgent.ipynb
```

---

## 🔑 Getting API Keys

| Key | Where to get it | Free tier |
|-----|----------------|-----------|
| `GOOGLE_API_KEY` | [Google AI Studio](https://aistudio.google.com/apikey) | ✅ Yes |
| `TAVILY_API_KEY` | [Tavily Dashboard](https://app.tavily.com) | ✅ Yes (1000 searches/month) |

---

## 📁 Project Structure

```
travel-agent/
├── TravelAgent.ipynb   # Main notebook — all agent code here
├── requirements.txt    # Python dependencies
├── .env.example        # Template for API keys (safe to share)
├── .gitignore          # Keeps .env and secrets out of Git
└── README.md           # This file
```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| [LangChain](https://python.langchain.com/) | Agent framework and tool definitions |
| [LangGraph](https://langchain-ai.github.io/langgraph/) | Multi-agent orchestration and memory |
| [Google Gemini](https://aistudio.google.com/) | LLM powering all agents |
| [Tavily](https://tavily.com/) | Real-time web search for flights/hotels |

---

## 💬 Example Queries

```
"Book a trip to Tokyo on 5 August 2026 for 4 days, 2 people from Mumbai"

"Book a tour to Darjeeling on 6 July 2026, 4 days, 4 people (1 child age 12) from Nagpur"

"Book a Manali package for 5 days, 4 people, flexible budget, flight on 6 June from Nagpur"
```

---

## ⚠️ Important Notes

- This agent **searches** for travel options but does not make real bookings
- Prices shown are illustrative — verify on official booking platforms
- Always revoke and rotate API keys if accidentally exposed

---

## 📄 License

MIT License — feel free to use and modify this project.

