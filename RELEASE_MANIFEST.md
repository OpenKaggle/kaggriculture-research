# Public release manifest

## Scope

This release is the public-source boundary for the Kaggriculture research
workbench. It contains reviewable OpenKaggle source, evaluators, builders, and
documentation. It is intentionally not a competition-data, replay, or
third-party-notebook archive.

## Included

- Original Python source for retained agents, builders, and verifiers.
- Arena and evaluation source that does not include protected inputs.
- Documentation, campaign context, notices, and lightweight provenance.

## Excluded

- Official Kaggriculture data, rules snapshots, replay payloads, and remote
  cache output.
- Submission packages, generated builds, models, environments, and credentials.
- All `agents/*/actions.json` fixtures and
  `agents/last_mile_harvest/tapes.json`.
- The entire `reference/` tree of third-party notebooks, kernels, and copied
  metadata.

## Release checks

Before a public push, verify all of the following against the commit being
published:

1. `git ls-files` contains neither `reference/` paths nor the excluded fixture
   paths above.
2. The working tree is clean and tracked files are scanned for credential-like
   material without printing candidate contents into logs.
3. The history reachable from `main` contains no excluded paths.
4. A fresh clone of the remote `main` repeats the path and structured-data
   checks.

## Reproduction boundary

Use [DATA_SOURCES.md](DATA_SOURCES.md) to obtain upstream material under its
own terms. Do not use this repository as authority to obtain protected data,
replays, or third-party content. The absence of a fixture is a safety boundary,
not a missing download instruction.
