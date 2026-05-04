# Agent Operating Rules

Repository-first operating rules for AI coding agents.

These rules are meant to reduce:

- silent misunderstanding
- oversized solutions
- unrelated edits
- speculative code
- weak verification
- repository mismatch

## 1. Resolve Ambiguity Early

Do not turn uncertainty into silent implementation.

- Say what you are assuming when the assumption matters.
- If the cost of guessing is meaningful, ask instead of choosing silently.
- If the cost is low, make the best reasonable assumption and make it visible.
- If the task can be read in more than one important way, surface the options.
- If the requested path implies a bad tradeoff, propose the better tradeoff.
- If something does not add up, stop and name the confusion.

The goal is to prevent expensive drift caused by a wrong initial read.

## 2. Use the Smallest Sufficient Change

Solve the actual problem with the smallest change that fully covers it.

- Do not add behavior that was not requested.
- Do not introduce abstractions for one-off cases.
- Do not add configurability without a real consumer.
- Do not add speculative handling for unsupported scenarios.
- If a shorter and clearer solution exists, prefer it.
- If the solution feels clever, verify that it is not also oversized.

Good code is proportionate code.

## 3. Constrain the Blast Radius

Keep the change bounded to the task.

- Do not refactor unrelated code because you noticed it.
- Do not rewrite nearby comments, formatting, or naming unless the task requires it.
- Follow the local style unless a repository rule explicitly overrides your preference.
- If you find unrelated issues, report them separately instead of bundling them into the same change.
- Remove only the unused imports, variables, branches, or helpers created by your own edit.
- Leave pre-existing dead code alone unless asked to address it.

Allowed exceptions:

- fixing breakage introduced by your change
- applying required formatter output
- making the smallest supporting edit necessary for correctness

Each changed line should have a direct path back to the task.

Manage file growth deliberately:

- Split files before they become hard to review or reason about.
- Treat size limits as guidance, not ideology.
- If a split adds more risk than clarity, keep the file larger temporarily and document why.
- Do not use the exception to avoid clearly safe separation of concerns.

## 4. Choose the Proof Before the Work

Decide how success will be checked before you call the work done.

- Convert vague requests into explicit success criteria.
- Prefer observable proof over confidence.
- When useful, reproduce the problem first.
- When useful, add or update tests first, then make them pass.
- For UI, exploratory, or stylistic work, define the verification method even when tests are not the main tool.
- For refactors, verify behavior before and after.

Useful plan shape:

1. change A -> verify with B
2. change C -> verify with D
3. final pass -> verify with E

Weak proof produces false confidence. Strong proof creates autonomy.

## 5. Follow the Local System

Do not treat the repository as if it were greenfield.

- Read repository-specific rules before making non-trivial changes.
- Respect local build, lint, test, and formatting requirements.
- Respect framework and project conventions unless the task is to change them.
- Extend existing helpers and patterns before inventing parallel ones.
- If local rules conflict with your default preference, follow the local rules.

Before building custom machinery:

- Check whether the framework, library, runtime, or repository already solves the problem.
- Prefer established project primitives when they solve the task cleanly.

When changing a contract:

- Inspect both sides of the contract, not just the file where the change begins.
- If you change a shared model, API, DTO, schema, or database contract, update the dependent consumers, tests, mocks, stories, and docs.

The best change is the one that belongs in the local system.

## 6. Avoid Speculative Surface Area

Do not add code whose only argument is that it may become useful later.

- Do not add unused helpers, methods, abstractions, or options.
- Do not create repository, service, controller, API, or UI surface with no real caller.
- Add extension points only when there is a concrete consumer or an immediate next step.

Unused flexibility is usually just deferred cost.

## 7. Make Comments Earn Their Place

Comments should add decision context, not retell visible code.

- Do not write comments that simply restate what the code already says.
- Do not add docblocks that only repeat parameter names or types.
- Use comments for rationale, constraints, workarounds, ordering requirements, or deliberate exceptions.
- `TODO` and `FIXME` are acceptable when they capture a real follow-up.

If the code is already clear, prefer no comment over redundant commentary.

## Working Baseline

Default behavior:

- resolve ambiguity early
- use the smallest sufficient change
- constrain the blast radius
- choose the proof before the work
- follow the local system
- avoid speculative surface area
- make comments earn their place
