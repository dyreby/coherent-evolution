# Worked Examples

These scenarios walk through Coherent Evolution's classification mechanics.
Each one is realistic and a little messy — the point is to stress-test the model against friction, not just confirm it works when things are clean.

---

## 1. Switch database engines (SQLite → Postgres)

**The situation.** An app has used SQLite for two years.
A backend engineer proposes switching to Postgres to support concurrent writes and a reporting layer that needs better query tooling.

**Classification.** Design.

The database engine is a structural choice — a boundary that everything in the implementation depends on, but that doesn't change what success looks like.
The project's goals haven't shifted; the current choice is just failing under load.

**How CE routes it.** The engineer opens a design-level conversation.
That means pointing to Vision constraints — what does the project value?
If the Vision says "simplicity of operation" or "no external dependencies," the proposal bumps up: it's not just a structural change, it's one that appears to conflict with a stated value.
That surfaces a Vision-level question — does "simplicity of operation" still hold given where the project is?

The change itself stays at Design; the conflict lives one level up.
CE makes the routing legible.

**Where the model helps.** Prevents the decision from collapsing into a code-level debate (connection pooling, migration tooling) when the real question is about Vision priorities.

**Where it strains.** The trigger for the change can be Vision-level (the project is scaling, which is growth) while the change itself is Design.
That's not a failure, but it does mean classification requires reading the signal carefully.
"We need Postgres" is Design; "we're now a product that scales to enterprise" may be Vision.

---

## 2. Rewrite in a different language

**The situation.** A team has built an internal CLI in Python.
Performance has become a real problem — startup time is hurting developer experience.
A senior engineer proposes a Rust rewrite.
Another engineer thinks the problem is solvable with optimizations.

**Classification.** Design.

Language is a structural choice.
It shapes everything in the implementation and has high blast radius, but it doesn't change what success looks like or why the project exists.

**How CE routes it.** The disagreement is Design-level.
The right conversation is: what does the Vision say about performance, maintainability, and team constraints?
If the Vision lists developer experience as a success criterion, that's relevant context.
If it's silent on performance, that's a gap — and the rewrite proposal may be surfacing it.

Neither engineer is wrong to care about their level.
The one arguing for optimization is thinking implementation-first.
The one arguing for the rewrite is thinking design-first.
CE names that without making either wrong.

**Where the model helps.** Stops the debate from becoming personal.
It's not "you want to burn everything down" versus "you're avoiding the real problem."
It's a legitimate design disagreement that can be resolved by checking Vision constraints and making a structural call.

**Where it strains.** The "right" answer still requires domain judgment.
CE tells you the conversation is Design-level; it doesn't tell you whether Rust is the right call.
That's explicit in the Vision's non-goals: it's a lens, not a substitute for expertise.

---

## 3. Pivot target audience

**The situation.** A developer tool was built for indie developers — small projects, quick setup, minimal config.
The company starts getting inbound from enterprise teams.
Leadership wants to add multi-tenant support, audit logs, and SSO.
A founding engineer pushes back: "This changes what the product is."

**Classification.** Vision, possibly Charter.

The founding engineer is right that something has shifted.
The question CE asks is: does the charter still hold?
If the charter is "a tool for developers who want to move fast," enterprise features may not serve that purpose.
If it's broad enough — "a tool for developers" — then the audience pivot is Vision (what serves that purpose today has changed).

**How CE routes it.** Start at Charter.
Does "enterprise" serve the charter?
If yes, it's a Vision change — goals, success criteria, and non-goals all become candidates for revision.
If no, this is a new project, and the honest conversation is whether to fork, kill the old product, or change the charter.

**Where the model helps.** Surfaces what the founding engineer's concern actually is — not "I don't want to do the work" but "this changes the why."
That's a Charter-level argument, and it deserves Charter-level attention.
Without CE, it often collapses into a product-roadmap debate that nobody wins.

**Where it strains.** The Charter/Vision boundary is genuinely fuzzy here.
"A tool for developers who want to move fast" could stretch to include enterprise developers who want to move fast.
The model helps ask the right question; it doesn't resolve the ambiguity.
Someone still has to make the call about what "serving the charter" means — and that's a human judgment.

---

## 4. Framework choice disagreement between two senior engineers

**The situation.** Two senior engineers disagree on framework choice for a new service.
One prefers React for its ecosystem; the other prefers a leaner option, arguing that React's complexity doesn't fit the service's scope.
Both are senior; neither is obviously wrong.

**Classification.** Design.

**How CE routes it.** This is clearly a Design conversation.
CE's value here isn't classification — it's preventing the disagreement from becoming a Vision or Charter argument.
Framework choices don't change the project's purpose or what success looks like.

The right inputs are Vision constraints: does the Vision say anything about ecosystem compatibility, build-time, or team consistency?
If yes, evaluate against those.
If no, the Design conversation is between two reasonable positions with no declared tiebreaker.

That's a real outcome: CE can surface that the conflict is unresolvable at Design level because the Vision is silent on the relevant trade-off.
The resolution is either to make a Design-level call (someone decides) or to push the question up and update the Vision.

**Where the model helps.** Stops the debate from becoming a values argument.
"React is overengineered" and "React is the industry standard" are both Design-level claims.
If someone starts arguing "we shouldn't be a React shop," that's shifted to Vision, and CE surfaces that shift.

**Where it strains.** The model is neutral on who decides.
CE identifies what kind of decision this is (Design) without resolving the authority question.
That's by design — it's a non-goal — but it can leave teams with a classification and no resolution mechanism.

---

## 5. Performance optimization that conflicts with a Vision non-goal

**The situation.** Vision says: "Simplicity over performance. We optimize when users feel pain, not in anticipation of it."
An engineer opens a PR that adds an in-memory cache layer.
There's no reported user pain yet; the engineer is anticipating a load spike.

**Classification.** Implementation, but the conflict is Vision.

The cache itself is an Implementation change.
But it directly conflicts with a stated Vision non-goal.

**How CE routes it.** The PR reviewer's job is to name this clearly:
"This conflicts with the Vision's non-goal on premature optimization.
That doesn't mean the PR is wrong — it might mean the non-goal is outdated.
Which conversation should we have?"

If the non-goal still holds, the PR is closed with a clear reason.
If the load spike is real and the non-goal no longer reflects the team's priorities, that's a Vision conversation — update it first, then merge the PR.

**Where the model helps.** Gives the reviewer a frame that isn't "I don't like this" or "you're over-engineering."
It's "this conflicts with something we agreed to. Let's check whether that agreement still stands."
The conflict is surfaced, not suppressed or litigated at the wrong level.

**Where it strains.** In practice, "when users feel pain" is fuzzy.
An anticipated load spike might or might not count.
CE surfaces the tension, but the Vision artifact still has to be precise enough to be useful.
Vague Vision artifacts push ambiguity down into every implementation decision.
That's not a failure of CE — it's an argument for investing in clarity at the Vision level.

---

## What the examples show

Across all five scenarios, CE does a few things consistently:

1. **Names the level where the conflict lives.** Even when the change is at one level, the friction is often one level up.
2. **Routes discussion to the right artifact.** Design disputes reference Vision. Vision tensions check against Charter.
3. **Contains blast radius.** A design change doesn't require an existential conversation. Charter changes do. The levels earn their keep by making that obvious.

Where it strains:

- **It doesn't resolve authority.** Classification tells you what kind of decision it is, not who makes it.
- **Fuzzy artifacts push ambiguity down.** CE is only as useful as the clarity in the artifacts it points to.
- **The Charter/Vision boundary is judgment-dependent.** The model helps ask the question; it doesn't answer it.

None of these are model failures — they're honest limits, and they're consistent with CE's stated non-goals.
The model is a lens, not a substitute for the judgment you still have to bring.
