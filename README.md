# LLM-BIM-WIKI (Based on Karpathy)

<img width="1419" height="565" alt="image" src="https://github.com/user-attachments/assets/6ea42b7a-3a66-4d99-8db4-6eeedaa46e66" />

**🌍 [Try the Live Browser Demo](https://aiamkovoi.github.io/llm-bim-wiki/)**

Browser-based BIM wiki generator that turns BCF and supporting project documents into a structured, queryable knowledge base. 
Based on Andrej Karpathy's [LLM Wiki pattern](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f).

## Problem

BCF issues capture coordination decisions, but those decisions are hard to reuse later. Closed clashes, clarified requirements, and recurring root causes usually stay buried inside issue trackers, meeting notes, and PDFs. Teams lose context between coordination sessions and new projects start from zero.

## What This App Does

Standard LLM chat tools chunk and search raw documents. This app works differently: the LLM reads your documents and compiles them into a connected markdown wiki.

Instead of hunting through raw files every time, you build a persistent, updating knowledge base across the project lifecycle:
- **Project start:** Upload the BEP, standards, and initial BCF log.
- **During coordination:** Add meeting minutes, decisions, and new BCF issues.

Every upload adds to the base. New issues form connections, recurring clashes get flagged, and instructions become searchable. Ask the Wiki project-specific questions instead of digging through folders.

### Key Features
- **Browser-based parsing:** Reads BCF files directly and extracts issue data.
- **Interactive Graph:** Visualizes connections between documents and concepts using `vis.js`.
- **Automatic Grouping:** Organizes wiki pages into colored communities based on topics (no embeddings required).
- **File Hashing:** Skips parsing unchanged documents (via SHA-256) to save API tokens.
- **Local Workspaces:** Supports multiple projects stored locally with backup/restore functionality.

## Current scope & limitations

- Browser-only MVP (runs entirely client-side without a backend).
- Local `localStorage` for persistence (subject to browser quotas).
- Requires an OpenRouter or Anthropic API Key for Wiki generation.
- Not production-ready for large projects (best for demos or small pilots).

## Quick Start

### Running Locally (Recommended)
This is a zero-backend web application. While you can simply double-click `index.html`, we highly recommend running a local server to avoid browser CORS restrictions when loading local files:

**Using Python:**
```bash
python -m http.server 8000
```
Then navigate to `http://localhost:8000`

**Using Node.js:**
```bash
npx serve .
```

### Usage Steps
1. Open the app in your browser via `localhost`.
2. Run the built-in demo project or upload your own BCF, PDF, and Markdown files.
3. Build the wiki to compile your project knowledge.
4. Explore generated text pages and the visual Interactive Graph.
5. Export a backup or restore one of the demo datasets.

## Customization Points

- Discipline keyword rules are centralized in the app config.
- Topic type labels and wiki generation logic can be extended without changing the UI flow.
- Storage is routed through an adapter, so `localStorage` can later be replaced with git-backed or backend storage.
- Backup payloads include a version field for future migrations.

## Roadmap

- FastAPI ingestion for large files and richer parsers
- Git-backed markdown storage
- Shared access for project teams
- PDF with images and XLSX with formulas
- **Static Wiki Generator**: Auto-generating an `index.md` and community-specific files for offline agent crawling (Backend implementation).

## Project Files

- [index.html](./index.html) - single-file app and UI
- [PROJECT.md](./docs/PROJECT.md) - concept and architecture notes
- [AGENTS.md](./AGENTS.md) - wiki schema and ingest conventions
- [demo/demo-backup.json](./demo/demo-backup.json) - importable demo workspace

## Publishing

This repo can be deployed as a static site on GitHub Pages or Vercel.

## Reference Sources
The sample documents and workflows in this project are inspired by industry standards:
- [Example BCF Projects & Templates](https://helpcenter.bimcollab.com/en/articles/325099-example-projects-and-templates) (BIMcollab)
- [Example BIM Execution Plan (BEP)](https://www.building.govt.nz/assets/Uploads/projects-and-consents/building-information-modelling/nz-bim-handbook-appendix-fi-project-bim-execution-plan-example.pdf) (New Zealand BIM Handbook)
- [safishamsi/graphify](https://github.com/safishamsi/graphify) (Architecture Reference for Zero-backend Knowledge Graph)

## License

MIT. See [LICENSE](./LICENSE).
