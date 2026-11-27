# FloatCore — the app's anchor custody

This repository is the timestamped, hash-verifiable home of the **FloatCore app** (the Onewheel
companion app built by Tony Kammerer / FloatCore LLC with Pimple). It exists so the shipped app's
bytes have a public anchor: a commit history nobody can quietly rewrite, against which any copy
of the app, anywhere, can be checked.

## The settled build

- **Version:** core pack **v3-16** — `floatcore-core-v3-16.html` (single self-contained HTML file)
- **md5:** `9b48e3ca628f247781011525eb23a0c6`
- **Size:** 3,793,627 bytes
- **Settled:** 2026-11-26, by Tony's verdict after the Tier-4 bench run on his own board
  (two full anti-theft ladder climbs, rung 3 at exactly the 5th counted step, zero guard starvation).
- Full frozen lineage (v3-12 → v3-16, with every version's hash, status, and sources): see
  [VERSIONS.md](VERSIONS.md).

Verify any copy: run `md5sum` on it. If the hash differs from the one above, it is not the
settled build — no matter what anything else claims.

## Delivery note

The app ships to riders as a **direct file**, never through a framed/hosted page — the hosted
Library view runs inside a frame where Web Bluetooth is unavailable, so a framed copy can never
connect to a board. This repository is the app's anchor and archive, not its delivery channel:
riders receive the file itself, and this repo is where its authenticity can always be proven.

## Custody

- Repo created by Tony Kammerer (GitHub account **Aekammerer**) as part of FloatCore's
  Total-Freedom Map: own what we depend on, in the order it can hurt us.
- The working source of truth remains the FloatCore goal workspace and the Drive-verified backup
  packs; this repo is the public anchor copy of the settled build.
