# ContractShield-AI-Local-Private-Contract-Reviewer
Analyze contracts offline using local LLMs (Mistral 7B, Llama 3.2, Phi-3) via Ollama. Zero data egress. Finance &amp; legal team safe.

📸 Demo
Upload PDF → JSON report with risk score, flagged clauses, liability caps
Side-by-side benchmark: Mistral 7B vs Llama 3.2 vs Phi-3

🗂️ Project Structure
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

⚡ Quick Start
1. Install Ollama
bash# macOS
brew install ollama

# Linux
curl -fsSL https://ollama.com/install.sh | sh

# Windows: download from https://ollama.com/download
2. Pull the 3 models
bashollama pull mistral        # ~4.1 GB
ollama pull llama3.2       # ~2.0 GB
ollama pull phi3           # ~2.2 GB
3. Clone & install
bashgit clone https://github.com/YOUR_USERNAME/contractshield-ai
cd contractshield-ai
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
4. Run
bash# Terminal 1 — make sure Ollama is running
ollama serve

# Terminal 2 — start the API
cd backend
uvicorn main:app --reload --port 8000

# Open browser
open frontend/index.html   # or just double-click it

🔌 API Endpoints
MethodEndpointDescriptionPOST/analyzeAnalyze contract with one modelPOST/benchmarkRun all 3 models in parallelGET/modelsList available Ollama modelsGET/healthHealth check
Example
bashcurl -X POST http://localhost:8000/benchmark \
  -F "file=@contracts/demo_contract.txt"

📦 Requirements

Python 3.11+
Ollama (running locally)
~9 GB disk for all 3 models
8 GB RAM minimum (16 GB recommended)


🔒 Privacy Guarantee
All processing happens on your machine. No data is sent to OpenAI, Anthropic, or any external API.

📄 License
MIT — use freely, keep it private.
