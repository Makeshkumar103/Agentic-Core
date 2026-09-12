# Week 3 Community Contributions - Best Projects

This document highlights the most outstanding projects from the Week 3 community contributions for the LLM Engineering course. Projects are evaluated on **completeness**, **code quality**, **innovation**, **practical utility**, and **documentation**.

---

## 🏆 Top Tier - Production-Ready Applications

### 1. **Technical Assistant Dataset Generator** — *patrickcmd/tech-assistant-synthetic-data-gen*
**Path:** `patrickcmd/tech-assistant-synthetic-data-gen/`

**Description:** A full-featured Gradio application for generating synthetic conversational datasets tailored for AI Engineer training assistants.

**Key Features:**
- Multi-model support: OpenAI (gpt-4.1-mini), Groq (llama3.2), Ollama (local)
- 4 engineer levels: Beginner, Intermediate, Advanced, Research
- 23 AI engineering topics (RAG, LLM inference, Fine-tuning, Quantization, Agents, etc.)
- Configurable dataset size (5-200 samples) and temperature
- Built-in HuggingFace Hub upload capability
- Clean modular architecture with Pydantic schemas

**Structure:**
```
schemas.py       — Pydantic models (DataPoint, SyntheticDataset)
llm_clients.py   — OpenAI/Groq/Ollama client abstraction
prompt_builder.py — System prompt templates per level & topic
generator.py     — Batch generation pipeline with validation
hf_uploader.py   — HuggingFace dataset upload
app.py           — Gradio UI (entry point)
```

**Why it stands out:** Professional project structure, multi-provider support, excellent documentation, and production-ready features like HF Hub integration.

---

### 2. **Synthetic Data Generator (Juan's)** — *juan_synthetic_data*
**Path:** `juan_synthetic_data/`

**Description:** An intelligent tabular synthetic data generator with statistical evaluation and visualization, originally from [Jsrodrigue/synthetic-data-creator](https://github.com/Jsrodrigue/synthetic-data-creator).

**Key Features:**
- OpenAI GPT-4o-mini / GPT-4.1-mini for tabular data synthesis
- Reference CSV upload to preserve statistical distributions
- Built-in quality evaluation (statistical comparison, TVD, visualizations)
- Pre-loaded example datasets: People, Sentiment, Wine
- Dynamic batching, configurable reference sampling
- Export to CSV, interactive Gradio UI with 5 tabs

**Structure:**
```
app.py                    — Main Gradio application
src/
  ├── constants.py        — Default prompts, reference sample size
  ├── data_generation.py  — Core batch generation & evaluation
  ├── evaluator.py        — Evaluation logic & metrics
  ├── IO_utils.py         — File management & temp directories
  ├── openai_utils.py     — OpenAI API wrappers
  ├── plot_utils.py       — Visualization generation
  └── helpers.py
data/                     — Reference CSV datasets
requirements.txt, pyproject.toml
```

**Why it stands out:** Comprehensive evaluation system with visualizations, statistical rigor, multiple example datasets, and production-grade code organization.

---

### 3. **Job Description One-Pager (Gradio)** — *job-description-one-pager-gradio*
**Path:** `job-description-one-pager-gradio/`

**Description:** Dual-tab Gradio app: (1) Paste job URL/text → generate one-pager, (2) Describe role → generate synthetic job posting → one-pager from it.

**Key Features:**
- Tab 1: Real job → one-pager (summary, requirements, cover letter bullets, resume keywords)
- Tab 2: Synthetic job generation (Week 3 theme) → one-pager pipeline
- 6 model options via OpenRouter (GPT-4o, Claude 3.5, Gemini 2.0, Llama 3.1)
- Streaming responses, save as Markdown
- Clean separation of concerns (`one_pager.py`, `scraper.py`, `app.py`)

**Why it stands out:** Practical real-world use case, creative synthetic data application, multi-model support, excellent UX with streaming.

---

### 4. **AI Web Page Summarizer** — *ai-web-summarizer*
**Path:** `ai-web-summarizer/`

**Description:** Modular web content summarizer supporting OpenAI and Ollama (local) inference engines.

**Key Features:**
- Multi-engine: OpenAI API, Ollama API, Ollama library
- Modular architecture: `fetcher.py`, `summarizer.py`, `utils/logger.py`
- CLI interface with environment configuration
- Error handling and logging throughout

**Structure:**
```
main.py                 — Entry point
summarizer/
  ├── fetcher.py        — Web content fetching
  └── summarizer.py     — Summarization logic
utils/
  └── logger.py         — Logging configuration
requirements.txt
```

**Why it stands out:** Clean modular design, local + cloud inference support, well-documented, educational value.

---

## 🥈 High Quality - Specialized Tools

### 5. **Dataset Quality Auditor** — *BernardUdo/dataset_quality_auditor.py*
**Path:** `BernardUdo/dataset_quality_auditor.py`

**Description:** CLI tool that compares synthetic CSV against reference CSV and generates a comprehensive Markdown quality report.

**Key Features:**
- Schema alignment scoring (column overlap, missing/extra columns)
- Missingness & uniqueness comparison per column
- Numeric drift analysis (mean, std deviation)
- Categorical distribution distance (Total Variation Distance)
- Smart CSV header detection (handles headerless CSVs)
- Single-file, zero-dependency (pandas only), CLI with argparse

**Why it stands out:** Addresses a critical gap (quality evaluation), robust CSV handling, actionable metrics, standalone utility.

---

### 6. **Car Model Dataset Generator** — *aryaman/dataset_generator/*
**Path:** `aryaman/dataset_generator/`

**Description:** Generates detailed automotive text datasets (car model profiles + brand profiles) using Ollama local LLMs.

**Key Features:**
- 100+ car models across 30+ brands (mass market to hypercars)
- Parallel generation with ThreadPoolExecutor (configurable workers)
- Retry logic with exponential backoff
- Two output types: car model profiles (700-1000 words) + brand profiles (500-800 words)
- Structured prompts covering class, generations, powertrain, safety, trims, legacy
- CLI with full configuration (count, overwrite, retries, workers)

**Structure:**
```
generate_car_dataset.py   — Main generation script
ollama_client.py          — Ollama client wrapper
build_jsonl_dataset.py    — Convert to JSONL for training
demo/ollama_car_dataset_demo.ipynb
```

**Why it stands out:** Domain-specific expertise, large-scale generation capability, robust error handling, local LLM focus.

---

### 7. **Token Probability Visualizer** — *aswamina/visualizer.py*
**Path:** `aswamina/visualizer.py` (also `visualizer_groq.py`, `visualizer_anthropic.py`, `visualizer_HF.py`)

**Description:** Visualizes LLM token-by-token prediction probabilities as a directed graph using NetworkX + Matplotlib.

**Key Features:**
- Streams tokens with logprobs (top 3 alternatives per position)
- Graph visualization: main sequence + alternative branches
- Multi-provider support: OpenAI, Groq, Anthropic, HuggingFace
- Vertical layout with alternating alternative positions
- Color-coded nodes (start=green, main=blue, alt=gray, end=red)

**Why it stands out:** Unique educational/debugging tool, visualizes model uncertainty, multi-provider, clean graph rendering.

---

### 8. **Story-Driven Dataset Generator** — *story_driven_dataset_generator/*
**Path:** `story_driven_dataset_generator/`

**Description:** Creative synthetic data generator with 5 generation modes and narrative-driven approaches.

**Key Features:**
- **5 Modes:** Standard, Story Chain (chronological narrative), Model Battle (side-by-side comparison), Data Remix (style transfer), Custom
- Multi-model: OpenAI (GPT-4o-mini, GPT-4o), Google Gemini (1.5 Flash, 2.0 Flash)
- **3 Style Personas:** Corporate Analyst, Creative Writer, Data Scientist
- **6 Pre-built Domains:** Startup Journey, Customer Journey, Patient Treatment, Stock Performance, Game Progress
- Gradio UI with domain/persona/model selection

**Why it stands out:** Innovative narrative approach, model comparison feature, style personas, diverse domains.

---

### 9. **Media Coverage Synthetic Data Generator** — *week3_assignment_data_generator_congress.py*
**Path:** `week3_assignment_data_generator_congress.py`

**Description:** Spanish/English synthetic data generator for media coverage analysis of events (congresses, conferences).

**Key Features:**
- 3 dataset types: Events, Media Coverage, Social Mentions
- Dual provider: OpenAI (GPT-4o-mini) + Anthropic (Claude 3.5 Haiku)
- Rich schema: sentiment scores, stance, reach, entities, hashtags, topic tags
- Temporal coherence, multilingual support (ES/EN)
- Gradio UI with event configuration (type, dates, location, attendance)
- JSON extraction with robust parsing (handles ```json``` blocks)

**Why it stands out:** Domain-specific (media analytics), multi-provider, rich structured output, bilingual.

---

### 10. **Legal Q&A Generator** — *legal_qna_generator/legal_qna_generator.ipynb*
**Path:** `legal_qna_generator/legal_qna_generator.ipynb`

**Description:** Generates synthetic Indian legal Q&A pairs with fictional but realistic legal sections.

**Key Features:**
- 10 legal topic seeds (criminal, property, contract, constitutional, IP, cyber, etc.)
- 7 question types (definition, procedure, penalty, rights, obligations, exceptions, examples)
- Generates fictional IPC/CrPC/IEA sections with legal language
- Q&A pair generation from synthetic sections
- Gradio UI for interactive generation
- JSON export

**Why it stands out:** Highly specialized domain, realistic legal formatting, structured Q&A generation.

---

## 🎯 Notable Mentions - Creative & Specialized

| Project | Path | Highlight |
|---------|------|-----------|
| **Podcast-to-Blog Summarizer** | `adams-bolaji/podcast_blog_summarizer.ipynb` | Whisper + Llama pipeline, audio → structured blog |
| **Anime Audio Translator** | `anime_audio_translator.colab.ipynb` | Whisper + Llama-3.1-8B, Japanese audio → English |
| **Telegram Bot with TTS** | `telegram_bot_llm/tg_lb_bot.py` | Quart webhook + Ollama + Balabolka TTS, cynical persona |
| **Meeting Minutes from Audio** | `day5_with_Gradio.ipynb`, `06_meeting_minute_assistant.ipynb` | Whisper transcription → Llama summarization → Gradio UI |
| **Nigerian Food Ingredients Generator** | `week_3_exercise_nigerian_food_ingredients_generator.ipynb` | Culturally specific synthetic data |
| **Synthetic Healthcare Data** | `synthetic-healthcare-data/app.ipynb` | Domain-specific healthcare data generation |
| **Portuguese-Brazilian Synthetic Data** | `week3-exercise-pt-br-synthetic-data-generator.ipynb` | Localized Portuguese data generation |
| **Intelligent Dataset Generator** | `intelligent_dataset_generator.ipynb` | Multi-strategy generation with validation |

---

## 📊 Category Summary

| Category | Count | Examples |
|----------|-------|----------|
| **Full Gradio Apps** | 12+ | Technical Assistant, Juan's Generator, Job One-Pager, AI Summarizer |
| **Synthetic Tabular Data** | 15+ | Juan's, Congress Media, Car Dataset, Healthcare, Wine/People/Sentiment |
| **Synthetic Text/Narrative** | 10+ | Story-Driven, Legal Q&A, Car Profiles, Anime Translator |
| **Audio/Voice Pipeline** | 6+ | Podcast→Blog, Meeting Minutes, Anime Translator, Telegram TTS |
| **Evaluation/Quality Tools** | 3 | Dataset Quality Auditor, Juan's Evaluator, Token Visualizer |
| **Multi-Model/Provider** | 8+ | Technical Assistant (3), Job One-Pager (6), Story-Driven (2), Congress (2) |
| **Local LLM (Ollama)** | 7+ | Technical Assistant, Car Generator, Token Visualizer, Telegram Bot |
| **HuggingFace Integration** | 4+ | Technical Assistant, Juan's (reference), Anime Translator, Meeting Minutes |

---

## 💡 Recommendations for Future Contributors

1. **Follow the modular pattern** from `patrickcmd` and `juan_synthetic_data` — separate concerns (clients, prompts, generation, UI)
2. **Add evaluation** — like `BernardUdo`'s auditor or `juan_synthetic_data`'s built-in metrics
3. **Support multiple providers** — OpenAI + Groq + Ollama + Anthropic increases accessibility
4. **Document with README** — clear setup, usage, architecture (see top 4 projects)
5. **Consider niche domains** — legal, healthcare, automotive, media analytics show creativity
6. **Add visualization** — token graphs, distribution plots, comparison charts add significant value
7. **Enable local inference** — Ollama support makes projects accessible without API keys

---

## 🔗 Quick Access

| Project | Entry Point | Type |
|---------|-------------|------|
| Technical Assistant Dataset Gen | `patrickcmd/tech-assistant-synthetic-data-gen/app.py` | Gradio App |
| Juan's Synthetic Data Generator | `juan_synthetic_data/app.py` | Gradio App |
| Job Description One-Pager | `job-description-one-pager-gradio/app.py` | Gradio App |
| AI Web Summarizer | `ai-web-summarizer/main.py` | CLI |
| Dataset Quality Auditor | `BernardUdo/dataset_quality_auditor.py` | CLI |
| Car Dataset Generator | `aryaman/dataset_generator/generate_car_dataset.py` | CLI |
| Token Visualizer | `aswamina/visualizer.py` | Script |
| Story-Driven Generator | `story_driven_dataset_generator/story_driven_dataset_generator.ipynb` | Notebook |
| Legal Q&A Generator | `legal_qna_generator/legal_qna_generator.ipynb` | Notebook |
| Congress Media Generator | `week3_assignment_data_generator_congress.py` | Gradio App |

---

*Generated from analysis of 199 community contributions in `llm_engineering/week3/community-contributions/`*