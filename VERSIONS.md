# FloatCore core pack — frozen lineage v3-12 → v3-17

Every hash below is the full md5 of that version's single shipped HTML file, as recorded in the
partnership's code-artifact MANIFEST (`goals/floatcore-onewheel-app/hidden_files/code-artifact-MANIFEST.md`,
hash block lines 522–531) and cross-checked in the Drive-verified backup pack run records
(Pack 90 / Pack 91 freeze checks, `~/workspace/backups/`). One reading note: the MANIFEST's per-version
rows are written at each version's emit and so still say "CANDIDATE" — settlement status below comes
from the Tier-4 bench records, which postdate the rows.

| Version | md5 (full) | Size | Status |
|---|---|---|---|
| v3-12 | `636c6cedf258b8790556ce725e08cfc4` | 3,428,771 B | Settled base of its era; superseded by v3-16 on 2026-11-26 |
| v3-13 | `f0d3e7bdc67941ce6f2a042afdbdbf37` | 3,457,393 B | Candidate — Tier 4 FAILED on Tony's 2026-11-24 board run (ladder rungs 2/3 never engaged live); never settled |
| v3-14 | `3f6f9779cf7123e800a99886d9a02fe4` | 3,489,830 B | Candidate — Tier 4 SPLIT at Tony's 2026-11-25 bench run (Bigfoot repeatable confirmed live; security ladder failed to engage); never settled |
| v3-15 | `d90553ae69a0517d35c85b4566785a17` | 3,792,197 B | Candidate — Tier 4 FAILED on 2026-11-26 (10 armings → 10× GUARD DATA STARVED); never settled |
| v3-16 | `9b48e3ca628f247781011525eb23a0c6` | 3,793,627 B | SETTLED — Tony's verdict, 2026-11-26 14:05; the previous settled build, superseded by v3-17 on 2026-11-27 |
| **v3-17** | **`16c758c9f13ff9c6db32b49f6b788526`** | **3,799,632 B** | **SETTLED — Tony's verdict, 2026-11-27 ~20:00. The current settled build.** |

## Settlement record (v3-17)

- Settled by Tony Kammerer on **2026-11-27** (~20:00, on the bench call: "Settle it and
  freeze the baseline"), after the Tier-4 bench run on his own board: Part A read exact on
  three reads (timeout 1000 ms, brake 0.00 A, signature 2099347128), rung 3 at the 3rd
  counted step with the final spoken line verbatim, manual Hold 15 A and the 25 A shudder
  dropped by the RELEASE button, DISARM mid-pulse and mid-repeat standing everything down,
  Focus mode proven, zero GUARD DATA STARVED across both exported deterrent logs.
- Source: `results-v3-17.md` in this repository (Tier 4 — RUN AND SETTLED section), with the
  run evidence in `bench-log-1-2026-11-27.txt` and `bench-log-2-2026-11-27.txt` beside it.
- The file in this repository (`floatcore-core-v3-17.html`) is byte-identical to the audited
  candidate Tony ran: its git blob SHA-1 matches the staged original, confirming md5
  `16c758c9f13ff9c6db32b49f6b788526`. v3-16 was re-verified byte-intact at the settle.

## Settlement record (v3-16)

- Settled by Tony Kammerer on **2026-11-26** (14:05, by options tap: "Settle v3-16 as the new base"),
  after the Tier-4 bench run on his own board: two full ladder climbs, rung 3 at exactly the 5th
  counted step both times, zero GUARD DATA STARVED across both session logs.
- Source: `goals/floatcore-onewheel-app/files/core-pack-v3-16/tier4-bench-record-2026-11-26.md`
  (settlement at lines 142–145, naming this md5).
- The file in this repository (`floatcore-core-v3-16.html`) was re-measured by md5sum at staging
  (2026-11-27) and matches the settled hash exactly.

## Sources per hash

- v3-12 — MANIFEST hash block line 522; row 62. Settled-base status: MANIFEST row 64
  ("v3-12, which remains the settled build"); Pack 90/91 freeze checks list it in the frozen set.
- v3-13 — MANIFEST hash block line 524; row 63. Tier-4 failure: partnership record (MEMORY.md).
- v3-14 — MANIFEST hash block line 526; row 64 (row carries the Tier-4 split verdict itself).
- v3-15 — MANIFEST hash block line 528; row 65. Tier-4 failure: MANIFEST row 66 catch-up note and
  `files/core-pack-v3-15/tier4-bench-record-2026-11-26.md`.
- v3-16 — MANIFEST hash block line 530; row 66. Settlement: Tier-4 bench record (above).
- v3-17 — the settled build's own record, `results-v3-17.md` in this repository (build record
  and the Tier 4 — RUN AND SETTLED section), with bench logs 1–2 beside it. Anchored in this
  repository at commit `2544ecd28cbc16dfbba03431d9251a97410161db`.

No hash in this manifest is carried as UNVERIFIED — all six were sourced from the records above.
Earlier frozen versions (v3-6 → v3-11) exist in the same MANIFEST hash block and in the backup
packs; this repo's lineage starts at v3-12, the first settled base of the security-ladder era.
