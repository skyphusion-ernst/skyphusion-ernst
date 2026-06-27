# Run log

Durable journal of legal-affairs work. Newest first.

---
## 2026-06-27 -- vivijure-local-backend: contacts CONFIRMED, SECURITY.md landed, set complete

Contact question RESOLVED by Conrad: security@ + abuse@skyphusion.org are real, monitored mailboxes
(they flow into the Postern email worker). So the final contact posture stands as drafted, no
downgrade: GitHub private vuln reporting (primary) + security@ (security fallback) + abuse@ (abuse)
+ NCMEC (CSAM). The monitored-mailbox caveat is closed.

Rollins landed SECURITY.md (commit 25e854b) with my Acceptable-use block + contacts verbatim,
dash-clean, zero placeholders. Final-read it: sections (Reporting / Scope / Acceptable use / Scope
of reports) are one voice with the AUP stub; CSAM/NCMEC bright line + "misuse is acceptable-use not
a security report" split intact; canonical studio AUP link + conditional in-repo ACCEPTABLE-USE.md link.

COORDINATION NOTE: the in-repo ACCEPTABLE-USE.md is added by MY PR #4, so the conditional link
resolves on #4 merge. Told Rollins NOT to add a second copy (avoid dupe/conflict on that file).

Lane #2 status: COMPLETE + landable. PR #4 (LICENSE canonical + CONTRIBUTING + ACCEPTABLE-USE stub)
ready for Mackaye review/merge alongside Joan README PR #3 and Rollins SECURITY.md, gated only on
Conrad one-paragraph AUP thumbs-up.

---
## 2026-06-27 -- vivijure-local-backend lane #2 LANDED as PR #4 (token unblocked)

Conrad added `repo` scope to skyphusion-ernst; access verified. Cloned the repo and discovered it
was NOT empty (my earlier staging assumed empty): LICENSE + NOTICE + README already existed, Joan's
README rewrite is PR #3, no CONTRIBUTING/SECURITY/AUP. So I reconciled instead of blind-adding.

PR #4 (branch ernst/legal-contributor, under skyphusion-ernst, DCO signed-off, dash-clean):
- LICENSE -- REPLACED the existing mangled AGPL copy (235 lines, reflowed, http:// URLs) with the
  canonical verbatim FSF AGPL-3.0-only, now byte-identical to studio (sha256 0d96a4ff...abcb0).
- CONTRIBUTING.md (new) -- DCO/inbound=outbound/house rules/pytest CPU flow/CSAM pointer, repo-tailored.
- ACCEPTABLE-USE.md (new) -- the standalone stub, PENDING Conrad one-paragraph confirm.

Reconciliation (so the PRs do not contradict, per Mackaye):
- NOTICE left as-is (already studio-matching); README owns the homelabber self-host framing.
- README NOT touched -- Joan PR #3 already one voice with NOTICE (License section mirrors it; "your
  data never leaves your box"; "skyphusion hosts nothing and sees nothing"). Avoided two PRs on one file.
- SECURITY.md NOT in my PR -- Rollins owns it as a single file; I sent him finalized policy text;
  CONTRIBUTING forward-references SECURITY.md (resolves when his lands).

Rollins convergence: he accepted my policy model; contacts = org-wide security@ + abuse@ (NOT a
backend alias); GitHub private vuln reporting will be ENABLED at the flip (primary) + security@
fallback; he added backend-specific scope (token-gate bypass = #1, R2/token leak, identity-strip
regression, SSRF via attacker R2 keys; weights are safetensors = low-risk). Open item still routed to
Strummer/Conrad: confirm security@/abuse@ mailboxes are actually monitored before flip.

Staged drafts dir in skyphusion-ernst is now superseded by the live PR; kept for history.

---
## 2026-06-27 -- vivijure-local-backend SECURITY.md: gave Rollins AUP wording + contacts

Rollins owns the repo's SECURITY.md (he mirrored the vetted vivijure-backend one, adapted Scope to
the local-door threat model: public tunnel + token-gate). He asked me for the policy wording. Sent
him a paste-ready "## Acceptable use" block (self-hosted framing: operator on own hardware/jurisdiction
responsible for lawful use; skyphusion ships software, operates/monitors nothing; CSAM/NCII bright
line = condemn + report to NCMEC; links canonical studio AUP) and a contact recommendation.

Contacts (grounded in live docs, not guesses): GitHub private vuln reporting PRIMARY +
security@skyphusion.org fallback (already published in org dot-github SECURITY.md); abuse@skyphusion.org
for abuse (already published in studio AUP v0.7.5); CSAM -> NCMEC. Using them is consistent, no new
commitment.

OPEN (flagged to team-lead -> Strummer/Conrad): confirm security@/abuse@skyphusion.org mailboxes are
actively MONITORED. Not a blocker (already public org-wide, so any gap pre-exists), but worth closing.
If Conrad prefers no email commitment, fall back to GitHub-private-reporting-only; I'll adjust the AUP
stub's reporting line to match.

---
## 2026-06-27 -- vivijure-local-backend: AUP stub + SECURITY draft staged

Follow-up to the #2 prep. Team-lead approved my AUP read and is recommending Conrad take the
STANDALONE option (backend can run without the studio, so it carries the CSAM/NCII red line
itself). Staged in drafts/vivijure-local-backend/ (commit cfcdb3b), dash-clean:
- ACCEPTABLE-USE.md -- one-paragraph CSAM/NCII red line + condemnation/report (NCMEC) + link to
  canonical studio AUP. One source of truth: stub restates only the absolute line, points to studio.
- SECURITY.md -- DRAFT vuln-reporting policy + abuse contact, modeled on org dot-github SECURITY,
  tailored for local-on-your-hardware (no hosted service to attack; operator secures their own box).
  PENDING: coordinate contacts (security@ / abuse@skyphusion.org) + backend wording with Rollins,
  then Conrad sign-off. Ernst = natural owner once access lands.

Access blocker unchanged (Conrad's call: grant ernst repo scope/collaborator, or it lands at the
public flip via public-scoped token). Not urgent; weekend pre-flip window. Messaging Rollins re
SECURITY contacts.

---
## 2026-06-27 -- vivijure-local-backend public-release prep (item #2: license + legal/contributor) -- STAGED, blocked on access

**Target:** skyphusion-labs/vivijure-local-backend (PRIVATE; prepping public flip, NOT the flip).
**Task from:** team-lead (Mackaye). My lane: LICENSE (AGPL-3.0 matching studio), CONTRIBUTING + DCO,
self-host framing note (NOTICE/README), novice-friendly tone; flag whether it needs own privacy/AUP.

**BLOCKER:** cannot reach the target repo. `gh api repos/skyphusion-labs/vivijure-local-backend`
returns 404 AND reports my (skyphusion-ernst) token lacks the `repo` scope, so I cannot see/clone/PR
any private repo. Need: confirm exact repo name + exists, and grant skyphusion-ernst `repo` scope +
collaborator access (or clone it into /home/ernst/dev/vivijure-local-backend). Reported to team-lead.

**Done anyway (staged, durable):** drafts/vivijure-local-backend/ in this repo, all dash-clean:
- LICENSE -- AGPL-3.0-only, byte-identical to studio (sha256 0d96a4ff...abcb0).
- NOTICE -- studio NOTICE + local-by-architecture paragraph.
- CONTRIBUTING.md -- DCO (no CLA), inbound=outbound AGPL, house rules, homelabber tone, CSAM pointer.
  Adapted from org dot-github CONTRIBUTING + vivijure-backend CONTRIBUTING.
- README-selfhost-section.md -- drop-in: self-host framing, License, AS-IS/no-warranty, CSAM hard
  line, not-legal-advice. Novice-friendly.
- STATUS.md -- documents blocker + recommendation.

**Recommendation:** framing note (NOTICE + README section) is sufficient; no full standalone PRIVACY
(local-only = nothing transmitted to skyphusion; full policy would be empty boilerplate) and no
forked AUP (point to the canonical studio AUP to keep one source of truth). Judgment call left to
Conrad: if the backend must stand fully alone (run without the studio), add a one-paragraph AUP stub
restating the CSAM/NCII bright line + linking the studio AUP. Flagged, not decided.

---
## 2026-06-27 -- Vivijure AUP "self-hosted" consistency follow-up (PR #378)

**Repo:** skyphusion-labs/vivijure | **Branch:** ernst/aup-selfhosted-consistency | **Commit:** d62b07c | **PR:** #378
Follow-up from the post-release legal framing read. One-line corpus-consistency fix in
docs/legal/ACCEPTABLE-USE.md: opening "stands with victims" paragraph wrote "self hosted"
unhyphenated; rest of the corpus uses "self-hosted". Correction to my earlier note: it was a
SINGLE occurrence, not two. No substantive/framing change, no deploy gate (docs only), DCO
signed-off, no dashes. PR opened under skyphusion-ernst.

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
