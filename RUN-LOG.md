# Run log

Durable journal of legal-affairs work. Newest first.

---
## 2026-06-27 -- Vivijure legal layer: self-host framing gate (PRs #367 + #369) -- CLEARS

**Repo:** skyphusion-labs/vivijure | **Docs:** docs/legal/{README,TERMS,PRIVACY,ACCEPTABLE-USE}.md
**Task from:** team-lead (Mackaye), release-gating check. Both PRs already MERGED to main
(#367 = legal layer in force + disclaimer + CSAM clause; #369 = TERMS values: $0 cap, Texas
governing law). Verified the merged state on origin/main = what the next tag will ship.

**Gate question:** do the docs use SELF-HOSTED-SOFTWARE framing (reader = operator on own
infra, compliant in own jurisdiction; skyphusion hosts/operates nothing for the public, sees
no user data by architecture) rather than hosted-SaaS "we collect/process/store/your account
with us/we may suspend"? Same miss that hit the vivijure legal layer once before, so read all
four docs in full, not just a couple of lines.

**Verdict: CLEAN. Gate clears.** Framing is strong and consistent across all four. The docs use
the correct TWO-MODE model: (1) self-host -> you operate, your data on your infra, skyphusion
never receives a byte; (2) Conrad's OWN private gated instance at vivijure.skyphusion.org (for
Conrad + crew + the Slate bot via service token) which is explicitly NOT a public sign-up
service. That second mode is the honest reason any "suspend / terminate / delete / your inputs"
language exists, and every instance of it is scoped to Conrad's own instance + project standing,
with "none of this reaches your self-hosted instance" stated plainly (TERMS section 11). That is
not a hosted-SaaS-for-the-public claim.

**Mechanical checks run on origin/main:**
- Em/en-dash scan (grep -P [–—]) across all four docs: CLEAN (zero hits).
- SaaS tell-phrase scan (we collect|store|process|retain|host|may suspend|reserve the right|
  your account with us|our service|sign-up|create an account): every hit is a NEGATION or a
  scoping statement, e.g. README L16 / PRIVACY L21-22 "does not run a hosted, multi-tenant,
  sign-up service ... no Vivijure account you create with us ... no pool of user data we hold";
  TERMS L66 "not open to public sign-up." No unscoped SaaS language anywhere.
- Not-legal-advice disclaimer: present at the top of ALL FOUR docs + README footer. KEPT.
- CSAM / abuse bright line: present and correctly framed -- condemnation + report on infra the
  project itself operates, with the explicit "we do not, and architecturally cannot, monitor a
  self-hosted instance" carve-out (AUP section 1; PRIVACY section 9). It is a condemnation+report
  stance, NOT a hosting/monitoring claim. KEPT.
- PR #369 values present: TERMS section 8 liability cap = $0 USD; section 13 governing law = Texas. Confirmed.

**One NON-BLOCKING style nit (does not affect the gate):** AUP opening line uses "self hosted"
unhyphenated twice ("data from your self hosted instances"); the rest of the corpus uses
"self-hosted". Pure consistency nit, not a framing/dash/disclaimer issue. Flagged to team-lead
as optional; release does not need to hold for it.

**Delivered:** reported CLEARS to team-lead via SendMessage so the tag can proceed.

---

## 2026-06-27 -- Postern PR #79: PRIVACY.md self-host framing fixes

**Repo:** skyphusion-labs/postern | **Branch:** ernst/privacy-notice-license | **Commit:** f63c85a
**Task from:** team-lead (Mackaye), isolated background session.

Conrad left two inline review comments on PR #79 PRIVACY.md, both on the
"Open items that need a licensed attorney before launch" section:
- L81 (controller/processor question): "No, it does not, because we don't operate postern
  for anyone, nor will we ever host postern for anyone. We write software, we're not an
  email hosting company."
- L83 (compliance burden): "That is correct, that is up to the operator of the software to
  operate the software in accordance with the laws and regulations within their own
  respective jurisdiction."

**The framing rule (recurring pattern):** skyphusion-labs SHIPS self-hosted software; it
never operates / hosts / processes mail for anyone. Every privacy/ToS/AUP line must read as
a software-license + self-host posture (reader = the operator on their own infra), not a
hosted-SaaS customer relationship. Same miss happened on the vivijure legal layer. Was told
to scan the WHOLE doc, not just the two flagged lines.

**What I did:**
- Both flagged items were resolved by Conrad's own review, so they are no longer "open
  items needing an attorney" (and were never really legal questions; they are business
  posture). Replaced that section with a definitive "Scope: software, not a service" that
  states both points as settled fact: (1) Skyphusion Labs writes/distributes Postern,
  operates it for no one, will not host mail, is not an email hosting company, runs no
  instance, so has no access to mail/user data and no controller/processor role attaches to
  the project; (2) running an instance lawfully is the operator's responsibility in their
  own jurisdiction, and the policy does not assume those duties for Skyphusion Labs.
- Dropped the now-dangling header clause "Items that need a licensed attorney are flagged at
  the end" (the section it pointed to is gone).
- Kept: top-of-doc "not legal advice" DRAFT disclaimer + a pointed consult-a-lawyer line for
  operators in the new section. (No abuse/CSAM clause exists in this doc; nothing to keep there.)
- Dash lint: clean (no em/en-dashes; only `--` and hyphens).

**Whole-doc framing scan result:** The BODY was already cleanly self-host framed
(BLUF L14-23 "no Postern service Skyphusion Labs operates for you"; "You are the data
controller" L34-40 already states operator-in-own-jurisdiction compliance; Children L60-62;
Changes L66-67; Contact L71-73 all say Skyphusion Labs runs no instance). The ONLY
hosted-SaaS-adjacent weakness was the two HEDGED open items, now fixed. No other misses found.

**Delivered:**
- Commit f63c85a pushed to PR #79 branch as skyphusion-ernst (DCO signed-off).
- Replies posted on both review threads (comment ids 3483536490, 3483541424) so Conrad can
  resolve them (reply ids 3484593363, 3484593413).

**Notes for next time:** the "open items needing an attorney" device is fine for genuine
legal-uncertainty flags, but once Conrad answers one in review it should become a definitive
statement, not stay a hedge. Business-posture facts (we do not host) are his calls, not
attorney questions; keep those out of the attorney-flag bucket.
