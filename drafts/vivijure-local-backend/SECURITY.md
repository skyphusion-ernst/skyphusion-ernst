# Security policy

> DRAFT pending coordination with Rollins on contact addresses and any backend-specific
> reporting wording, and Conrad's sign-off. Modeled on the Skyphusion Labs org-wide policy,
> tailored for a local backend that runs on the operator's own hardware.

## Supported versions

This is a rolling, single-`main`-branch project. Only the latest release (or current `main`)
receives security fixes. If you are running an older revision, upgrade to pick them up.

## Reporting a vulnerability

Please do **not** file a public GitHub issue for security problems.

Report it privately through GitHub's private vulnerability reporting: open the repository's
**Security** tab and click **"Report a vulnerability"**. This creates a private advisory visible
only to you and the maintainers. If that option is not available, email
**security@skyphusion.org** instead (do not disclose details in a public issue).

Please include:

- A description of the issue and its impact.
- Steps to reproduce, including a minimal example if possible.
- The affected version (release, tag, or commit SHA if known), and your GPU / driver / OS if
  the issue is hardware- or environment-specific.
- Any suggestions for remediation.

Reports will be acknowledged within a reasonable window (target: 5 business days). Time-sensitive
issues should say so. Please allow up to 90 days for a coordinated fix before public disclosure.

## Scope

This software runs locally on **your** hardware; Skyphusion Labs operates no instance of it and
holds none of your data, so there is no hosted service of ours to attack. Security reports should
concern this project's own code and how it runs on your machine (for example: unsafe file
handling, a path-traversal in artifact paths, command/argument injection into a render step, or a
dependency we pull in a way that is exploitable). The security of upstream model weights or
third-party libraries themselves should go to their respective projects (beyond how our code
invokes them). Because you are the operator, securing the box you run this on (OS, drivers,
network exposure of any local API you choose to expose) is yours to own.

Please do not send code, diffs, or excerpts you do not have the rights to share.

## Abuse and content reports (not security)

Misuse of the software to generate prohibited content is an Acceptable Use matter, not a
vulnerability. See [`ACCEPTABLE-USE.md`](ACCEPTABLE-USE.md). Suspected CSAM goes to NCMEC
(report.cybertip.org) and law enforcement; other abuse involving the project goes to
**abuse@skyphusion.org**.
