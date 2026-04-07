# Release Checklist

This document tracks what is already done for the browser-only release and what still needs to be finished before publishing.

## Goal

Publish a LinkedIn-ready, browser-only MVP that:

- clearly shows `BCF -> structured wiki`
- demonstrates multi-project workflows
- shows smart BCF batching
- supports backup and restore without a backend
- is easy to adapt later for a real BIM team workflow

## Done

### Product

- Browser-only app flow is in place.
- `Try demo` action is available in the UI.
- Sample workspace is available through `demo/demo-backup.json`.
- Full backup and restore works without a server.
- Empty state explains what to upload and what the current limits are.
- Multi-project and BCF batching are visible in the app.

### Repo

- `README.md` exists.
- `LICENSE` exists.
- `.gitignore` exists.
- Demo backup data exists.

### Architecture

- BCF discipline rules are centralized in app config.
- Storage uses an adapter layer instead of direct calls everywhere.
- Backup payloads are versioned.
- Backup import has a migration normalization step.

## Must Finish Before Publish

### 1. Deploy

- Set up GitHub Pages or Vercel.
- Verify the app loads as a static site.
- Verify `demo/demo-backup.json` loads correctly in deployed mode.

### 2. README polish

- Add a `How it works` section.
- Add 3-5 screenshots or 1 short GIF.
- Add a short `Quick start` section.
- Add a short `Limitations` section for browser-only scope.

### 3. GitHub product polish

- Add issue templates:
  - bug report
  - feature request
  - customization request
- Optionally add a small pull request template.

### 4. Final verification

- Test `Try demo`.
- Test `Load sample workspace`.
- Test `Backup all` and `Restore`.
- Test project switching after ingest.
- Test one large BCF with batching.
- Test one small BCF without batching.

## Nice To Finish Before Publish

- Move screenshots into a dedicated `docs/` or `assets/` folder.
- Add a short demo dataset description to the README.
- Replace any broken text encoding in UI copy.
- Add a footer link to roadmap/customization notes.

## Can Wait Until After Publish

- FastAPI backend
- auth
- shared editing
- git-backed markdown storage
- PDF image extraction
- XLSX formula parsing
- large-file backend ingestion

## Suggested Publish Order

1. Run final browser checks locally.
2. Capture screenshots or GIF.
3. Update README with visuals and `How it works`.
4. Push to GitHub.
5. Deploy to GitHub Pages or Vercel.
6. Test the public link.
7. Publish LinkedIn post.

## LinkedIn Message Check

Before posting, make sure the repo and demo clearly communicate these points in under 30 seconds:

- This is not just a file viewer.
- It converts BCF into a structured wiki.
- It supports multi-project workflows.
- It batches large BCFs by discipline.
- It supports backup and restore.
- It is browser-only today but ready to customize further.
