# CLAUDE.md

Baseline operating rules for AI coding assistants.
Add project-specific rules separately.

---

## Source

The canonical version lives in `rules.md`.
This file is the compact drop-in version.

---

# Agent Operating Rules

Use this file as a working baseline, then add local repository rules below it.

## Default posture

- Resolve ambiguity early.
- Use the smallest sufficient change.
- Constrain the blast radius.
- Choose the proof before the work.
- Follow the local system.
- Avoid speculative surface area.
- Make comments earn their place.

## Practical rules

### 1. Resolve Ambiguity Early

- Do not turn uncertainty into silent implementation.
- State important assumptions.
- Ask when guessing would be costly.
- If the risk is low, make the best reasonable assumption and make it visible.
- Surface competing interpretations when they materially change the outcome.

### 2. Use the Smallest Sufficient Change

- Solve the actual problem, not the larger imagined one.
- Do not add extra behavior, abstraction, configurability, or speculative handling without a real consumer.
- Prefer the shorter clear solution over the flexible oversized one.

### 3. Constrain the Blast Radius

- Keep the diff bounded to the task.
- Do not refactor unrelated code just because you saw it.
- Do not rewrite nearby formatting, comments, or naming unless the task requires it.
- Remove only the dead code your own edit creates.
- Allowed exceptions:
  - fixing breakage introduced by your change
  - applying required formatter output
  - making the smallest supporting edit necessary for correctness

### 4. Choose the Proof Before the Work

- Decide how success will be checked before declaring the work done.
- Convert vague requests into explicit verification.
- Use tests when they fit; use another clear verification method when they do not.
- Prefer observable proof over confidence.

### 5. Follow the Local System

- Do not treat the repository as greenfield.
- Read and follow local build, test, lint, formatting, and framework rules.
- Reuse local helpers and patterns before inventing parallel ones.
- When changing a shared contract, inspect and update both sides.

### 6. Avoid Speculative Surface Area

- Do not add code whose only defense is future possibility.
- No unused helpers, options, endpoints, surfaces, or extension points without a concrete next consumer.

### 7. Make Comments Earn Their Place

- Comments should add rationale, constraints, workarounds, or deliberate exceptions.
- Do not narrate code that is already obvious.
- Prefer no comment over redundant commentary.

For the full explanatory version, use `rules.md`.
