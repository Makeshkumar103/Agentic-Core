# Best Community Contributions - Week 2

Curated list of the most impressive, complete, and innovative projects from the Week 2 community contributions.

---

## 🏆 Top Tier - Production-Ready Applications

### 1. **Model Arena** (`kacper_lechicki/model_arena/`)
**Multi-LLM Comparison Platform with Judge Evaluation**
- **Tech Stack**: Gradio, SQLite, OpenRouter/Gemini/Ollama, Custom CSS/JS
- **Features**:
  - Streaming responses from multiple LLMs simultaneously
  - GPT-4o judge evaluates responses on Accuracy, Conciseness, Tone, Speed
  - History tracking with session persistence (SQLite)
  - Winner badges, score bars, detailed reasoning
  - Responsive dark-themed UI with animations
- **Structure**: Modular `src/` with `arena.py`, `judge.py`, `db.py`, `config.py`
- **Standout**: Clean architecture, production-grade UI, real-time streaming

---

### 2. **Voice-Enabled Multi-Model AI Assistant** (`salah/v2/`)
**Full-Stack Voice Assistant with STT/TTS**
- **Tech Stack**: Gradio, OpenRouter, Gemini (STT/TTS), Modular Service Architecture
- **Features**:
  - Real-time voice conversation with multiple LLM backends
  - Speech-to-text (Gemini) + Text-to-speech (Gemini)
  - Conversation memory management
  - Configurable models, voices, system prompts
  - Clean service-layer architecture (`services/`, `ui/`, `models/`, `config/`)
- **Structure**: Professional Python package structure with `run.py` entry point

---

### 3. **AI Travel Planner** (`makinda/ai_travel_planner/`)
**Telegram Bot + Gradio Web UI for Travel Planning**
- **Tech Stack**: Telegram Bot API, Gradio, SQLite, Threading
- **Features**:
  - Dual interface: Telegram bot AND Gradio web app
  - Travel planning with budget, dates, preferences
  - Database-backed persistence
  - Modular design: `bot.py`, `app.py`, `planner.py`, `database.py`
  - CLI flags to run bot only, Gradio only, or both
- **Standout**: Multi-platform deployment, clean separation of concerns

---

### 4. **Mafia Game - LLM Social Deduction** (`aryaman/mafia/mafia_game.py`)
**Fully Playable Mafia Game with LLM Players**
- **Tech Stack**: Ollama (local LLMs), OpenAI-compatible API
- **Features**:
  - 3-player game: Mafia, Doctor, Detective roles
  - Night phases: Mafia kill, Doctor protect, Detective investigate
  - Day phases: Public discussion + voting
  - Private Mafia coordination chat
  - Detective private investigation results
  - Win condition checking (Villagers vs Mafia)
  - Full conversation history tracking per player
- **Standout**: Complex multi-agent interaction, game theory implementation, role-based information asymmetry

---

## 🥈 High Quality - Complete Feature Sets

### 5. **AI Gold Investment Assistant** (`AI Gold Investment Assistant/ai_investment_estimations.ipynb`)
**Multi-Agent Investment Platform with Voice & Translation**
- **Features**:
  - Real-time gold prices via MetalPriceAPI (11 currencies)
  - AI-powered investment advice with risk assessment tool
  - Fake gold purchase simulation with JSON persistence
  - Arabic translation agent (all responses auto-translated)
  - Speech-to-text via OpenAI Whisper
  - Multi-panel Gradio UI: English chat + Arabic panel + Feature docs
- **Agents**: Price Agent, Purchase Agent, Translation Agent, STT Agent

---

### 6. **AI Career Planner** (`AI-career-planner-with-UI-waijian1/`)
**Job Market Analysis + 4-Week Study Plan Generator**
- **Tech Stack**: Gradio, Gemini/Ollama, Job Search API, Country codes CSV
- **Features**:
  - Live job search by title + country
  - Analyzes real job postings for skill requirements
  - Generates personalized 4-week learning plans
  - Highlights top 5 companies, apply links, required skills
  - Streaming responses, model selector (Gemini/Ollama)
  - Country dropdown with 200+ countries

---

### 7. **Medical Prescription → Google Calendar** (`medical_prescription_to_google_calender/`)
**OCR Pipeline for Medicine Scheduling**
- **Pipeline**: OCR → Text Cleaning → Structured Parsing → Date Processing → Calendar Events
- **Features**:
  - Image-based prescription reading
  - Medication extraction with dosage/frequency
  - Automatic Google Calendar event creation
  - Date parsing for "daily", "twice daily", specific times
  - Modular: `ocr.py`, `preprocess.py`, `parsing_json.py`, `calendar_auth.py`, `create_calender_events.py`

---

### 8. **Flight Assistant with Booking & Price Checking** (`Flight Assistant with booking and price checking/week2solution.ipynb`)
**Complete Travel Booking Agent**
- **Features**:
  - Flight search with Amadeus API integration
  - Price comparison across dates/airlines
  - Booking simulation with confirmation
  - Multi-tool orchestration (search, price, book)
  - Gradio interface for user interaction

---

## 🥉 Notable Projects - Unique Concepts

### 9. **AI Library Clerk** (`AI Library Clerk/main.ipynb`)
- Library management with book search, checkout, returns
- Gradio interface with persistent state

### 10. **3-Way Chatbot Conversations** (Multiple implementations)
- **Final Fantasy Characters** (`3_way_chatbot_conversations_final_fantasy_characters/`) - Character-based roleplay
- **Sherlock Holmes Trialogue** (`Day1_SherlockHolmes_Trialogue.ipynb`) - Literary character debate
- **Presidential Debate** (`day1_presidential_debate.ipynb`) - Political simulation
- **British 3-Way Chat** (`3_way_brit_chat/`) - Regional persona simulation
- **Football Conversation** (`3_way_football_conversation_anton_kenderov/`) - Sports discussion

### 11. **Word Chain Game** (`word-chain-game/`)
- Multi-player word chain validator with LLM opponents
- Game logic + Gradio UI

### 12. **CyberPunk Panel** (`CyberPunkPanel/`)
- Themed multi-agent panel discussion with cyberpunk personas

### 13. **Accessible Design Review Panel** (`Accessible_Design_Review_Panel.ipynb`)
- Multi-agent accessibility audit for UI designs

### 14. **Technical QA Assistant** (`technical-qa-assistant/` / `technical-question-answerer-with-gradio-v3.ipynb`)
- Code review and technical question answering with Gradio

### 15. **Weather Agent** (`weather_agent.ipynb`)
- Weather tool integration with conversational interface

### 16. **Course Booking Assistant** (Multiple: `day 4 - course booking assistant.ipynb`, `week2_day4_exercise.ipynb`)
- Multi-tool booking flow with availability checking

### 17. **Brochure Generator with Gradio** (`brochure-generator-interface.ipynb`, `brochure-builder-with-gradio.ipynb`)
- Multi-shot prompting for marketing brochure creation

### 18. **Model Version Selector** (`specific_model_version_selection.ipynb`)
- Dynamic model version selection UI

### 19. **Voting Bots** (`oob-Week_2-Day_5-Voting_Bots.ipynb`)
- Multiple LLMs vote on answers, consensus mechanism

### 20. **ISP Customer Care** (`week2-ISP-Customer_Care.ipynb`)
- Telecom support simulation with tool calling

---

## 📊 Category Summary

| Category | Count | Notable Examples |
|----------|-------|------------------|
| **Multi-Agent Systems** | 15+ | Model Arena, Mafia Game, CyberPunk Panel, 3-Way Chats |
| **Tool-Using Agents** | 20+ | Flight Assistant, Gold Investment, Medical OCR, Career Planner |
| **Voice/Multimodal** | 8+ | Salah v2, Gold Investment (STT), Airlines Audio, Voice Assistant |
| **Gradio UIs** | 30+ | Nearly all major projects |
| **Game/Simulation** | 5+ | Mafia Game, Word Chain, Voting Bots, Debate Simulations |
| **Real-World Integrations** | 10+ | Google Calendar, Amadeus Flights, MetalPriceAPI, Job Search, Telegram |

---

## 🎯 Recommendations for Further Development

1. **Model Arena** → Add ELO ratings, tournament brackets, export results
2. **Mafia Game** → Web UI (Gradio), spectator mode, configurable player count
3. **AI Travel Planner** → Add maps, itinerary export, hotel/activity booking
4. **Medical Prescription** → Mobile app, pharmacy integration, refill reminders
5. **Gold Investment** → Portfolio tracking, price alerts, historical charts
6. **Career Planner** → Resume builder, interview prep, skill gap analysis

---

## 📁 How to Run

Most projects use standard Python/Gradio:

```bash
# Model Arena
cd kacper_lechicki/model_arena && python app.py

# Salah Voice Assistant
cd salah/v2 && python run.py

# AI Travel Planner
cd makinda/ai_travel_planner && python main.py --gradio

# Mafia Game (requires Ollama)
cd aryaman/mafia && python mafia_game.py

# Gold Investment (Jupyter)
jupyter notebook "AI Gold Investment Assistant/ai_investment_estimations.ipynb"
```

---

*Curated from 459 community contributions in Week 2 of LLM Engineering Course*
+ Thought: 839ms
Created BEST_PROJECTS.md with 20 curated projects across 4 tiers:
Top Tier (Production-Ready):
Model Arena - Multi-LLM comparison with judge evaluation, SQLite history, streaming UI
Voice Assistant (salah/v2) - Full STT/TTS pipeline, modular service architecture
AI Travel Planner - Telegram bot + Gradio dual interface, threaded deployment
Mafia Game - Complete social deduction game with LLM players, role-based info asymmetry
High Quality:
5. AI Gold Investment - 11 currencies, risk assessment tool, purchase simulation, Arabic translation, Whisper STT
6. AI Career Planner - Live job search → 4-week study plans, 200+ countries
7. Medical Prescription → Calendar - OCR pipeline → Google Calendar events
8. Flight Assistant - Amadeus API, multi-tool booking flow
Notable (12 more) including 3-way character chats, word chain game, cyberpunk panel, accessibility reviewer, technical QA, voting bots, ISP support.
The file includes category summary table and run instructions for each major project.