# ⚖️ ContractShield AI — Local & Private Contract Reviewer

> Analyze contracts offline using local LLMs (Mistral 7B, Llama 3.2, Phi-3) via Ollama.  
> Zero data egress. Finance & legal team safe.

![Python](https://img.shields.io/badge/Python-3.11+-blue) ![Ollama](https://img.shields.io/badge/Ollama-local-green) ![FastAPI](https://img.shields.io/badge/FastAPI-0.111-teal) ![License](https://img.shields.io/badge/license-MIT-purple)

---

## 📸 Demo

```
Upload PDF → JSON report with risk score, flagged clauses, liability caps
Side-by-side benchmark: Mistral 7B vs Llama 3.2 vs Phi-3
```

---

## 🗂️ Project Structure

```
contractshield/
├── backend/
│   ├── main.py            # FastAPI app
│   ├── analyzer.py        # Ollama + Instructor logic
│   ├── schemas.py         # Pydantic models
│   └── pdf_utils.py       # PDF text extraction
├── frontend/
│   └── index.html         # Single-file UI (no build step)
├── contracts/
│   └── demo_contract.txt  # Sample risky contract
├── requirements.txt
├── .env.example
└── README.md
```

---

## ⚡ Quick Start

### 1. Install Ollama
```bash
# macOS
brew install ollama

# Linux
curl -fsSL https://ollama.com/install.sh | sh

# Windows: download from https://ollama.com/download
```

### 2. Pull the 3 models
```bash
ollama pull mistral        # ~4.1 GB
ollama pull llama3.2       # ~2.0 GB
ollama pull phi3           # ~2.2 GB
```

### 3. Clone & install
```bash
git clone https://github.com/YOUR_USERNAME/contractshield-ai
cd contractshield-ai
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 4. Run
```bash
# Terminal 1 — make sure Ollama is running
ollama serve

# Terminal 2 — start the API
cd backend
uvicorn main:app --reload --port 8000

# Open browser
open frontend/index.html   # or just double-click it
```

---

## 🔌 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/analyze` | Analyze contract with one model |
| POST | `/benchmark` | Run all 3 models in parallel |
| GET | `/models` | List available Ollama models |
| GET | `/health` | Health check |

### Example
```bash
curl -X POST http://localhost:8000/benchmark \
  -F "file=@contracts/demo_contract.txt"
```

---

## 📦 Requirements

- Python 3.11+
- Ollama (running locally)
- ~9 GB disk for all 3 models
- 8 GB RAM minimum (16 GB recommended)

---

## 🔒 Privacy Guarantee

All processing happens on your machine. No data is sent to OpenAI, Anthropic, or any external API.

---

## 📄 License

MIT — use freely, keep it private.
