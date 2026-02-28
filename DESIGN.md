# Design

This document operationalizes the [Vision](VISION.md).
It defines how the levels model works in practice — constraint flow, change classification, drift detection, and what CE requires structurally.

## Constraint and Feedback

Each level constrains the next downward:

- Charter constrains Vision — the vision must serve the charter's purpose.
- Vision constrains Design — design decisions must advance vision goals.
- Design constrains Implementation — code must follow design choices.

Feedback flows upward:

- Implementation pain signals design flaws.
  Repeated workarounds, excessive boilerplate, patterns that fight the architecture.
- Design friction signals vision gaps.
  Design decisions that can't be made without re-interpreting the vision, or design goals that conflict with each other.
- Vision tension signals charter ambiguity.
  Vision goals that pull in incompatible directions, or evolution that no longer clearly serves the charter.

**Escalation triggers.** Upward feedback becomes an escalation when:

- The same friction reappears after being addressed at the current level.
- A decision at the current level requires assumptions about the level above.
- Contributors disagree on interpretation, and the disagreement traces to the higher level.

When an escalation is identified, resolve it at the level where the ambiguity lives before continuing work below.

## Change Classification

Not all changes are equal.
A change's level determines its blast radius, review expectations, and who needs to care.

**Implementation** — the work.
The change stays within existing design boundaries.
No new patterns, no structural shifts.
Tests pass, constraints hold, ship it.

**Design** — learning.
The change introduces or revises a pattern, module boundary, or architectural choice.
It should reference the vision goal it serves.
Existing implementation may need to adapt.

**Vision** — growth.
The change redefines what success looks like, adds or removes goals, or shifts priorities.
All design and implementation become candidates for reassessment.
The charter must still be served.

**Charter** — a new project.
The fundamental purpose changes.
Everything below is invalidated and rebuilt from the new foundation.

**Decision tree:**

1. Does this change the project's purpose? → Charter change.
2. Does this change what success looks like or what the project values? → Vision change.
3. Does this introduce a new pattern, boundary, or structural decision? → Design change.
4. None of the above → Implementation change.

When classification is ambiguous, default to the lower level and note the uncertainty.
If the lower-level change keeps bumping into higher-level questions, that's an escalation trigger — reclassify upward.

## Misalignment and Drift

Alignment is a process, not a state.
Drift is normal.
What matters is detecting it early and correcting at the right level.

**Observable signals of drift:**

- The same debate reopens repeatedly without resolution.
- Exception lists grow — special cases that don't fit the design.
- Implementation churn continues without corresponding design evolution.
- Contributors interpret the same vision goal in conflicting ways.
- Changes are routinely misclassified — implementation changes that are actually design shifts, or design changes disguised as implementation.

**When to escalate vs. absorb:**

Absorb when the signal is local — a one-off exception, a single ambiguous case, a friction that resolves with a small clarification at the current level.

Escalate when the signal is structural — the same pattern across multiple instances, friction that can't be resolved without reinterpreting a higher level, or disagreement that persists after the current level's constraints have been applied.

## Artifacts of Clarity

CE requires structural artifacts that make alignment visible.
These are artifacts of clarity, not procedures of compliance — "have this, not do this."

CE does not prescribe workflow mechanics, tooling, or process.
It specifies what must exist and what it must contain.

**Required artifacts:**

- **Charter** — the project's purpose, stated plainly.
  Short enough to hold in memory.
  Stable enough that changing it means starting over.

- **Vision** — what serves the charter today.
  Includes goals, success criteria, and explicit non-goals.
  Evolves as understanding grows.

- **Design** — how the vision gets built.
  References vision constraints.
  Captures patterns, boundaries, and classification decisions.

- **Classified changes** — changes are labeled by level.
  The classification is visible in the change record (commit, PR, or equivalent).
  Misclassification is a signal, not a failure.

- **Identifiable revisions** — vision and design artifacts have a revision trail.
  When they change, the change is traceable — what shifted, why, and what it affects downstream.

These artifacts close the feedback loop.
Implementation pain that surfaces a design flaw is captured in a design revision.
Design friction that reveals a vision gap is captured in a vision revision.
The trail is the mechanism — without it, feedback dissipates.
