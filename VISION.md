# Vision

## The model

Software is built on layers of decisions.
At the top: *what* is this for? Below that: *how* do we get there?
And each *how* opens its own question — *what* does this piece need to do, and *how* should it do it? — repeating downward through layers of detail.

Coherent Evolution is a model for staying aligned across those layers as a project changes.
It gives teams a shared language for locating alignment problems and deciding where to focus.

## The *what* and *how*, all the way down

Every level of a project has a *what* (the intent) and a *how* (the approach).
The *what* at one level is answered by the *how* at that level, and that *how* becomes the *what* for the level below it.

Fewer people are involved at each successive level.
A project's purpose concerns everyone.
A subsystem's interface concerns the people working on and around it.
An implementation detail concerns whoever is writing the code or will work with it in the future.

People engage where they care about the *what*.
Once they're satisfied the shared understanding at that level is sufficient, they can release the *how* to the people working at the next level down.
Those people can then work without needing to check back constantly.
That trust is the mechanism that lets work flow without bottlenecks, and it only holds when the *what* is genuinely shared.

When a level is aligned on its *what*, the work below it is encapsulated.
You don't need to understand every implementation choice to trust a subsystem, and you don't need to understand every subsystem to trust the project is heading in the right direction.
Each level of alignment reduces what the levels above need to track.

## Change has a level

When something changes, the most important question is: which level does it affect?

A change to *how* something is implemented is different from a change to *what* a component is supposed to do, which is different from a change to *what* the project is for.
The response, the people involved, and the ripple effects all depend on the level.

Change is constant — during initial development, as needs shift, as people and technology change.
Alignment is never done; the structure helps you know where to re-align when things shift.

Friction at one level often surfaces a misalignment at the level above.
Persistent disagreement about an implementation detail may indicate misalignment on the *what* behind that *how*.
Recognizing that pattern lets you focus on the right problem.

## What success looks like

The Coherent Evolution model is working when:

- People can identify what level a change belongs to.
- Disagreements about *how* resolve quickly when the *what* is aligned.
- Friction at one level surfaces issues at the level above without destabilizing everything.
- People can explain their level's *what* without needing deep understanding of the levels above.

## What Coherent Evolution is not

- Not a process framework. There are no ceremonies, cadences, or prescribed workflows.
- Not governance. It identifies what kind of change is happening, not who decides.
- Not a replacement for domain expertise. Knowing which level a question belongs to doesn't answer the question.
- Not prescribing structure. No required artifacts, file layouts, or formats.
