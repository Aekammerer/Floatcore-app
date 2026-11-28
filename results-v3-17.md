# FloatCore v3-17 — combined build/audit record (STAGED CANDIDATE)

**Status: CANDIDATE (AMBER) — staged for Tony's check-off. NOT settled.
Settling is Tony's act after his Tier-4 bench run.**
Built 2026-11-27 under the engine-room protocol + Tony's standing
order (crews never idle; the version pipeline — a settle is a
starting gun). Base: settled v3-16 (Tony's verdict 2026-11-26
14:05), bytes untouched throughout.

- Artefact: `floatcore-core-v3-17.html` —
  md5 `16c758c9f13ff9c6db32b49f6b788526`, 3,799,632 bytes
  (v3-16 base 3,793,627; delta +6,005). Builder deterministic:
  two runs, identical md5 (builder's runs + auditor's two runs).
- 33 enumerated, count-asserted (×1) edits. Subtraction identity:
  v3-17 − 33 edits == v3-16 byte-for-byte; composed chain
  stripV315∘stripV316∘stripV317 == v3-14 byte-for-byte.
- Build record: `work-build/RESULTS.md`. Tier-2 audit:
  `work-audit/audit-v3-17-tier2.md`. Bench card (predictions
  P1–P6): `bench-card-v3-17.md`.

## What was built (the four queue items, nothing else)

1. **Rung-2 retune** (Tony's direction, v3-16 Tier-4 record §F3,
   14:02/14:03 — the steady 15 A hold graded TOO WEAK
   perceptually: felt at engagement, then unnoticeable through
   the carry handle; only shudder registers). The live guard
   (guard314) rung 2 now fires a **pulsed hold**: new
   `TorqueSession.startPulseHold()` drives the proven rung-3
   shudder pattern (4-on/1-off ticks, 80% duty) at the 15 A
   peak, with the heartbeat invariant enforced — the `_begin`
   re-emit excludes `pulsehold`, so no steady frame can
   overwrite the pattern (unit-proven: emissions exactly
   15,0,15,0…; sabotage removing the exclusion reproduces
   duplicate steady frames). Escalation shortened:
   `GUARD314_STEPS_TO_RUNG3` 5→3, provenance comment updated to
   Tony's 2026-11-26 direction. Every user-facing surface tied
   to the constants updated to truthful pulsed/three-step
   wording. The esc313/rung313 layer is byte-untouched —
   finding, from code + the bench deterrent log: the bench
   rung-2 was guard314's (log-verbatim ×2); rung313 produced
   zero lines and by construction cannot emit a rung-2 hold
   (its deps are speak/jerkMicro/shudder/log only).
2. **Dash Focus Mode** (spec `files/dash-focus-mode/spec-
   2026-11-26.md`): in the Dash view, one tap on the Focus
   control hides header, tab bar, and theme switcher
   completely; Dash fills the viewport; a slim semi-transparent
   handle pinned to the right edge restores everything in one
   tap (single class toggle — restore exact by construction);
   leaving the Dash tab exits focus. Scope: `sec-dash` only —
   the only section owning `#switcher` + `#stage` (auditor
   verified structurally); all other sections classified
   not-dashboard-style in the build RESULTS.
3. **Release-control fix — root-caused, not papered over.**
   Measured on frozen v3-16 bytes with real CDP mouse events:
   the first-run tour card's body (`pointer-events:auto`,
   floating over the scrolled Security section) sat in the
   `elementsFromPoint` stack above the RELEASE button and ate
   the tap — the handler (proven good: `disabled=false` during
   a hold, programmatic `.click()` releases instantly) never
   ran and no log line was written, matching the bench
   signature exactly ([01:24] hold, no release entry, DISARM
   at [01:41] — DISARM sits outside the card's band). Fix at
   the cause: card body `pointer-events:none`; only its
   Skip/Next buttons keep `auto`. Repro FAILS on v3-16, PASSES
   on v3-17 at the identical position; sabotage restoring
   `auto` fails again with the identical signature.
4. **Stale copy, new version only** (register
   `hidden_files/placeholder-register-2026-11-26.md`): B-1
   banner replaced — now states only record-supported facts
   (Tier-4 proven 2026-11-26; settled in v3-16; this build's
   retune + release fix await bench re-test). B-4 badge now
   reads `v3.17 CANDIDATE` — truthful for a staged build.
   Build asserts: old banner ×0, "v3.16 CANDIDATE" ×0,
   `"lights: verified"` ×0, final rung-2/rung-3 spoken lines
   ×1 each, byte-untouched (FINAL WORDING, Tony 2026-11-25).

## Tier 1 — builder suite + sabotage (on the shipped bytes)

Live shapes: trail1@40/@850, trail1ff, exact, chunk5 CLIMBED
(intake/guard 99/99, rung 3 at step 3); short1 STARVED (honesty
holds). Torque unit 7/7. Poll: parta 2/2 both bases; adapted
DEBUG ladder 10/10 (stepsAt3=3) with unmodified-expectation
control on v3-16 (9/10, P3 = stale-line conjunct, bisected).
Replay S1–S7 7/7 (control on v3-16 7/7 at step 5 — only delta
is the retune). Full page suite ALL PASS: in-page selftests
49/49, sec313 15/15, sec314 8/8 at both widths. Assembly
regression: control on v3-16 = 311 PASS / 10 FAIL (the v3-16
lane's exact result); v3-17 = 307/14 — the same 10 identity-
chain exceptions + 4 new literal-string conjuncts broken by
enumerated Q1 edits, each named with mechanism (auditor
verified in harness source: no functional check differs).
Focus harness 24/24 (360+412 × 2 themes). Release repro:
v3-16 FAIL → v3-17 ALL PASS incl. DISARM + micro regressions.
Sabotage: 6, all discriminating (carried sab1/sab3; new
sab-pulse, sab-steps, sab-release, sab-focus). Frozen
baselines re-md5'd at close: v3-16/v3-15/v3-14/v3-12 intact.

## Tier 2 — independent auditor (fresh agent, clean read)

**VERDICT: PASS-WITH-FINDINGS. No claim refuted.** The auditor
re-ran the full proof set from its own runs (build ×2 cmp-
identical; strip identity + composed chain PASS; release repro
FAIL on v3-16 / ALL PASS on v3-17; torque 7/7; focus 24/24;
assembly 311/10 control, 307/14 with all 4 new failures
verified as literal-string conjuncts) and added its own
sabotage (removing only the `pulsehold` heartbeat exclusion →
pattern-exact FAILS with duplicate steady frames — the
invariant is independently load-bearing). Findings, all minor:
F1 — RESULTS prose calls the tour card "position:fixed,
z-9990"; measured: fixed/z-9990 is the tour root, the card is
absolute (causal claim unaffected). F2 — full-suite probe-line
counts differ trivially between lanes (verdict ALL PASS both).
F3 — the audit brief cited a non-existent results path; the
auditor used the actual Tier-4 bench record. F4 — the focus
attempt-1 log's exact 16-check count is unverifiable because
the log was overwritten — exactly as the builder disclosed.
Builder disclosures (§8/§10) judged honest: the v3-15 builder
side-effect regenerated its own artefact byte-identically (md5
re-verified then and at close-out; no shipped byte changed).

## Tier 3 — record audit (coordinator, against the register)

Cross-checked against `placeholder-register-2026-11-26.md`,
the Tier-4 bench record, the promise ledger, and the MANIFEST:

- **B-1 — CLOSED in v3-17 (staged).** The stale "TIER-4 FAILED
  … BENCH RE-TEST PENDING" banner is gone from the new
  version's bytes (asserted ×0 by build + auditor); the
  replacement text claims only what the Tier-4 record supports.
- **B-4 — CLOSED in v3-17 (staged), both halves.** In-build:
  badge reads `v3.17 CANDIDATE`. Records half: the MANIFEST's
  v3-16 row now carries a dated catch-up note (SETTLED
  2026-11-26 14:05 after Tier-4 PASS), and a v3-17 row has
  been added in the same format (CANDIDATE, Tier-2
  PASS-WITH-FINDINGS, Tier 4 UNVERIFIED until Tony's run).
- **Walls advanced:** W-10 (rung-2 perceptibility) — ladder
  built (pulsed hold + 3-step escalation), awaiting Tony's
  bench feel grade (bench card P1/P2). W-12 (release defect)
  — root-caused and fixed, awaiting bench confirmation (P3;
  P4 covers the DISARM regression).
- **No new placeholders set by this build.** The Focus
  control/handle are working, harness-proven UI, not
  stand-ins; the new banner is truthful copy.
- **Still open, surfaced for Tony (deliberately NOT in this
  build's queue):** B-2 — the stale 4-stage ladder note
  (~line 3257) and its selftest assertion remain in v3-17's
  bytes, byte-untouched per the queue; the tab still
  contradicts itself on that one note. B-3 — the lock badge
  still says UNVERIFIED although the record proves the lock
  (G-4 + Tier-4 unlock integrity PASS); conservative
  direction, but stale. Both ride a future version's queue —
  Tony's call.
- Freeze check: v3-16 `9b48e3ca…`, v3-15 `d90553ae…`, v3-14
  `3f6f9779…`, v3-12 `636c6ced…` — all byte-intact at close.

## Tier 4 — Tony's bench (not run; predictions written in advance)

`bench-card-v3-17.md` carries P1–P6 with the exact log lines:
P1 rung-2 pulse felt through the carry handle as a continuing
pulse (vs v3-16's fade); P2 rung 3 at the 3rd counted step;
P3 manual Hold 15 A → RELEASE drops it immediately (log line
"TORQUE released (RELEASE button)"); P4 DISARM still stands
everything down mid-hold; P5 Focus hides all chrome on every
theme, side handle restores in one tap; P6 zero GUARD DATA
STARVED across the run.

## Tony's check-off consists of

1. This record + the Tier-2 audit (both in the pack folder).
2. His Tier-4 bench run per `bench-card-v3-17.md` (P1–P6).
3. His settle verdict. Until then v3-17 remains CANDIDATE and
   v3-16 remains the settled base. Nothing here settles,
   ships, or replaces anything on its own.

## Tier 4 — RUN AND SETTLED (Tony's bench, 2026-11-27 evening)

- Tony ran v3-17 on his S21 against his ADV board and delivered
  two exported deterrent logs, preserved beside this record:
  `bench-log-1-2026-11-27.txt` (md5 8eadcdd380d521c48e88623e391b93c4)
  and `bench-log-2-2026-11-27.txt` (md5 abf9ee32ca887251ddc08685faa08637).
  A third upload was byte-identical to log 1. The app-file copies
  Tony sent hash to 16c758c9... — the audited candidate bytes are
  what ran.
- Part A: PASS, three reads (02:36 / 09:28 / 10:17) — timeout
  1000 ms, brake 0.00 A, signature 2099347128, as predicted.
- P1: log-side PASS — rung-2 pulsed hold fired as predicted
  (06:25; again 09:57, 10:03, 10:05). No separate feel wording
  was given; Tony's settle verdict below is the grade.
- P2: PASS — steps 1 and 2 counted with no escalation; step 3
  fired the 25 A shudder and the final spoken line verbatim;
  timer release; guard re-armed after 5 s still.
- P3: PASS — manual Hold 15 A dropped by the RELEASE button
  (09:38, 09:39) and the 25 A shudder dropped by RELEASE
  (09:35, 09:41, 09:46); log line "TORQUE released (RELEASE
  button)" each time.
- P4: PASS — DISARM at 10:10 during an active rung-2 pulsed
  hold (steps counted) stood everything down mid-pattern;
  DISARM at 07:20 killed the rung-3 repeat cycle; nothing
  fired after either until re-armed.
- P5: PASS — Focus full-screen dash + right-edge restore
  handle, on Tony's photo and his word.
- P6: PASS — zero GUARD DATA STARVED across both logs.
- Bonus evidence in log 2: owner-cancel path x4; the 45 s
  rung-3 repeat cycle; persisted BOARD-REPORTED LOCK read and
  synced (07:29).
- **SETTLED by Tony, 2026-11-27 ~20:00 CST ("Settle it and
  freeze the baseline").** v3-17 is now a frozen baseline:
  floatcore-core-v3-17.html, 3,799,632 B, md5
  16c758c9f13ff9c6db32b49f6b788526. v3-16 re-verified
  byte-intact at settle (9b48e3ca628f247781011525eb23a0c6).
- v3-18 queue opened the same turn on Tony's order: B-2 + B-3.
