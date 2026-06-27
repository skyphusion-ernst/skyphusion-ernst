# Status: vivijure-local-backend legal/contributor prep (staged, NOT yet landed)

Public-release groundwork (item #2: license + legal/contributor) for the homelabber flagship
`skyphusion-labs/vivijure-local-backend`. The repo is still PRIVATE and this is prep, NOT the
public flip (which waits on the security audit + Conrad's explicit go).

## BLOCKER (why these are staged here, not in the target repo)

As of 2026-06-27 I cannot reach the target repo to open a PR:
- `gh api repos/skyphusion-labs/vivijure-local-backend` returns **404 Not Found**, and
- the same call reports my (skyphusion-ernst) gh token **lacks the `repo` scope**, so I cannot
  see, clone, or PR ANY private repo regardless of whether it exists under that exact name.

So one of two things is needed before I can land these:
1. Confirm the exact repo name and that it exists, AND
2. Grant skyphusion-ernst the `repo` scope (and collaborator access) on it, OR have it cloned
   into `/home/ernst/dev/vivijure-local-backend` for me.

These four files are ready to drop in the moment access is sorted.

## What is staged

- `LICENSE` -- GNU AGPL-3.0-only, **byte-identical** to the Vivijure Studio LICENSE
  (sha256 0d96a4ff...abcb0). Copyleft self-host, matches the studio and the RunPod backend.
- `NOTICE` -- matches the studio NOTICE, plus a local-by-architecture paragraph (runs on your
  own GPU; data never leaves your box; Skyphusion Labs runs no instance).
- `CONTRIBUTING.md` -- DCO sign-off (no CLA), inbound=outbound AGPL, house rules (no em/en
  dashes, Conventional Commits), adapted from the org default + the vivijure-backend
  CONTRIBUTING, with a homelabber-friendly tone and a CSAM bright-line pointer.
- `README-selfhost-section.md` -- a drop-in README section: novice-friendly self-host framing
  (you run it, we host nothing, your data never leaves your box), License summary, AS-IS / no
  warranty, the CSAM hard line, and a not-legal-advice note.

## Recommendation: does it need its own PRIVACY / AUP, or just the framing note?

My read: the **framing note (NOTICE + README section) is sufficient**; it does NOT need its own
full PRIVACY policy or a full standalone AUP, for these reasons:

- **Privacy:** a local-only backend is the strongest possible privacy case. It runs on the
  user's own hardware and, in the self-host path, transmits nothing to Skyphusion Labs (even
  more so than the studio, which at least has Conrad's gated instance). A full PRIVACY policy
  would be near-empty boilerplate. The framing note ("your data never leaves your box, by
  architecture") says the true thing more honestly than a SaaS-style policy would.
- **AUP:** the canonical Acceptable Use Policy already lives in the Vivijure Studio legal
  corpus (`docs/legal/ACCEPTABLE-USE.md`). To keep ONE source of truth, the backend should
  **point to** that AUP rather than fork a second copy that can drift. I have put a short CSAM
  bright-line pointer in both CONTRIBUTING and the README section.

**One judgment call for Conrad:** the backend is the actual generation engine and could in
principle be run WITHOUT the studio. If we want it to stand fully on its own (so a downstream
user who only ever sees the backend still meets the CSAM/NCII red lines head-on), the minimal
add is a tiny `ACCEPTABLE-USE.md` stub in this repo that states the CSAM/NCII bright line in
one paragraph and links the canonical studio AUP for the rest. I can add that stub if Conrad
wants the backend self-contained; otherwise the pointer in CONTRIBUTING + README is enough.
Flagging rather than deciding, since "self-contained vs points-to-studio" is a posture call.
