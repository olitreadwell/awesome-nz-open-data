# Security

This repository is a Markdown list, a Python site builder, and two GitHub
Actions workflows. There is no server and no user data, so the realistic
security surface is small.

## Report a vulnerability

Use GitHub's private report form:

<https://github.com/olitreadwell/awesome-nz-open-data/security/advisories/new>

That channel is private between you and the maintainer. Please do not open a
public issue for a vulnerability, and do not paste a working exploit into an
issue thread.

## What is in scope

- A link in `README.md` that points at something malicious, or at a domain
  that has been taken over since the entry was added.
- A command in `scripts/build_site.py` or `scripts/validate_readme.py` that
  could execute untrusted input from `README.md`. Both scripts parse the
  README, so this is the part worth attacking.
- A workflow that exposes a secret, or that runs contributor-controlled code
  with write permissions.

## What is out of scope

- Vulnerabilities in development dependencies or the toolchain that do not
  change what the scripts do.
- Anything that needs a modified clone or a compromised machine.

## Handling

The site builder and the validator run on every pull request. Link checking
runs weekly and reports into `.state/`. Neither reads anything other than
`README.md`.
