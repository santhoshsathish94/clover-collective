# Clover collective learning

The shared core that every Clover app can receive: problem-solving patterns that Clover users found useful, for
example "audit a file: read it, then check the numbers with Python". There is no server. This repository is the
whole system.

## Receiving: no account needed

Turn on **Receive Collective Learning** in the app. It downloads two files from this repository,
`releases/manifest.json` and then `releases/history/v<version>.json`, and checks them before using anything:

- the Ed25519 signature against the public key built into every Clover app:
  `a4d9d040035a19a5f1214bd30881b40842d4b06d0990c1bfdd6252fd90280283`
- the SHA-256 of every rule file
- expiry and revocation

A release that fails any check is not applied.

## Contributing: public, with your GitHub account

1. Turn on **Contribute to Collective Learning** and sign in with GitHub.
2. The app shows you the exact patterns.
3. When you confirm, it opens a public issue here under your GitHub name.

Each pattern contains only:

- words from a closed general vocabulary (Open English WordNet 2025)
- tool names
- local counts

It never contains messages, memory, files or names. Personal memory and learning stay in each person's own
private repository.

The automation ([`.github/workflows/collective.yml`](.github/workflows/collective.yml), running
[`engine/collective_repo.py`](engine/collective_repo.py)) checks every request again. It refuses:

- words outside the vocabulary
- personal fields
- unknown tools
- strategy text other than the fixed text for those tools, because a rule's strategy becomes guidance in every app
- accounts younger than 30 days, and bots

It replies on the issue and closes it.

A pattern joins the shared core when both of these are true:

- at least 3 different GitHub accounts have sent it
- it passes the held-out checks in `engine/collective_evaluator.py`: unseen phrasings, cross-domain use, and no
  regressions

The automation then signs a new release.

To withdraw, use **Withdraw** in the app. It opens a "withdraw" issue, and your patterns leave the next release. The
issues and the git history stay public.

## What is here

| Path | What it holds |
| --- | --- |
| `releases/manifest.json` | The current release, signed |
| `releases/history/` | Every release with its rule files; this is what the apps download |
| `core/` | The rules of the current release, one file each |
| `contributions/` | The patterns each GitHub account sent, named by GitHub's numeric account id |
| `candidates/`, `evaluations/` | The checks behind each release |
| `seed/rules.json` | The 5 rules carried over from Clover's earlier shared core (release 1.0.327 on k3, 2026-11-07) |
| `engine/` | The code the automation runs, copied from the Clover framework (see `engine/SOURCE.md`) |

## Limits

- **New kinds of patterns:** the held-out checks only cover patterns they have probes for. A new kind of pattern
  needs probes added to `engine/collective_evaluator.py` before it can be promoted.
- **Who controls releases:** the signing key is a secret of this repository. Whoever controls the repository
  controls the releases. Replacing the key means updating the public key in the apps.
- **Starting rules:** the 5 seed rules stay until contributions promote a rule for the same word.

License: Apache-2.0. Open English WordNet 2025 (CC BY 4.0) is downloaded by the automation at run time, checked
against a pinned SHA-256, and not stored here.
