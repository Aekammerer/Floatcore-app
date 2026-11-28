# FloatCore v3-17 — Tier-4 Bench Card (Rung-2 Retune + Dash Focus + Release Fix)

Status: written 2026-11-27 by the v3-17 BUILD lane, BEFORE the
live run, per predict → capture → grade. It goes to Tony only
after a fresh Tier-2 audit of the assembled v3-17 candidate.
All three spoken lines are FINAL (Tony, 2026-11-25) and are
byte-untouched in this build.

Artefact: `floatcore-core-v3-17.html`, md5
`16c758c9f13ff9c6db32b49f6b788526` (3,799,632 B, assembled
candidate — CANDIDATE (AMBER), not settled). Base: the SETTLED
v3-16 (md5 `9b48e3ca628f247781011525eb23a0c6`). v3-17 − v3-16 is
33 enumerated edits, subtraction-proven byte-for-byte
(`work-build/RESULTS.md`).

## What changed since the settled v3-16

1. **Rung-2 retune (your 2026-11-26 direction, record §F3).** The
   steady 15 A hold you graded TOO WEAK — felt at engagement, then
   unnoticeable through the carry handle — is now a PULSED hold:
   the same 10 Hz, 4-on/1-off tick pattern you graded GOOD at
   rung 3, at the 15 A peak. Escalation is sooner: rung 3 now
   fires at the **3rd** counted step (was the 5th).
2. **Dash Focus Mode (your spec, 2026-11-26).** A Focus button in
   the dashboard selection row: one tap hides the app header, the
   tab bar AND the dashboard selection — nothing but the dashboard
   on screen. A slim handle on the right edge restores everything
   in one tap. Works on every dashboard theme; leaving the Dash
   tab exits focus.
3. **RELEASE fix (your owner-discovered defect, 2026-11-26).**
   Root cause found inside by reproduction on the frozen bytes:
   the first-run tour card sits fixed on screen and silently ate
   taps on any control scrolled beneath it — RELEASE included —
   leaving no trace in any log, while buttons tapped outside the
   card's band (Hold, DISARM) worked. The card body is now
   tap-transparent; only its own Skip/Next buttons take taps. The
   RELEASE handler itself was never broken.
4. **Stale copy corrected.** The Security ladder-watch badge no
   longer claims the 2026-11-26 Tier-4 failure / pending re-test
   (that re-test ran and v3-16 settled); it now states the feed
   fix is Tier-4 proven on the settled base and that THIS build's
   retune + release fix await their bench re-test. Version badge
   reads v3.17 CANDIDATE.

## Setup

1. Open the v3-17 candidate top-level from Downloads in Chrome on
   the S21 (never the Library/Spaces frame). VESC Tool fully
   closed first.
2. Connect. Part A read — prediction: gate OPEN, Timeout 1000 ms ·
   brake 0.00 A · signature 2099347128, stated once.
3. Lock the board (verify physically). One tap on **Set Tamper** —
   prediction: the whole guard arms; button reads "Tamper set —
   guarding".

## Predictions — grade each PASS / FAIL as it happens

- **P1 — Rung-2 pulse is FELT through the carry handle.** Climb to
  rung 2 (lift and hold the board tilted, footpads unpressed,
  ~2 s), then keep carrying it. Prediction: unlike v3-16's steady
  hold — which faded to unnoticeable once engaged — the pulsed
  hold keeps registering through the handle as a continuing
  pulse/jerk for as long as rung 2 lasts. Log line you should
  see: `GUARD RUNG 2 — carried: 15 A pulsed hold SENT
  (TorqueSession, shudder-pattern ticks at the 15 A peak) +
  spoken put-the-board-down warning.` Grade the feel in your
  words: stronger / right / too much — against your §F3 verdict.
- **P2 — Rung 3 at the 3rd step.** While at rung 2, take carrying
  steps. Prediction: steps 1 and 2 count with NO rung 3 (log:
  `GUARD STEP 1 of 3 counted…`, `GUARD STEP 2 of 3 counted…`); at
  the **3rd** counted step rung 3 fires — 25 A shudder + the
  rung-3 line. Log: `GUARD STEP 3 of 3 counted…` then
  `GUARD RUNG 3 — 3 steps: FULL SHUDDER SENT (25 A, TorqueSession,
  footpad-press abort armed) + stolen/tracked warning; repeats
  every 45 s until put-down or DISARM.`
- **P3 — RELEASE drops a manual hold immediately.** On the
  Security tab, tap **Hold 15 A** (log: `TORQUE START — hold at
  15 A…`), then tap **RELEASE**. Prediction: the hold drops at
  once and the log states `TORQUE released (RELEASE button) —
  handbrake-0 sent`. (This is the exact control that failed on
  2026-11-26; if the tour card is on screen, tap RELEASE wherever
  it sits — the tap must land even if RELEASE is scrolled under
  where the card floats.)
- **P4 — DISARM still stands everything down mid-hold.** Start
  **Hold 15 A** again, then tap **DISARM**. Prediction: immediate
  release — log: `TORQUE released (guard stand-down — DISARM) —
  handbrake-0 sent` plus the GUARD STAND-DOWN lines; continued
  disturbance for 10 s produces no torque, no speech, no re-climb
  until Set Tamper is tapped again.
- **P5 — Dash Focus on every theme.** On the Dash tab: tap
  **Focus** (right end of the dashboard selection row).
  Prediction: header, tab bar and the dashboard selection all
  disappear; the dashboard fills the whole screen; a slim handle
  stays visible on the right edge. One tap on the handle restores
  everything exactly as it was. Repeat on at least one other
  dashboard theme (swipe the theme first) — same behaviour.
- **P6 — Zero GUARD DATA STARVED.** Across the whole run,
  prediction: no `GUARD DATA STARVED` line appears while the
  board is connected and answering (the v3-16 P0 re-grade,
  carried).

## Carried bench residue (from the v3-16 card, still open)

- Held-perfectly-still rung-2 variant: at P1, if you can, hold the
  board perfectly still in the air at rung 2 for a few seconds —
  the pulse should still be felt (the pattern runs on its own
  clock; stillness does not gate it).
- DISARM during an active rung-2 (guard) hold in the card's exact
  form: during P1/P2, tap DISARM mid-pulse — prediction: the
  pulse releases immediately, mid-pattern, not at a boundary.

## While you listen

- All three spoken lines are FINAL — approved by Tony 2026-11-25;
  none changed by a single character in this build. Rung 2:
  "Warning. This board is locked. Put it down now — keep carrying
  it and the full alarm triggers." Rung 3: "Your actions have
  caused this board to be identified as stolen and being tracked.
  Authorities have been notified. Put it down now, or you will be
  caught and prosecuted."
- Lights: verification stays SKIPPED on this board (early-stock
  LCM); nothing in this run grades lights and no surface claims
  otherwise.
- The step count (3), the pulse pattern (4-on/1-off at 10 Hz) and
  the 15 A peak are DESIGN VALUES for bench tuning — if a rung
  feels too eager or too lazy, note the rung and direction; the
  bench retune is expected, not a failure.

## Safety / abort

- Footpad press aborts the rung-3 shudder.
- DISARM is the hard stop at any point. Closing the page is the
  dead-man fallback.
