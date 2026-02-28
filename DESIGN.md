# Design

This document bridges the [Vision](VISION.md) to practice.

## Constraints and Feedback

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

Misalignment is easiest to resolve at the highest level where it occurs.
Signs that a higher-level conversation may serve you well:

- Exception lists keep growing.
- More unicorns are allowed.
- The same type of friction keeps reappearing.
- People seem to be talking past each other.

## Change Classification

Changes in a project happen at different levels, and the level determines the blast radius.

- **Implementation** — the work.
  The change stays within existing design boundaries.
  No new patterns, no structural shifts.

- **Design** — learning.
  The change introduces or revises a pattern, module boundary, or architectural choice.
  Existing implementation may need to adapt.

- **Vision** — growth.
  The change redefines what success looks like or shifts priorities.
  All design and implementation decisions become candidates for reassessment.

- **Charter** — a new project.
  The fundamental purpose changes.
  Everything below is invalidated and rebuilt from the new foundation.

When classification isn't obvious, these questions may help:

1. Does this change the project's purpose? → Charter.
2. Does this change what success looks like or what the project values? → Vision.
3. Does this introduce a new pattern, boundary, or structural decision? → Design.
4. None of the above → Implementation.

When in doubt, default to the lower level.
If the change keeps bumping into higher-level questions, that's a sign it belongs higher.

## Artifacts

The vision describes shared artifacts at each level — something you can point to that captures alignment.
In practice, there are two kinds of artifacts that make collaboration work.

### Clarity

Artifacts of clarity capture what alignment looks like at each level.

- **Charter** — why the project exists.
  Short enough to hold in memory.
  Stable enough that changing it means starting over.

- **Vision** — what serves that purpose today.
  Includes goals, success criteria, and explicit non-goals.
  Evolves as understanding grows.

- **Design** — how the vision gets built.
  References vision constraints.
  Captures patterns, boundaries, and classification decisions.

- **Implementation** — the code itself.
  Expresses design decisions in working software.

### Change

Artifacts of change capture how those artifacts evolve.
They preserve why decisions were made, so the reasoning survives the conversations they were made in.
What these look like varies by project: issues, pull requests, commit history, design docs, conversation threads, whatever fits.
They serve all levels — a pull request might change the vision or fix a bug.

How many to keep is its own question.
Too many create noise; too few risk context being lost.
The right balance, and how it evolves with the project, should be a continuing conversation for those involved.
