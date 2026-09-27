# Reproducibility guide

## Snapshot purpose

This is a frozen, no-submit archive of Kaggriculture agents, builders,
evaluators, research notes, and small receipts. Reproduction is local and
read-only by default. It does not authorize a Kaggle upload, active-slot change,
remote replay crawl, or new remote experiment.

## Entry points

- `CAMPAIGN_CHARTER_v1.0.md` records the historical research gates.
- `arena/run_league.py` is the local league harness.
- `arena/analyze_league.py` and related `arena/` tools analyze local results.
- `build_submission.py` and `verify_submission.py` are packaging/validation
  utilities; invoking them does not authorize submission.
- `research/relaunch_2026-09-17/` preserves the later bounded research record.

The root README does not publish one canonical command with frozen arguments,
environment, and payloads. This release therefore does not fabricate a
quickstart. Reconstruct the environment and exact arguments from the retained
campaign records, then keep any generated builds, raw data, replay/cache output,
and submission files outside the public Git tree.

## Determinism and comparison

For any local replay, record the source hash, environment version, seeds,
opponent, seat, outcome, margins, and output bundle hash. Paired-seat or local
league evidence is research evidence only; it is not permission to mutate a
remote competition state.

Third-party agents and the Apache-2.0 `agents/last_mile_harvest/` subtree retain
their own notices. See `NOTICE.md` before reuse.
