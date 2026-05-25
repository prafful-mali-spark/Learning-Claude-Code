# Project Roadmap: Multi-Source Data Pipeline + AI Analyst

Living document. Update as we build.

---

## Phase 0: Claude Code Setup ✅ IN PROGRESS

Goal: Configure Claude Code for this project before writing any code.

- [x] CLAUDE.md — project rules, conventions, stack
- [x] .gitignore
- [x] .claude/settings.json — MCP (GitHub), permissions, hooks
- [ ] Memory — save project context for future sessions
- [ ] Initial git commit + push to GitHub

Claude Code features: CLAUDE.md, settings.json, Memory, MCP

---

## Phase 1: Project Scaffold

Goal: Working Python project structure, dependencies installed, nothing broken.

- [ ] Create folder structure (src/, tests/, data/, notebooks/)
- [ ] pyproject.toml or requirements.txt with pinned versions
- [ ] .env.example (template without secrets)
- [ ] Verify imports work
- [ ] First real commit

Claude Code features: Plan Mode, TodoWrite

---

## Phase 2: Data Fetchers

Goal: 3+ live data sources returning clean polars DataFrames.

Sources (TBD — pick in Phase 1):
- [ ] Source 1 (e.g. crypto prices — CoinGecko free API)
- [ ] Source 2 (e.g. weather — Open-Meteo free API)
- [ ] Source 3 (e.g. HackerNews — free, no auth)

Each fetcher: one file, one function, returns `pl.DataFrame`.

Claude Code features: Subagents (build fetchers in parallel)

---

## Phase 3: Data Pipeline

Goal: Raw data → cleaned → transformed → stored in DuckDB.

- [ ] clean.py — nulls, types, deduplication
- [ ] transform.py — normalize, join sources, resample time series
- [ ] store.py — write to DuckDB
- [ ] NumPy analytics — correlation matrix, z-scores, moving averages

Claude Code features: TodoWrite (track each pipeline step)

---

## Phase 4: LangChain Layer

Goal: Natural language interface over stored data.

- [ ] Query chain — NL → SQL → DuckDB → answer
- [ ] Summary chain — data snapshot → insight paragraph
- [ ] Anomaly chain — detect unusual patterns

Claude Code features: Memory (store chain configs, prompt templates)

---

## Phase 5: LangGraph Agent

Goal: Autonomous multi-step analyst agent.

Agent flow:
```
fetch_node → clean_node → analyze_node → report_node
                                ↓
                        [anomaly detected?]
                                ↓
                        deep_dive_node
```

- [ ] Define nodes (pure functions)
- [ ] Define edges + conditional logic
- [ ] Test agent end-to-end

Claude Code features: Subagents (test different agent paths in parallel)

---

## Phase 6: CLI Interface

Goal: Clean CLI to operate the pipeline.

Commands:
- [ ] `fetch` — pull fresh data from all sources
- [ ] `analyze` — run LangGraph agent
- [ ] `ask "..."` — natural language query
- [ ] `report` — generate daily digest

Claude Code features: Custom Skills (/fetch, /analyze, /ask, /report)

---

## Phase 7: Hooks + Polish

Goal: Automate repetitive tasks via Claude Code hooks.

- [ ] Pre-commit hook — run pytest
- [ ] Session start hook — show last pipeline run status
- [ ] Post-fetch hook — log data freshness

Claude Code features: Hooks

---

## Claude Code Features Map

| Phase | Feature Learned |
|-------|----------------|
| 0 | CLAUDE.md, settings.json, Memory, MCP |
| 1 | Plan Mode, TodoWrite |
| 2 | Subagents (parallel) |
| 3 | TodoWrite |
| 4 | Memory |
| 5 | Subagents (testing) |
| 6 | Custom Skills |
| 7 | Hooks |
