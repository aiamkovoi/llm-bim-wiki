# BCF Wiki — LLM-powered BIM knowledge base

**Pattern:** BCF issues → persistent LLM wiki → pattern intelligence
**Stack:** Python, BCF 2.1, Anthropic API, Obsidian-compatible markdown
**Author:** Alex Iamkovoi

---

## The problem

BIM coordination generates decisions. Clash resolved, RFI answered, LOD confirmed — then the knowledge disappears into a closed BCF issue or a Teams chat. The next project starts from zero. A new team member reads 400 pages instead of asking a question.

RAG doesn't fix this. It retrieves chunks from raw files at query time and synthesizes an answer from scratch every time. Nothing compounds.

## The idea (from Karpathy's LLM Wiki pattern)

Instead of indexing raw BCF files for retrieval, an LLM reads each issue and **compiles it into a persistent wiki** — updating discipline pages, flagging recurring root causes, building cross-references between issues. The wiki gets richer with every new BCF file ingested.

Ask "which clashes repeated across coordination sessions?" — the wiki already knows. It doesn't re-read the BCF. The synthesis is already there.

## Architecture

```
raw/                          ← BCF files, immutable
  infrastructure_project_A.bcf

wiki/                         ← LLM writes this layer
  index.md                    ← catalog + quick stats
  log.md                      ← append-only ingest history
  disciplines/
    structural.md             ← per-discipline summary + patterns
  issue-types/
    clash.md                  ← issue type analysis
  patterns/
    overview.md               ← recurring root causes, flagged

CLAUDE.md                     ← schema: conventions for the LLM agent
ingest.py                     ← BCF parser + Claude API call → wiki update
query.py                      ← ask questions against the compiled wiki
make_sample_bcf.py            ← generates realistic demo BCF
```

## Usage

```bash
# Generate sample BCF
python make_sample_bcf.py

# Ingest BCF → build/update wiki
python ingest.py raw/infrastructure_project_A.bcf

# Query the wiki
python query.py "Which issues repeated across coordination sessions?"
python query.py "What open issues remain and what is the risk?"
python query.py "What is the most common root cause?"
```

Set `ANTHROPIC_API_KEY` in your environment before running.

## Open BIM

Works with any BCF 2.1 source — BIMcollab, Solibri, Revit, Navisworks, OpenBIM tools.
The wiki format is plain markdown — open in Obsidian, VS Code, or any text editor.
No vendor lock-in. No proprietary database.

## What this is not

Not a replacement for BIMcollab or Solibri. Those tools manage the live coordination workflow.
This layer sits on top — it accumulates institutional knowledge from closed issues so the next project doesn't start from zero.

## LinkedIn demo

The interactive demo (index.html) shows the full flow:
1. Parse — 8 BCF issues from a realistic infrastructure project
2. Ingest — Claude builds 4 wiki pages, flags 2 recurring patterns
3. Query — ask questions in natural language, answers cite specific wiki pages
