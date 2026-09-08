# Deskflow Security

Proof-of-concept scripts for security vulnerabilities in Deskflow.

## Scope: published advisories only

**This repository contains PoCs for vulnerabilities that are already published
and fixed.** Every script here corresponds to a GitHub Security Advisory on
[deskflow/deskflow][advisories] that has been published, with a fix available in
a released version.

Work on unpublished or embargoed advisories does not belong here. It goes in the
private embargo repository until the advisory is published, at which point the
PoC is copied across in a fresh commit.

If you are reporting a new vulnerability, do not open a pull request here. Use
[private vulnerability reporting][reporting] on the main repository.

[advisories]: https://github.com/deskflow/deskflow/security/advisories
[reporting]: https://github.com/deskflow/deskflow/security/advisories/new

## Layout

```
poc/
  cve_<year>_<id>_<area>_<class>.py   # one PoC per CVE
  utils.py                            # shared helpers
```

## Prerequisites

- Python 3.9+
- A running Deskflow instance to target

## Running a PoC

```bash
python poc/<script>.py --host <target_ip> [--port <port>]
```

All PoCs default to `localhost:24800` and support `--help`.

Only run these against instances you own or are authorised to test.

## Adding a PoC

1. Confirm the advisory is **published** on [deskflow/deskflow][advisories].
   If it is not, this is the wrong repository.
2. Add a file in `poc/` named `cve_YYYY_NNNNN_<area>_<class>.py`.
3. Reuse helpers from `poc/utils.py` where it makes sense.
4. Exit non-zero (or print a clear `[FAIL]`/`VULNERABLE` line).
