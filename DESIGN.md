# Design

This document bridges the [Vision](VISION.md) to practice.

## Constraint and Feedback

Each level constrains the next downward:

- Charter constrains Vision.
- Vision constrains Design.
- Design constrains Implementation.

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
All design and implementation become candidates for reassessment, but the charter must still be served.

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

What matters is detecting drift early and correcting at the right level.

**Observable signals:**

- The same debate reopens repeatedly without resolution.
- Exception lists grow: special cases that don't fit the design.
- Implementation churn continues without corresponding design evolution.
- Contributors interpret the same vision goal in conflicting ways.
- Changes are routinely misclassified: implementation changes that are actually design shifts, or design changes disguised as implementation.

**When to escalate vs. absorb:**

- Absorb when the signal is local: a one-off exception, a single ambiguous case, a friction that resolves with a small clarification at the current level.
- Escalate when the signal is structural: the same pattern across multiple instances, friction that can't be resolved without reinterpreting a higher level, or disagreement that persists after the current level's constraints have been applied.

## Artifacts

The vision describes shared artifacts at each level — something you can point to that captures alignment.
In practice, there are two kinds of artifacts that make collaboration work.

### Clarity

Artifacts of clarity make alignment visible.
They capture what a project is and how it thinks about itself.
Every project following CE needs structural clarity at three levels:

- **Charter** — why the project exists.
  Short enough to hold in memory.
  Stable enough that changing it means starting over.

- **Vision** — what serves that purpose today.
  Includes goals, success criteria, and explicit non-goals.
  Evolves as understanding grows.

- **Design** — how the vision gets built.
  References vision constraints.
  Captures patterns, boundaries, and classification decisions.

### Change

Artifacts of change make evolution traceable.
They capture why decisions were made, so the reasoning survives the conversations they were made in.
What these artifacts look like varies by project: issues, pull requests, commit history, design docs, conversation threads, whatever fits.

There's a balance. Too many artifacts create noise; too few risk context being lost.
What the right balance is, and how it evolves with the project, is a conversation for those involved.
