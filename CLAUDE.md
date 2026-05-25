# CLAUDE.md

## Project: Multi-Source Data Pipeline + AI Analyst

Python data pipeline pulling from multiple APIs, processing with pandas/polars/numpy, analyzed by LangChain + LangGraph agent.

## Tech Stack

- **Python 3.11+**
- **Data:** polars (primary), pandas (complex transforms), numpy (stats)
- **Storage:** DuckDB
- **AI:** LangChain, LangGraph, Claude API (claude-sonnet-4-6)
- **CLI:** Typer
- **Testing:** pytest

## Project Structure

```
src/
  fetchers/     # one file per data source, returns polars DataFrame
  pipeline/     # clean.py, transform.py, store.py
  analytics/    # numpy-based computations
  agent/        # langchain chains, langgraph agent
data/
  raw/          # gitignored
  processed/    # gitignored
tests/
notebooks/      # exploration only, never import from src
```

## Conventions

- Fetchers return `pl.DataFrame` (polars), never raw dicts
- All column names: `snake_case`
- Store cleaned data in DuckDB before any AI layer touches it
- LangGraph nodes: pure functions, no side effects inside node
- Never hardcode API keys — always read from env
- One data source per fetcher file

## What NOT to do

- No pandas in fetchers (polars only)
- No LangChain calls before data is cleaned and stored
- No notebooks in src/
- No global state in agent nodes

## Running

```bash
python -m src.cli fetch       # pull all sources
python -m src.cli analyze     # run agent
python -m src.cli ask "..."   # natural language query
python -m src.cli report      # generate digest
```

## Testing

```bash
pytest tests/ -v
```
