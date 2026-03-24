# Workshop TODO Checklist

8 hands-on tasks across Parts 1–8. Complete them in order — each builds on the last.

Part 2 (data loading) is pre-built — just run the cells to load and embed the data.

---

### Part 1 — Oracle Setup ([Guide](part-1-oracle-setup.md))

1. Implement `connect_to_oracle` with retry logic (TODO 1)

### Part 2 — Data Loading ([Guide](part-2-data-loading.md))

No TODOs — pre-built. Read through to understand the data pipeline.

### Part 3 — Table Setup ([Guide](part-3-table-setup.md))

2. Implement `create_research_papers_table` with safe drops (TODO 2)

### Part 4 — Retrieval ([Guide](part-4-retrieval.md))

3. Implement `vector_search_research_papers` (TODO 3)
4. Implement `hybrid_search_research_papers_pre_filter` (TODO 4)

### Part 5 — RAG Pipeline ([Guide](part-5-rag-pipeline.md))

5. Implement `research_paper_assistant_rag_pipeline` (TODO 5)

### Part 6 — Agents & Tools ([Guide](part-6-agents-basics.md))

6. Implement `get_research_papers` tool with `@function_tool` (TODO 6)

### Part 7 — Orchestration ([Guide](part-7-orchestration.md))

7. Implement the orchestrator agent with `agent.as_tool()` (TODO 7)

### Part 8 — Session Memory ([Guide](part-8-session-memory.md))

8. Implement `OracleSession` class (TODO 8)
