# AGENTS.md — BCF Wiki schema

This file defines how the LLM agent maintains the wiki.
Keep it in the project root. Reference it at the start of each session.

## Wiki structure

```
wiki/
  index.md          — catalog of all pages, updated on every ingest
  log.md            — append-only ingest log, never edited
  disciplines/      — one file per discipline (structural.md, mep.md, civil.md...)
  issue-types/      — one file per BCF topic type (clash.md, information-required.md...)
  patterns/
    overview.md     — recurring root causes, cross-issue patterns
```

## Page conventions

### disciplines/{name}.md
Sections (required):
- ## Summary — one paragraph, key numbers
- ## Open issues — table: ID, title, priority, assigned
- ## Closed issues — table: ID, type, title, root cause cluster, closed date
- ## Root cause patterns — bulleted, reference [patterns/overview] for recurring ones

### issue-types/{name}.md
Sections:
- ## Overview — count, status breakdown
- Table of all issues of this type
- ## Resolution patterns — how this type typically gets resolved

### patterns/overview.md
- One H2 section per recurring pattern, prefixed ⚠ RECURRING PATTERN
- Include: issue IDs, dates, interval between occurrences, zone/discipline
- Include: resolution history and recommended action
- Separate section for single-occurrence issues to monitor

### index.md
- Links to all wiki pages with one-line descriptions
- Quick stats table: total issues, closed, open, patterns, critical closed

### log.md
- Append-only. Format: `## [YYYY-MM-DD HH:MM] ingest | {filename} | {n} issues`
- Never edit existing entries

## Ingest workflow

When processing a new BCF file:
1. Parse all issues
2. Read existing wiki pages via index.md
3. For each issue: identify discipline, type, root cause
4. Update relevant discipline page
5. Update relevant issue-type page
6. Check patterns/overview.md — does this root cause appear before? If yes, flag ⚠ RECURRING PATTERN
7. Update index.md
8. Append to log.md

## Rules

- Never invent information not in the BCF. Use [TODO] for gaps.
- Use actual issue IDs, element IDs, gridlines, and dates from the data.
- Cross-reference pages using markdown links: [page-name](path/to/page.md)
- One occurrence = note it. Two occurrences = ⚠ RECURRING PATTERN with recommendation.
- Human reviews wiki — LLM writes it. Flag uncertainty, don't hide it.

## Query workflow

When answering questions:
1. Read index.md to find relevant pages
2. Read those pages
3. Answer with citations: [page-name]
4. If answer is valuable (analysis, comparison, pattern discovery) — offer to file it back as a new wiki page
5. Never guess. If wiki doesn't contain the answer, say so.
