# Week 5 Community Contributions — Best Projects

Curated selection of standout projects from the LLM Engineering Week 5 community submissions. Each demonstrates a unique approach to RAG, agentic workflows, or knowledge management.

---

## 1. Agentic RAG Challenge — ReAct-Style Iterative Retrieval

**Author:** `week5-challenge-agentic-rag`  
**Type:** Full agentic RAG system with self-evaluation loop  
**Stack:** Python, ChromaDB, LiteLLM, Groq/OpenAI, Gradio, Pydantic, Tenacity

### Why It's Exceptional
This is the most sophisticated implementation in the collection — a **ReAct (Reasoning + Acting) agent** that iteratively refines answers through retrieval and self-evaluation, rather than a single static retrieval pass.

### Architecture
```
User Question
    ↓
┌─────────────────────────────────────┐
│  ReAct Loop (up to 15 turns)        │
│                                     │
│  Thought → Action → Observation     │
│                                     │
│  Tools:                             │
│  - vector_search: semantic search   │
│  - text_search: keyword search      │
│  - rerank: reorder chunks           │
│  - judge_answer: evaluate draft     │
│  - final_answer: submit response    │
└─────────────────────────────────────┘
    ↓
Final Answer + Retrieved Chunks
```

### Key Innovations
| Feature | Description |
|---------|-------------|
| **Self-Evaluation Gate** | Agent must call `judge_answer` and meet thresholds (Accuracy=5, Relevance=5, Completeness≥4) before `final_answer` |
| **Dual Retrieval** | Vector search + keyword search (with strict single-word queries for names) |
| **Mandatory Reranking** | LLM-based reranking required before every evaluation |
| **Structured ReAct Parsing** | Robust parsing handles malformed LLM output |
| **Debug Logging Levels** | 5 verbosity levels (0=silent → 4=full LLM responses) |
| **Evaluation Harness** | Built-in retrieval + answer evaluation with CLI |

### Files of Interest
- `implementation/answer.py` — Core agent loop (910 lines)
- `evaluation/eval.py` — Automated evaluation pipeline
- `evaluation/tests.jsonl` — Ground truth test cases
- `app.py` — Gradio UI with side-by-side context view

### Run
```bash
cd week5/community-contributions/week5-challenge-agentic-rag
uv pip install -e .
echo "OPENAI_API_KEY=..." > .env
echo "GROQ_API_KEY=..." >> .env
python app.py
```

---

## 2. Personal Knowledge Worker RAG — Multi-Source Document Intelligence

**Author:** `vic_knowledge_worker_with_RAG`  
**Type:** End-to-end personal knowledge management with auto-conversion  
**Stack:** LangChain, Chroma, HuggingFace/OpenAI embeddings, Gradio, Plotly, t-SNE

### Why It's Exceptional
**Automatic file conversion pipeline** — Drop raw files (PDF, Word, Excel, PPT, images) into `knowledge_base_raw/`, system auto-converts to Markdown in `knowledge_base_markdown/` for embedding.

### Features
- **Multi-format ingestion**: PDF, DOCX, XLSX, PPTX, images (OCR), EPUB, HTML, TXT
- **History-aware retrieval**: Maintains conversational context
- **Embedding visualization**: 2D/3D t-SNE plots of vector space
- **Gradio ChatInterface**: Clean chat UI with streaming
- **Modular design**: Separate notebooks for ingestion, chat, visualization

### Architecture
```
knowledge_base_raw/  →  Auto-convert  →  knowledge_base_markdown/
                                                      ↓
                                              Chunk + Embed
                                                      ↓
                                              Chroma Vector DB
                                                      ↓
                                              Gradio Chat + Viz
```

### Run
```bash
cd week5/community-contributions/vic_knowledge_worker_with_RAG
uv add gradio plotly numpy scikit-learn tiktoken python-dotenv \
  langchain langchain-openai langchain-huggingface langchain-chroma langchain-community
echo "OPENAI_API_KEY=..." > .env
# Run personal_info_bucket.ipynb → converts files → launches chat
```

---

## 3. Recipe Tailor RAG — Domain-Specific Assistant with Smart Routing

**Author:** `davenjeru`  
**Type:** Cooking assistant with intent-based query routing  
**Stack:** OpenAI, ChromaDB, Gradio, custom RAG engine

### Why It's Exceptional
**Intent classification without an LLM classifier** — uses keyword heuristics to route queries to specialized handlers (ingredient-based, time-constrained, dietary, cooking technique, general), each with tailored prompts.

### Query Routing Logic
| Trigger Keywords | Handler | Example Query |
|------------------|---------|---------------|
| `ingredient`, `have`, `using`, `with` | `_handle_ingredient_query` | "What can I make with chicken and rice?" |
| `quick`, `fast`, `minutes`, `time` | `_handle_time_query` | "Dinner under 30 minutes" |
| `vegetarian`, `vegan`, `gluten-free` | `_handle_dietary_query` | "Healthy vegetarian recipes" |
| `how to`, `cook`, `prepare`, `make` | `_handle_cooking_query` | "How do I cook perfect pasta?" |
| (fallback) | `_handle_general_query` | "Italian dinner ideas" |

### Specialized Search Methods
- `search_by_ingredients(ingredients, max_results)` — filters recipes containing ingredients
- `search_by_time(max_prep_time, max_results)` — filters by prep/cook time
- `search_natural_language(query, max_results)` — semantic search fallback

### Run
```bash
cd week5/community-contributions/davenjeru
# Ensure config.py, rag_core.py, data_pipeline.py, app.py are present
echo "OPENAI_API_KEY=..." > .env
python app.py
```

---

## 4. Personal Knowledge Assistant — Google Workspace + Outlook + Local Files

**Author:** `Week5_Exercise_Personal_Knowledge`  
**Type:** Unified knowledge assistant with cloud email/drive integration  
**Stack:** LangChain, Chroma, Google APIs (Gmail, Drive), Microsoft Graph (Outlook), Gradio

### Why It's Exceptional
**Most ambitious integration scope** — connects **four distinct data sources** with OAuth flows:
1. **Local files** (multi-format via reused conversion code)
2. **Gmail** — alias-based auth, time-range email extraction
3. **Outlook** — device-code flow for Microsoft Graph
4. **Google Workspace / Drive** — folder-specific document extraction

### Project Structure
```
The project/
├── credentials/
│   ├── gmail_credentials.json
│   └── google_workspace_credentials.json
├── tokens/              # Auto-created
│   ├── gmail_tokens/
│   ├── google_workspace_tokens/
│   └── outlook_tokens/
├── vector_index/
│   ├── local_vector_index
│   ├── google_workspace_vector_index
│   ├── gmail_vector_index
│   └── output_vector_index
├── Week5_Exercise_Personal_Knowledge_Assistant.ipynb
├── Gmail_API_Credential_Guide.ipynb
├── Outlook_API_Credential_Guide.ipynb
└── Google_Workspace_API_Credential_Guide.ipynb
```

### TO-DO Roadmap (shows forward thinking)
- Slack integration
- Local LLM/embedding models (Llama)
- Optimized auth flows
- Source-labeled vector stores (private vs work)
- Vector visualization

---

## 5. RAG Without LangChain — From-Scratch Implementation

**Author:** `day 4 no_langchain`  
**Type:** Pure Python RAG — no framework dependencies  
**Stack:** ChromaDB (direct), OpenAI SDK, NumPy, scikit-learn (t-SNE), Plotly, Gradio

### Why It's Exceptional
**Pedagogical gold** — builds every RAG component manually to demystify what frameworks abstract away. Based on [this blog post](https://blog.futuresmart.ai/building-rag-applications-without-langchain-or-llamaindex).

### Manual Components Built
```python
# Custom Document class (replaces LangChain's)
class Document:
    def __init__(self, metadata, page_content):
        self.metadata = metadata
        self.page_content = page_content

# Direct Chroma usage
client = chromadb.PersistentClient(path="chroma_db")
collection = client.get_or_create_collection("my_collection")
collection.add(documents=chunks, embeddings=embeddings, ids=ids, metadatas=metadatas)

# Manual retrieval + generation
results = collection.query(query_embeddings=[query_embedding], n_results=5)
context = "\n".join(results['documents'][0])
response = openai.chat.completions.create(model="gpt-4o-mini", messages=[...])
```

### Knowledge Base
French regional knowledge: 8 regions × (mountains + languages + general) = 24 markdown files

### Run
```bash
cd "week5/community-contributions/day 4 no_langchain"
echo "OPENAI_API_KEY=..." > .env
jupyter notebook RAG_chat_no_LangChain.ipynb
```

---

## 6. SafeHire AI Risk Advisor — Domain-Specific Decision Support

**Author:** `winniekariuki`  
**Type:** Nanny hiring risk assessment with structured profiles  
**Stack:** LangChain, Chroma, OpenAI, Gradio

### Why It's Exceptional
**Practical domain application** — not a generic Q&A bot but a decision-support tool with:
- **Curated knowledge base**: Compliance, red flags, hiring best practices, reference verification, trust scores, child safety
- **Structured nanny profiles** (JSON): Injected into prompt when queried by name
- **Focused retrieval**: Top-3 chunks, gpt-4o-mini generation

### Data Files
- `knowledge-base/safehire_knowledge.md` — Guidelines
- `profiles/nanny_profiles.json` — Structured candidate profiles

### Run
```bash
cd week5/community-contributions/winniekariuki
pip install langchain-community langchain-text-splitters langchain-openai langchain-chroma chromadb gradio python-dotenv
echo "OPENAI_API_KEY=..." > .env
jupyter notebook week5_exercise.ipynb
```

---

## 7. Company Website RAG Assistant — Clean Reference Implementation

**Author:** `cwait`  
**Type:** Company Q&A bot using only local knowledge base  
**Stack:** LangChain, ChromaDB, HuggingFace embeddings (all-MiniLM-L6-v2), Gradio

### Why It's Exceptional
**Clean, minimal, reproducible** — excellent reference for standard RAG pattern:
- No API key for embeddings (local HuggingFace model)
- Persisted ChromaDB (`company_chroma_db/`)
- Configurable rebuild flag (`REBUILD_DB = True`)
- Clear separation: ingest → chunk → embed → store → chat

### Tech Choices
| Component | Choice | Rationale |
|-----------|--------|-----------|
| Embeddings | `all-MiniLM-L6-v2` | Fast, local, no API key |
| Chunking | 1000/200 overlap | Balanced context |
| LLM | gpt-4.1-nano | Cost-effective |
| Loader | `DirectoryLoader` + `TextLoader` | Simple markdown ingestion |

### Run
```bash
cd week5/community-contributions/cwait
jupyter notebook week5_igniters_cwait.ipynb
# Set REBUILD_DB = True in Config cell on first run
```

---

## 8. AI Knowledge RAG Assistant — Educational Focus

**Author:** `Wanjiru-Week-5`  
**Type:** Learning assistant for AI concepts (RAG, embeddings, transformers, vector DBs)  
**Stack:** LangChain, HuggingFace embeddings, Chroma, Gradio

### Why It's Exceptional
**Meta-educational** — a RAG system that teaches you *about* RAG. Includes companion documentation:
- `docs/rag.md`
- `docs/embeddings.md`
- `docs/transformers.md`
- `docs/vectordb.md`

### Run
```bash
cd week5/community-contributions/Wanjiru-Week-5
jupyter notebook week_5_exercise.ipynb
```

---

## Comparison Matrix

| Project | Complexity | Novelty | Production-Ready | Learning Value |
|---------|------------|---------|------------------|----------------|
| Agentic RAG Challenge | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Personal Knowledge Worker | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| Recipe Tailor | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| Personal Knowledge Assistant | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| RAG Without LangChain | ⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐ | ⭐⭐⭐⭐⭐ |
| SafeHire Advisor | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ |
| Company Website RAG | ⭐⭐ | ⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| AI Knowledge Assistant | ⭐⭐ | ⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |

---

## Recommendations by Goal

| Goal | Start With |
|------|------------|
| **Learn agentic patterns** | Agentic RAG Challenge |
| **Build personal knowledge base** | Personal Knowledge Worker |
| **Understand RAG internals** | RAG Without LangChain |
| **Deploy a clean RAG quickly** | Company Website RAG |
| **Domain-specific assistant** | Recipe Tailor or SafeHire |
| **Cloud integration (Gmail/Drive/Outlook)** | Personal Knowledge Assistant |
| **Teach AI concepts** | AI Knowledge Assistant |

---

## Common Patterns Across Top Projects

1. **ChromaDB** — Universal vector store choice
2. **Gradio** — Standard for chat UIs
3. **Markdown knowledge bases** — Preferred over raw formats
4. **HuggingFace embeddings** — Popular for local, free embeddings
5. **Notebook-driven development** — Iterative exploration → production script
6. **`.env` for secrets** — Consistent config pattern
7. **Modular structure** — Separation of ingestion, retrieval, generation, UI

---

## Notable Mentions

- **`week5_jom`** — Exercise notebook with clear structure
- **`Stephen`** — Week 5 exercise solution
- **`yemi_gabriel`** — `study_buddy.py` + notebook
- **`Cosmus`** — Week 5 exercise notebook
- **`Collins`** — Pharma knowledge base (drugs + company overview)

---

*Generated from analysis of 30+ community submissions in `llm_engineering/week5/community-contributions/`*