# Patterns overview

Source: infrastructure_project_A.bcf | Last updated: 2024-05-11

## ⚠ RECURRING PATTERN 1: STR/MEP coordination gap — zone E

**Issues:** 001 (2024-03-05), 004 (2024-04-02)
**Interval:** 28 days between occurrences
**Zone:** Gridlines E-7 and E-9 — adjacent columns, same corridor
**Assigned to:** MEP Coordinator (both times)

**Pattern:** Structural model updated, MEP model not synced before coordination session. Beam-level clashes detected reactively rather than prevented.

**Resolution history:** Beam lowered 150mm (001), sprinkler rerouted (004). Both required RFI.

**Recommended action:** Add zone E as standing agenda item in coordination sessions. Require MEP Coordinator to confirm model sync before each session in this zone.

---

## ⚠ RECURRING PATTERN 2: Outdated reference files — civil discipline

**Issues:** 002 (2024-03-08), 006 (2024-04-18)
**Interval:** 41 days between occurrences
**Disciplines:** STR vs CIV both times

**Pattern:** Civil team working from stale gridline/survey file. Issue 006 comment explicitly references issue 002 as same pattern.

**Resolution history:** Pile relocated 400mm (002), civil model corrected to match structural (006).

**Recommended action:** Establish single source of truth for gridline file — version-controlled, distributed by BIM Coordinator on each structural revision. Civil team confirms receipt before updating their model.

---

## Single-occurrence issues (monitor)

| Pattern | Issue | Risk of recurrence |
|---------|-------|--------------------|
| IFC export drops parameter | 003 | Medium — depends on export workflow |
| MEP model not updated after STR revision | 007 | Medium — process gap, not one-off |
| LOD requirements not communicated to modeller | 008 | High — no formal LOD distribution process confirmed |

---

## Timeline

```
Mar 05 — Issue 001: STR/MEP gap, zone E-7
Mar 08 — Issue 002: CIV outdated ref file
Mar 10 — Issue 003: IFC param loss
Apr 02 — Issue 004: STR/MEP gap, zone E-9  ← pattern 1 repeats
Apr 15 — Issue 005: OPEN
Apr 18 — Issue 006: CIV outdated ref file  ← pattern 2 repeats
May 03 — Issue 007: MEP not synced
May 07 — Issue 008: LOD gap
```
