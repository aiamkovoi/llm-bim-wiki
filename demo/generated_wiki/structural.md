# Structural discipline

Source: infrastructure_project_A.bcf | Last updated: 2024-05-11 | Issues: 8

## Summary

7 closed, 1 open. Dominant issue type: clashes with MEP (3 of 8). Two recurring root cause clusters identified — see [patterns/overview].

## Open issues

| ID | Title | Priority | Assigned |
|----|-------|----------|----------|
| 005 | Slab opening OS-221 not aligned with architectural partitions | Normal | Structural Engineer |

**Risk:** Architectural drawing Rev C not yet coordinated. Structural review pending. Potential slab rework if not resolved before reinforcement.

## Closed issues

| ID | Type | Title | Root cause cluster | Closed |
|----|------|-------|--------------------|--------|
| 001 | Clash | STR-B-112 vs MEP-D-045 [gridline E-7] | STR/MEP coordination gap | 2024-03-12 |
| 002 | Clash | FND-P-023 vs CIV-DR-008 | Outdated reference data | 2024-03-20 |
| 003 | Info Req | STR wall C-4 fire rating missing | IFC export parameter loss | 2024-03-14 |
| 004 | Clash | STR-B-089 vs MEP-SP-012 [gridline E-9] | STR/MEP coordination gap | 2024-04-09 |
| 006 | Clash | RW-07 STR vs CIV mismatch | Outdated reference data | 2024-04-25 |
| 007 | Clash | MEP-CT-067 vs STR-C-018 | Missed coordination session | 2024-05-10 |
| 008 | Info Req | STR-SL-004 LOD insufficient Stage 3 | LOD requirement not communicated | 2024-05-11 |

## Root cause patterns

→ **STR/MEP coordination gap** (issues 001, 004): two beam-level clashes in zone E (gridlines E-7 and E-9). Same coordinator, different sessions. ⚠ RECURRING PATTERN — see [patterns/overview].

→ **Outdated reference data** (issues 002, 006): civil discipline working from stale gridline/survey files. ⚠ RECURRING PATTERN — see [patterns/overview].

→ **IFC export data loss** (issue 003): fire rating parameter dropped on export. One occurrence — monitor on next export cycle.

→ **LOD communication gap** (issue 008): structural modeller not informed of Stage 3 requirements. Process issue, not model issue.
