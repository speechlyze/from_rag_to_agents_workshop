# From RAG to Agents Workshop

**Build a complete RAG pipeline and agentic system with Oracle AI Database, OpenAI, and the Agents SDK**

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/YOUR-ORG/from-rag-to-agents-workshop)

---

## What You Will Build

Starting from raw data, you will construct a **Research Paper Assistant** — a multi-agent system that retrieves, reasons over, and discusses 1,000 ArXiv papers stored in Oracle AI Database. Along the way you'll implement five retrieval strategies, build an end-to-end RAG pipeline, wrap retrieval as agent tools, compose a multi-agent orchestration system, and finish with persistent session memory backed by Oracle.

## Workshop Parts

| Part | Topic | Guide |
|---|---|---|
| 1 | Oracle AI Database setup and connection | [Part 1 Guide](docs/part-1-oracle-setup.md) |
| 2 | Data loading and embedding generation | [Part 2 Guide](docs/part-2-data-loading.md) |
| 3 | Database table setup and data ingestion | [Part 3 Guide](docs/part-3-table-setup.md) |
| 4 | Retrieval mechanisms (keyword, vector, hybrid, graph) | [Part 4 Guide](docs/part-4-retrieval.md) |
| 5 | Building a RAG pipeline | [Part 5 Guide](docs/part-5-rag-pipeline.md) |
| 6 | AI agents — basics and tools | [Part 6 Guide](docs/part-6-agents-basics.md) |
| 7 | Agent orchestration and chat system | [Part 7 Guide](docs/part-7-orchestration.md) |
| 8 | Session memory with Oracle AI Database | [Part 8 Guide](docs/part-8-session-memory.md) |

> **[TODO Checklist](docs/TODO-checklist.md)** — all 8 tasks at a glance with links to their guide sections.

## Getting Started

### Option A: GitHub Codespaces (recommended for the workshop)

1. Click the **Open in GitHub Codespaces** badge above
2. Wait for the environment to build (~3-5 minutes)

   ![Codespace startup](images/codespace_startup.png)

3. Once the terminal prompt appears, start Oracle AI Database:

   > **Tip:** If your browser prompts you to allow clipboard pasting, click **Allow** so you can paste commands into the terminal.

   ```bash
   docker compose -f .devcontainer/docker-compose.yml up -d oracle
   ```

   ![Oracle getting pulled](images/oracle_getting_pulled.png)

4. Wait for Oracle to become healthy (~60-90 seconds), then verify:
   ```bash
   docker ps
   ```
   You should see `(healthy)` in the STATUS column for the `oracle-free` container.

   ![Oracle ready](images/oracle_ready.png)

5. Confirm the Python connection works:
   ```bash
   python3 -c "import oracledb; c = oracledb.connect(user='VECTOR', password='VectorPwd_2025', dsn='localhost:1521/FREEPDB1'); print('Connected. Oracle version:', c.version); c.close()"
   ```

   ![Database ready](images/database_ready.png)

6. Open [`workshop/notebook_student.ipynb`](workshop/notebook_student.ipynb) in the file explorer
7. Select the **From RAG to Agents Workshop** kernel from the top-right kernel picker
8. Follow the notebook cells top to bottom, using the part guides in `docs/` when you hit a TODO

You will need:
- A GitHub account (free)
- An OpenAI API key — needed from Part 5 onwards

> **Note:** On subsequent Codespace opens, Oracle should start automatically via `postStartCommand`. If you ever see a connection error in the notebook, run step 3 above again from the terminal.

### Option B: Local development

```bash
git clone https://github.com/YOUR-ORG/from-rag-to-agents-workshop
cd from-rag-to-agents-workshop

# Start Oracle AI Database
docker compose -f .devcontainer/docker-compose.yml up -d oracle

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
jupyter lab workshop/notebook_student.ipynb
```

Wait approximately 2 minutes for Oracle to initialise before running notebook cells.

## Workshop Files

```
from-rag-to-agents-workshop/
├── .devcontainer/
│   ├── devcontainer.json       Codespaces configuration
│   ├── docker-compose.yml      Oracle AI Database container
│   ├── setup_build.sh          Dependency installation and kernel registration
│   ├── setup_runtime.sh        Oracle startup and vector memory configuration
│   ├── start_oracle.sh         Oracle health check on Codespace restart
│   └── oracle-init/
│       └── 01_vector_memory.sql  Vector memory pool initialisation
├── workshop/
│   ├── notebook_student.ipynb    Your working notebook (contains TODO gaps)
│   └── notebook_complete.ipynb   Complete reference (do not open until done)
├── docs/
│   ├── part-1-oracle-setup.md
│   ├── part-2-data-loading.md
│   ├── part-3-table-setup.md
│   ├── part-4-retrieval.md
│   ├── part-5-rag-pipeline.md
│   ├── part-6-agents-basics.md
│   ├── part-7-orchestration.md
│   ├── part-8-session-memory.md
│   └── TODO-checklist.md
├── images/
├── requirements.txt
└── README.md
```

## Stack

- Oracle AI Database via `gvenzl/oracle-free:23-slim`
- `sentence-transformers` — local embedding model (nomic-embed-text-v1.5, 768-dim), no API key needed
- `oracledb` — Python Oracle driver
- `OpenAI API` — LLM generation (GPT-4o)
- `openai-agents` — Agent SDK (Agent, Runner, function_tool, orchestration)

## Where to Next?

- **[Oracle AI Developer Hub](https://github.com/oracle-devrel/oracle-ai-developer-hub)** — More technical assets, samples, and projects with Oracle AI
- **[Oracle Developer Resource](https://www.oracle.com/developer/)** — Documentation, tools, and community for Oracle developers
- **[OpenAI Agents SDK Documentation](https://openai.github.io/openai-agents-python/)** — Full reference for the Agent SDK used in Parts 6-8

---

Built for the Oracle AI Developer Experience team.
