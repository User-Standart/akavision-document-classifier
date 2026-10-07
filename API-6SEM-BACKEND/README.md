# API-6SEM-BACKEND

Backend of **AkaVision** — Technical Document Classifier, an integrated project between Fatec SJC and AKAER.

## Stack

- **Language:** Python
- **AI models:** local via Ollama (bge-m3 for embeddings, Llama 3.2 for answers), with no calls to external services (project constraint)
- **Database:** PostgreSQL with pgvector, via Docker Compose
- _Web framework to be confirmed and documented here once defined_

## Running locally

```bash
# 1. Clone the repository and open the backend folder
git clone https://github.com/User-Standart/API-6SEM.git
cd API-6SEM/API-6SEM-BACKEND

# 2. Create and activate a virtual environment
python -m venv .venv
source .venv/bin/activate      # Linux/Mac
.venv\Scripts\activate         # Windows

# 3. Install the dependencies
pip install -r requirements.txt

# 4. Set up the environment variables
cp .env.example .env
# edit .env with your machine's values

# 5. Start the database
docker compose up -d

# 6. Run the application
# (command to be defined once the framework is chosen)
```

## RAG Pipeline (EverySpec)

Scripts that download the EverySpec specifications, prepare the texts, generate the embeddings and answer questions citing the document and page.

| Step | Script |
|---|---|
| Download the PDFs | `baixar_everyspec.py` |
| Extract text per page | `extrair_texto.py` |
| Split into chunks and quality filter | `gerar_chunks.py` |
| Generate embeddings with local Ollama | `gerar_embeddings.py` |
| Import embeddings generated in Colab (`.npz`) | `importar_embeddings.py` |
| Vector search | `buscar.py` |
| Answer with source citations | `responder.py` |

The full step-by-step guide is in [docs/pipeline-rag.md](docs/pipeline-rag.md).

PDFs, extracted texts, chunks and the `.npz` file are kept out of Git. The `.npz` file is shared via Google Drive.

## Contribution flow

1. Create a branch from `develop`: `feature/task-name`
2. Commits and PR titles follow [Conventional Commits](https://www.conventionalcommits.org), in English: `feat:`, `fix:`, `docs:`, `chore:`, `test:`
3. Open the PR against `develop` — requires 1 approval, green CI and a validated title
4. Always merge with **Squash and merge**

## CI

The `Backend CI` workflow runs on every PR/push to `main` and `develop`: it installs the dependencies and runs lint (`ruff`).

## Links

- Main project: [API-6SEM](../README.md)
- Frontend: [API-6SEM-FRONTEND](../API-6SEM-FRONTEND)
