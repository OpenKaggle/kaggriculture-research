# Kaggriculture after-action review — 2026-10-29

> After-action review prepared 2026-10-29 from public post-competition sources;
> internal evidence grades mapped to Verified/Unverified.

Evidence convention: **Verified** = backed by a recorded receipt or an official
frozen reading; **Unverified** = not obtained within the review budget.

## A. Final state vs the winner (quantified)

- [Verified] The winner "M & M & P & Q" finished at **3314.1** vs our frozen
  q5 bot at **1231.2** (the public-lane bot scored 1167.8), a gap of **2082.9**;
  final rank **3177/10148**. Source: frozen final-leaderboard capture at
  closeout (2026-10-15).
- [Verified] Leaderboard distribution: p50 = 831.9, p90 (≈ rank 1015) = 1842.9,
  p99 (≈ rank 101) = 2467.3; the Top 10 spanned 2931.9–3314.1, and every Top-10
  team's last submission was **2026-09-30** (iterating to the final day).
- [Verified] Rating→rank conversion anchors: 2266.9 → rank 299; 2094.7 → 500;
  1846.8 → 1000; 1782.9 → 1232; 1607.5 → 2000; 1231.2 → 3177. In the mid and
  tail of the board, ~600 rating points ≈ ~2000 rank places.
- [Verified] Convergence-period decay: the live reading of 2116 (2026-09-10)
  decayed monotonically to the frozen 1231.2, a loss of ~885 rating points
  (rank 299 → 3177).
- [Unverified] The mechanisms of the winner (M & M & P & Q) and the runner-up
  ("Victor @ Tufa Labs"): official writeup pages are JavaScript-rendered and
  no public writeup was retrievable within budget.

## B. What the leaders did that we did not

1. [Verified] **Neural policy as the main line.** The 3rd-place DSM solution
   (3161.8) is a BC+PPO-trained policy network (generation-70 weights), not a
   pure hand-written expert. Source: the
   `github.com/seven320/kaggriculture-3rd-place-solution` README.
2. [Verified] **A fast local simulator.** Built on the community "4000x
   environment speedup" public notebook (Apache-2.0), plus a custom Rust engine
   verified per transition pair against `kaggle-environments` 1.32.7 (31 tests).
3. [Verified] **Large-sample strict A/B testing.** 7 opponents × 1792 games per
   arm with bootstrap 95% CIs (their post-processing layer measured +13.62pp
   [+10.88, +16.41]). Our own paired tests ran only 432 games per arm; a
   false-positive route upgrade was the direct cost of the underpowered sample.
4. [Verified] **A rule-based post-processing layer.** Replacing wasted actions
   with the network's next-best action, banking at hour 23, selling at ≥ base
   price, a day-29 collection plan starting at step 708, and an endgame
   liquidation pass — the entire endgame cash chain made explicit as stages.
5. [Verified] **Iterating to the deadline.** All Top-10 teams submitted through
   2026-09-30; our last submission was 2026-09-26.
6. [Verified] **What we did not lack.** Two-slot freezing, paired falsification
   tests, and verification that the official reward equals final cash —
   discipline was comparable. The missing pieces were the learnable layer and
   the fast simulator.

## C. Not worth pursuing (honest assessment)

- Full reproduction of the BC/PPO pipeline plus the CUDA evaluation arena:
  their eval harness requires unpublished opponent weights, and the line is
  closed, so rebuilding the setup exceeds the benefit. **Not worth pursuing.**
- A self-built Rust engine: a community 4000x simulator already exists under an
  open license. **A self-built version is not worth pursuing**; adopting an
  off-the-shelf simulator in the next competition is.
- Day-29/hour-23 hand tuning: game-specific. The one generalizable rule — when
  reward = final cash, the endgame cash-conversion chain should be planned as
  explicit stages — was already known to us and only ever applied as local
  settlement optimizations.

## D. Lessons to institutionalize

1. **Game/adversarial lines: never extrapolate rank or prize probability from a
   single live rating reading.** The conversion table in section A shows the
   2116 reading corresponds to only ~rank 450 on the frozen board, with ~885
   rating points of monotone decay during convergence. Rule: take the lower
   bound of the cash band and estimate rank from the convergence-period rank
   distribution. (Same failure shape as the earlier Maze Crawler line.)
2. **The single biggest leverage if replayed: wire in the 4000x community
   simulator in week 1.** It lifts paired experiments from 432 games per arm to
   ≥1700 games per arm (enough to resolve +13.6pp-level differences), which
   would most likely have falsified our route/post-processing false positives
   early — at near-zero cost (public, Apache-2.0). This was the single largest
   missing piece in this campaign.
3. **The dominant architecture in simulation games is a learnable policy plus
   rule-based post-processing**; pure hand-written experts are the structural
   ceiling of this arena. Our gap to 3rd place was architectural (no BC/PPO
   layer), not tuning-level. Evaluate "can we train a policy here" before
   committing to hand-written investment.
4. **Iteration-deadline management.** The Top 10 all submitted on the final
   day; the opponent pool kept changing until the deadline. Freezing early
   forfeits the last round of matching gains against that pool (our 09-26 vs
   their 09-30).

## E. Open questions

- The winner's mechanism, and the cross-team BC signal implied by the 3rd-place
  repository's "sub112 → MMPQ-BCw" note: requires reading the official writeup
  or the winner's replay — not machine-retrievable (JavaScript-rendered pages).
- The official Bradley–Terry update equation was never published; our 80-game
  noise conclusion has no public quantitative corroboration [Unverified] and is
  supported only by our own convergence-monitoring series (980/1001 games
  recorded, Verified).
- Opponent-side causes of the Bakery→Smoothie −1885 and Yarn→Yarn −32 failure
  clusters: would require frame-by-frame replay analysis.

## Sources

- `github.com/seven320/kaggriculture-3rd-place-solution` (3rd-place solution
  README) [Verified]
- Kaggle competition and discussion pages for kaggriculture
  (JavaScript-rendered; only title-level retrieval succeeded) [Unverified]
- Frozen final-leaderboard capture at the 2026-10-15 closeout [Verified]
