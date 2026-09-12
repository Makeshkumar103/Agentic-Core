# Week 4 Community Contributions - Best Projects

This document highlights the most outstanding projects from the Week 4 community contributions for the LLM Engineering course. Week 4 focuses on **code generation, translation, documentation, testing, and developer tools**. Projects are evaluated on **completeness**, **code quality**, **innovation**, **practical utility**, and **documentation**.

---

## 🏆 Top Tier - Production-Ready Applications

### 1. **AI Stock Trading & Sharia Compliance Platform** — *ai_stock_trading*
**Path:** `ai_stock_trading/`

**Description:** A comprehensive **Streamlit-based** web application providing AI-powered stock analysis with Islamic Sharia compliance assessment for USA and Egyptian markets.

**Key Features:**
- **Multi-market support**: USA (75+ stocks) and Egypt (50+ stocks) with proper currency handling (USD/EGP)
- **Real-time data** via yfinance with robust error handling
- **Advanced technical indicators**: RSI, MACD, Bollinger Bands, Moving Averages
- **Risk metrics**: Volatility, Sharpe ratio, maximum drawdown, multi-timeframe returns
- **AI-powered trading decisions**: GPT-4o-mini with senior analyst persona (15+ years exp)
- **Sharia compliance**: AAOIFI standards screening (debt-to-assets < 33%, interest income < 5%), 50+ prohibited categories
- **Natural language chat interface** with context awareness
- **Interactive dashboards** with Plotly charts (price, volume, risk, trading signals)
- **Professional KPI dashboard** with real-time metrics

**Architecture:**
```
tools/
  ├── fetching.py         — Multi-market stock data + currency formatting
  ├── analysis.py         — Technical indicators, risk metrics, performance
  ├── trading_decisions.py — Senior analyst AI with structured JSON output
  ├── sharia_compliance.py — Islamic finance screening (AAOIFI/DSN)
  └── charting.py         — Plotly interactive visualizations
core/
  ├── data_service.py     — Caching & data orchestration
  └── ai_assistant.py     — Chat interface logic
components/
  └── chat_interface.py   — Gradio-style chat component
main_app.py               — Streamlit entry point (3 pages: Home, Chat, Dashboard)
```

**Why it stands out:** Professional-grade financial application, unique Sharia compliance niche, modular tool-based architecture, comprehensive documentation with MCP integration roadmap, real-world utility.

---

### 2. **VRP Code-Generation Benchmark** — *makinda*
**Path:** `makinda/`

**Description:** Benchmarks LLM providers (OpenRouter, OpenAI, Ollama, Gemini) on a **Nairobi grocery delivery Vehicle Routing Problem** — each model generates Python code to solve VRP instances with cost minimization.

**Key Features:**
- **Business scenario**: 3 depots, 12 vehicles, 20–200 orders with lat/lon, weight, delivery windows, late penalties
- **Traffic modeling**: 1.0 off-peak, 1.4 during rush hours (7–9, 16–19)
- **Synthetic data generation**: Random Nairobi coordinates, weights, time windows — not hardcoded
- **Composite scoring**: 50% cost, 20% feasibility, 15% runtime, 10% code stability, 5% token efficiency
- **Sandbox execution**: Validates `vrp_result.json`, checks hard constraints (capacity, time windows)
- **Adversarial testing**: Tight time windows + high order counts to separate weak/strong models
- **Route visualization** via matplotlib
- **Gradio UI** with provider/model selection, order count, window tightness, timeout

**Structure:**
```
data_generator.py   # Synthetic Nairobi orders, depots, vehicles
problem_spec.py     # Prompt + contract (vrp_result.json schema)
evaluator.py        # Sandbox execution, validation, cost calculation
scoring.py          # Composite score breakdown
route_plot.py       # Optional matplotlib route visualization
vrp_benchmark.py    # LLM client + run_benchmark()
notebook.ipynb      # Gradio UI
```

**Why it stands out:** Rigorous benchmarking methodology, real-world optimization problem, synthetic data avoids memorization, business-centric reporting, multi-provider comparison framework.

---

### 3. **Python C Extension Generator** — *c_extension_generator/python_c_ext_generator.ipynb*
**Path:** `c_extension_generator/`

**Description:** Uses frontier models (GPT-4o/GPT-5) to generate **high-performance Python C extensions** from Python code — complete with C code, `setup.py`, and usage examples with benchmarks.

**Key Features:**
- **Structured output** via Pydantic: `c_code`, `setup.py`, `usage_example.py`
- **Automatic compilation & benchmarking**: Compiles `.c` → `.so`, runs timing comparison vs original Python
- **Gradio interface** for interactive generation
- **Example modules**: `calculate_pi`, `zz_my_module`, `python_hard` (included in repo)
- **System-aware**: Tailors compilation commands to user's toolchain
- **Performance focus**: Targets CPU-bound Python bottlenecks

**Why it stands out:** Unique niche (C extensions), end-to-end pipeline (generate → compile → benchmark), practical performance engineering, includes working examples.

---

### 4. **Multi-LLM Python to C++ Translator** — *python_to_cpp_code_translator/python_code_translator.ipynb*
**Path:** `python_to_cpp_code_translator/`

**Description:** Comprehensive code translation system comparing **GPT-4o, Claude 3.5 Sonnet, Gemini 2.0 Flash** with automatic compilation testing and quality analysis.

**Key Features:**
- **3 LLM providers**: OpenAI, Anthropic, Google
- **Automatic C++ compilation** via g++ with error capture
- **Execution testing** of compiled binaries
- **Quality analysis**: Code metrics, performance benchmarking
- **Interactive examples** with provided test cases (sorting, fibonacci, calculator)
- **Comprehensive test suite** with pytest
- **Gradio interface** for translation + comparison

**Structure:**
```
python_code_translator.ipynb  — Full pipeline notebook (1280+ lines)
examples/
  ├── calculator.py
  ├── fibonacci.py
  └── sorting_algorithms.py
```

**Why it stands out:** Multi-model comparison, compilation verification, quality metrics, practical translation workflow.

---

### 5. **Python-to-Multi-Language Porting** — *chrys/port_python_to_languages.ipynb*
**Path:** `chrys/`

**Description:** Ports Python code to **C++, C, Rust, Java, JavaScript** with system-aware prompts (detects user's OS, Rust toolchain) and **execution time comparison** vs original Python.

**Key Features:**
- **5 target languages** with tailored prompts
- **System info injection**: OS, CPU, Rust toolchain version → model generates correct compile/run commands
- **Benchmarking**: Runs original Python + each port, shows speedup ratios
- **Gradio UI** with model selection (OpenAI, OpenRouter, Ollama)
- **Language-specific prompt engineering** (ownership in Rust, memory in C/C++)

**Why it stands out:** Broad language coverage, system-aware generation, empirical performance comparison, practical for polyglot developers.

---

## 🥈 High Quality - Developer Tools

### 6. **AutoDoc - Code Documenter** — *irytck/auto_doc/*
**Path:** `irytck/auto_doc/`

**Description:** CLI tool that generates comprehensive documentation for Python code using LLMs.

**Key Features:**
- **Modular design**: `documenter.py` (core), `prompt.py` (templates), `main.py` (CLI)
- **Multi-provider support** via OpenRouter
- **Sample code included** for testing
- **Clean separation** of prompt engineering from execution

**Structure:**
```
documenter.py   — CodeDocumenter class with document_code()
prompt.py       — System/user prompt templates
main.py         — CLI entry point
sample_code.py  — Test input
```

**Why it stands out:** Clean architecture, focused on documentation generation, extensible prompt system.

---

### 7. **Docstring Generator (Multi-Provider)** — *adams-bolaji/docstring_generator.ipynb*
**Path:** `adams-bolaji/`

**Description:** Gradio app for generating Python docstrings with **7 provider support**: OpenAI, Anthropic, Gemini, Grok, Groq, Ollama, OpenRouter.

**Key Features:**
- **Model comparison**: Side-by-side docstring quality across providers
- **Gradio UI** with `gr.Code` input, themed styling
- **Structured prompts** for consistent docstring format (Google/NumPy/Sphinx styles)
- **Multi-model dropdown** with API key status indicators

**Why it stands out:** Broadest provider support, comparison-focused, clean Gradio UI.

---

### 8. **Unit Test Generator** — *salah/unit-tests-generator/*
**Path:** `salah/unit-tests-generator/`

**Description:** Gradio app generating **pytest unit tests** with streaming output via OpenRouter (free Llama 3.1).

**Key Features:**
- **Streaming output** for responsive UX
- **Comprehensive test coverage**: Happy paths, edge cases, error handling
- **Simple architecture**: `test_generator.py` + `app.py` (2 files)
- **Free model** via OpenRouter (meta-llama/llama-3.1-8b-instruct:free)

**Structure:**
```
test_generator.py  — generate_tests() with streaming
app.py             — Gradio interface
main.py            — Alternative entry point
.env.example       — OPENROUTER_API_KEY
```

**Why it stands out:** Streaming UX, focused scope, free model access, minimal dependencies.

---

### 9. **Code Explainer (One-Page)** — *code_explainer/code_to_explanation.ipynb*
**Path:** `code_explainer/`

**Description:** Converts code into structured **one-page Markdown explanations**: Summary, Control Flow, Data Flow.

**Key Features:**
- **Strict output format** enforced via system prompt (Summary → Control Flow → Data Flow only)
- **OpenRouter default** with model selection
- **Gradio UI** with `gr.Code` input
- **Low temperature** (0.2) for consistent technical writing

**Output Format:**
```markdown
## Summary
One paragraph: purpose, main idea, algorithm/pattern

## Control Flow
- Entry points, conditionals, loops, key calls

## Data Flow
- Inputs, outputs, variables, data movement
```

**Why it stands out:** Enforced structure, clear technical writing focus, minimal but effective.

---

### 10. **AutoTrader Code Generator** — *autotrader_code_generator/*
**Path:** `autotrader_code_generator/`

**Description:** Gemini-driven autonomous **equities trading bot generator** for simulated market APIs.

**Key Features:**
- **Gemini API** via `google-genai` SDK
- **API spec driven**: Reads `api_spec.json` for simulated exchange endpoints
- **Generates complete trading bot** with risk management, position sizing
- **Gradio interface** for parameter configuration
- **Outputs runnable Python bot** (`generated_trading_bot.py`)

**Structure:**
```
Auto_trader_script_generator.ipynb  — Main notebook
gemini_trading_code_generator.py    — Core generation logic
api_spec.json                       — Simulated exchange API spec
generated_trading_bot.py            — Example output
```

**Why it stands out:** Domain-specific (algo trading), spec-driven generation, complete runnable output.

---

## 🎯 Notable Mentions - Creative & Specialized

| Project | Path | Highlight |
|---------|------|-----------|
| **AI App Builder** | `ai_app_builder/builder.ipynb` | LLM creates files/projects via tool calls, stores in projects/ |
| **Code Commentor** | `code_commentor.ipynb` | Multi-model code commenting with Gradio |
| **Code Documentation Generator** | `code_documentation_generator.ipynb` | Full project documentation from source |
| **Unit Test Generator v3** | `unit-test-generator-v3.ipynb` | Advanced test generation with benchmarks |
| **Python to Go Translator** | `week4_python_to_go.ipynb` | Single-language focus (Python→Go) |
| **Java Unit Test Generator** | `day5_java_unit_test_generator.ipynb` | Java-specific test generation |
| **Code Converter (13 langs)** | `Week4_Exercise_convert_between_thirteen_lang_coment_unit_test.ipynb` | Massive multi-language support |
| **Trading Floor Simulator** | `week4-exercise-pt-br-trading-floor-simulator.ipynb` | Portuguese-BR localized trading sim |
| **Prompt Cost Calculator** | `JamesDominiqueAI/prompt_cost_calculator.py` | Token cost estimation utility |

---

## 📊 Category Summary

| Category | Count | Examples |
|----------|-------|----------|
| **Code Translation/Conversion** | 12+ | Python→C++, Python→Rust/Go/Java/JS, 13-language converter |
| **Documentation Generation** | 8+ | Docstrings (multi-provider), AutoDoc, Code Explainer, Commentor |
| **Unit Test Generation** | 10+ | PyTest, Java tests, v3 with benchmarking |
| **Financial/Trading Apps** | 5+ | AI Stock Trading (Sharia), AutoTrader, Trading Floor Sim |
| **Code Explanation/Analysis** | 4+ | One-page explainer, Code to explanation, DocuPy |
| **C Extension/Performance** | 2+ | C extension generator, Code Accelerate |
| **Benchmarking/Evaluation** | 2+ | VRP benchmark, CynthiaOmovoIye unit test benchmark |
| **AI App Builders** | 2+ | AI App Builder, Code Generator |
| **Multi-Provider Support** | 15+ | Most projects support 3-7 providers (OpenAI, Anthropic, Gemini, Groq, Ollama, OpenRouter) |
| **Gradio UIs** | 20+ | Nearly all projects have Gradio interfaces |
| **Streamlit Apps** | 2+ | AI Stock Trading, possibly others |
| **Local LLM (Ollama)** | 10+ | Widely supported across projects |

---

## 💡 Recommendations for Future Contributors

1. **Follow the modular tool pattern** from `ai_stock_trading` — separate concerns (fetching, analysis, decisions, compliance, charting)
2. **Add compilation/execution verification** — like `python_to_cpp_code_translator` and `c_extension_generator` do
3. **Benchmark with synthetic data** — `makinda`'s approach avoids memorization and tests real reasoning
4. **Support multiple providers** — 7+ providers in `adams-bolaji` shows what's possible
5. **Enforce output structure** — `code_explainer`'s strict Markdown format ensures parseable results
6. **Consider niche domains** — Sharia compliance, VRP optimization, C extensions show creativity
7. **Stream outputs** — `salah/unit-tests-generator` demonstrates responsive UX with streaming
8. **Document with visuals** — `ai_stock_trading` README with screenshots is exemplary

---

## 🔗 Quick Access

| Project | Entry Point | Type |
|---------|-------------|------|
| AI Stock Trading (Sharia) | `ai_stock_trading/main_app.py` | Streamlit App |
| VRP Benchmark | `makinda/notebook.ipynb` | Gradio Notebook |
| Python C Extension Gen | `c_extension_generator/python_c_ext_generator.ipynb` | Notebook + Gradio |
| Python→C++ Translator | `python_to_cpp_code_translator/python_code_translator.ipynb` | Notebook |
| Python→Multi-Lang Port | `chrys/port_python_to_languages.ipynb` | Notebook + Gradio |
| AutoDoc CLI | `irytck/auto_doc/main.py` | CLI |
| Docstring Generator | `adams-bolaji/docstring_generator.ipynb` | Notebook + Gradio |
| Unit Test Generator | `salah/unit-tests-generator/app.py` | Gradio App |
| Code Explainer | `code_explainer/code_to_explanation.ipynb` | Notebook + Gradio |
| AutoTrader Generator | `autotrader_code_generator/Auto_trader_script_generator.ipynb` | Notebook |

---

*Generated from analysis of 201 community contributions in `llm_engineering/week4/community-contributions/`*