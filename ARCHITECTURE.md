# Architecture

Visual scheme of the thinking map — what each part does and how they fit together.

## Quick links

- [Project docs](https://github.com/igareosh/fpf-agentic-thinking-map)
- [Project live demo](https://igareosh.github.io/fpf-agentic-thinking-map/)

## Module chain

- `primitives.py` — 12 primitives + 5 floors
- `state.py` — binding + active state + slice
- `guards.py` — 9 hard constraints
- `logic.py` — 6 operators + rules
- `traversal.py` — step engine + 10 declared outcomes

## Runtime contract

`step()` is the normal runtime path. It returns a compact JSON slice:

- where the agent is
- what can fire
- what is blocked
- what evidence is missing or stale
- what outcome applies

The model stays free to generate. The map only keeps runtime state and checks the next lawful move.
