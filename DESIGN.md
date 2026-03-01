# Design

The vision describes *why* conversations at the right level matter.
This document is about *what* supports those conversations: the artifacts and practices we find useful for applying the model.
Two kinds of artifacts matter: artifacts that capture clarity, and artifacts that capture change.

## Artifacts of clarity

At each level of a project, shared understanding works best when it lives in something concrete: documents, code, whatever makes alignment at that level legible.
We find these useful:

- **A charter** captures the top-level *what*.
  What is this project for? Who is it for?
  A few sentences that everyone involved can point to.
- **A vision** captures the *how* at the highest level: the approach, the model, the shape of the solution.
  It answers the charter and becomes the *what* for the level below.
- **Design documents** capture the *how* at the next level down: what tools, structures, and patterns serve the vision.
  Each design doc answers a piece of the vision and becomes the *what* for the people building it.
- **The code itself** is an artifact of clarity at the lowest level.
  It captures the *how* of implementation.
  When it's clear, it speaks for itself. When it isn't, that's a signal.

These aren't prescribed formats.
A charter might be one sentence. A design doc might be a diagram.

The test is always the same: if someone new joins at this level, do they have what they need to understand the *what* and contribute to the *how*?
We call this the onboarding test.
It's the simplest way to check whether your artifacts of clarity are working.

## Artifacts of change

Clarity artifacts capture where alignment stands now.
But alignment shifts, and the reasoning behind those shifts matters as much as the result.

Artifacts of change capture how and why the clarity artifacts evolve.
Issues, pull requests, commit messages, conversation threads.
They answer a different question than artifacts of clarity.
Clarity artifacts say "here's what we aligned on."
Change artifacts say "here's how we got there."

This matters because reasoning doesn't survive memory.
The context behind a decision fades, for the people who made it and certainly for anyone who arrives later.
When artifacts of change are working, someone can trace a decision back to the conversation that produced it and understand the tradeoffs that were weighed.

Not every decision needs this level of documentation.
The overhead of capturing reasoning should match the stakes.
A one-line fix doesn't need the same trail as a design change.
But when a decision affects alignment at a level, when it changes the *what*, the reasoning is worth preserving.

## Feedback between levels

Friction at one level often signals misalignment at the level above.
A persistent argument about implementation may mean the *what* behind it isn't actually shared.
A design that keeps getting reworked may point to an unresolved question in the vision.

Concrete artifacts make this signal visible.
An issue that keeps reopening, a PR discussion that won't converge, a pattern of rework in the code: these are legible signs that something above needs attention.
Without artifacts, the signal stays informal and easy to miss.

The response is to move the conversation to the right level.
Not to escalate, but to locate.
The model gives you a way to say "I think we're disagreeing about the *what*, not the *how*" and redirect from there.

## Signal and noise

More artifacts aren't better.
Every doc, issue, and comment is something someone might need to read.
The balance between capturing enough context and drowning in noise is a continuing conversation, not a solved problem.

Some useful questions:

- Is anyone reading this artifact? If not, is it serving clarity or just ceremony?
- Can someone at this level get oriented without reading everything below?
- When a decision gets revisited, can the reasoning behind it be found?

There's no formula.
The right balance depends on the team, the project, and the moment.
Noticing when you're missing context is a signal to capture more.
Noticing when docs are stale or ignored is a signal to capture less.

## A concrete example

We find GitHub issues and pull requests useful as artifacts of change.

An issue captures the *what* of a change: what needs to happen and why.
A pull request captures the *how*: the approach, the tradeoffs, the conversation around them.
Together they form a trail from intent to implementation that anyone can follow later.

When a PR discussion stalls, it's often because the *what* isn't shared.
Moving that conversation to an issue, relocating it to the right level, tends to unstick things.

This isn't the only way.
Other tools, other workflows: the mechanism matters less than whether the reasoning is preserved and findable.
The artifact is a side effect of the conversation, not a replacement for it.
