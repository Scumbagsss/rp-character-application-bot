# RP Character Application Bot

> **Portfolio showcase — production source is private and this repository is intentionally non-runnable.**

Discord character application and review system for RP servers with dynamic application types and staff workflows.

## What it demonstrates

- Dynamic application types
- Modal-based character forms
- Role-based staff routing
- Take/approve/reject workflow
- Role grant after approval
- Persistent review state

## Technology

Python • discord.py • JSON/JSONC • Persistent Views • Async workflows

## High-level workflow

1. Choose application type
2. Collect character data
3. Create review context
4. Staff processes application
5. Apply role/state outcome

## Public interface preview

The public skeleton exposes only the architectural surface:

- `open_application(...)`
- `submit_character(...)`
- `assign_reviewer(...)`
- `approve_character(...)`
- `reject_character(...)`

The production implementations behind these methods are withheld. See [`NOTICE.md`](NOTICE.md).

## Repository contents

- `src/public_interface.py` — non-runnable interface skeleton;
- `docs/ARCHITECTURE.md` — high-level design;
- `examples/config.example.jsonc` — sanitized configuration shape;
- `LICENSE` — explicit all-rights-reserved notice.

## Status

Production-tested private project / portfolio edition.
