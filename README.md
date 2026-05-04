# Agent Engineering Rules

A repository-first operating standard for AI coding agents.

This repository packages a baseline ruleset for AI coding assistants working inside real repositories. It is meant to sit underneath project-specific instructions, not replace them.

## Why this exists

Most AI coding failures are not exotic. They are repetitive:

- they misread the task and keep going
- they solve too broadly
- they edit outside the real scope
- they introduce speculative code
- they claim success before verification
- they ignore the local system they are supposed to fit into

This repository exists to counter those patterns with one reusable baseline.

## Repository layout

- `rules.md`
  - the full canonical ruleset
  - best source when you want the complete wording
- `CLAUDE.md`
  - compact drop-in version for Claude-oriented workflows
- `AGENTS.md`
  - compact drop-in version for agent-oriented workflows

The files are intentionally not identical:

- `README.md` explains the repository
- `rules.md` defines the full standard
- `CLAUDE.md` and `AGENTS.md` provide shorter install targets

## Installation

### Use as `CLAUDE.md`

New project:

```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/martin-fabian/agent-engineering-rules/main/CLAUDE.md
```

Append to an existing file:

```bash
printf '\n' >> CLAUDE.md
curl https://raw.githubusercontent.com/martin-fabian/agent-engineering-rules/main/CLAUDE.md >> CLAUDE.md
```

### Use as `AGENTS.md`

New project:

```bash
curl -o AGENTS.md https://raw.githubusercontent.com/martin-fabian/agent-engineering-rules/main/AGENTS.md
```

Append to an existing file:

```bash
printf '\n' >> AGENTS.md
curl https://raw.githubusercontent.com/martin-fabian/agent-engineering-rules/main/AGENTS.md >> AGENTS.md
```

### Use the neutral rules file

If your tooling supports a shared reference file, use `rules.md` directly and let local project instructions point to it.

## The baseline in one view

The operating model is built around seven habits:

1. resolve ambiguity early
2. use the smallest sufficient change
3. constrain the blast radius
4. choose the proof before the work
5. follow the local system
6. avoid speculative surface area
7. make comments earn their place

## Scope

This repository is intentionally:

- language-agnostic
- framework-agnostic
- vendor-agnostic
- repository-first

It does not define:

- language style guides
- framework idioms
- test commands
- build commands
- CI rules
- deployment workflow

Those belong in the target repository.

## Intended use

Use this repository as the baseline layer.

Then add project-local rules for:

- framework conventions
- build, test, and formatting commands
- architectural boundaries
- API or schema constraints
- deployment and release rules

## License

MIT
