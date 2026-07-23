# FPF Agentic Thinking Map - Architecture

Current architecture index for
[`fpf-agentic-thinking-map`](https://github.com/igareosh/fpf-agentic-thinking-map).
The library repository remains the source of truth.

## Live visual

[Open the v1.9.2 three-run runtime trace](https://igareosh.github.io/fpf-agentic-thinking-map/demos/three-runs.html).

It shows three test-backed paths:

- evidence recovery followed by a lawful transition;
- `PendingInput` producing `AWAIT`, then resolving to `IDLE`;
- a concrete `MoveIntent` protected by a state-bound
  `AuthorizationReceipt`.

## Current module chain

- `primitives.py` - 10 primitives + 5 floors
- `authorization.py` - expiring, single-use approval bound to transition + state
- `pending_input.py` - external dependency identity and wake conditions
- `move_intent.py` - concrete move identity, parameters, and lineage
- `state.py` - runtime binding, active state, slices, and trace
- `guards.py` - 9 hard constraints
- `logic.py` - 6 operators + rules
- `traversal.py` - step/inspect/attempt engine + 11 declared outcomes
- `examples.py` - 8 shipped scenarios
- `verify.py` - 26 deterministic checks

## Runtime contract

`step()` inspects what is currently possible. `inspect_move()` evaluates one
concrete proposal without mutation. `attempt_transition()` is the explicit
write path and rechecks evidence, gates, guards, and authorization before state
changes.

The model remains free to generate and compare. The runtime keeps movement
legality, waiting, approval, and trace identity explicit.

## Source documents

- [Full architecture](https://github.com/igareosh/fpf-agentic-thinking-map/blob/main/ARCHITECTURE.md)
- [Version tracker](https://github.com/igareosh/fpf-agentic-thinking-map/blob/main/docs/VERSION_TRACKER.md)
- [Advisories](https://github.com/igareosh/fpf-agentic-thinking-map/blob/main/docs/deep/ADVISORIES.md)
- [Development and compliance harness](https://github.com/igareosh/fpf-agentic-thinking-map/tree/main/dev_mcp)
