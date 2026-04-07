# Clash issues

Source: infrastructure_project_A.bcf | Last updated: 2024-05-11 | Count: 6 clashes (of 8 total)

## Overview

6 clash issues, 5 closed, 1 open. All involve structural discipline as one party.

| Clash pair | Zone | Priority | Status |
|-----------|------|----------|--------|
| STR-B-112 vs MEP-D-045 | Gridline E-7 | Critical | Closed |
| FND-P-023 vs CIV-DR-008 | Foundation zone | Critical | Closed |
| STR-B-089 vs MEP-SP-012 | Gridline E-9 | Major | Closed |
| RW-07 STR vs CIV | Retaining wall zone | Major | Closed |
| MEP-CT-067 vs STR-C-018 | Zone E corridor | Critical | Closed |
| OS-221 vs ARQ partitions | Slab zone | Normal | **Open** |

## Resolution patterns

**Structural yields to MEP (2x):** Beam lowered (001), sprinkler rerouted (004). When structural element is primary load-bearing, MEP reroutes. When beam is secondary, beam adjusts.

**Civil model corrected (2x):** Issues 002 and 006 resolved by updating civil model to match structural. Both caused by outdated reference files — see [patterns/overview].

**MEP rerouted (1x):** Cable tray split around column (007). Column was non-negotiable.

## Severity distribution

- Critical: 3 (001, 002, 007)
- Major: 2 (004, 006)
- Normal: 1 (005, open)

All critical clashes closed. One normal-priority open.
