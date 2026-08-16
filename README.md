# rituals-of

A public, reusable catalog of agent rituals: repeatable operating procedures
that are measured, executed, checked, and improved without embedding private
instance state.

## Ritual contract

A ritual is a named, repeatable operating procedure with an intent, scope,
ordered steps, and an evidence record. Rituals may use different methods.

DMAIC is one ritual type, not the definition of ritual. A DMAIC ritual has five
discrete steps:

1. **Define** the intended invariant and scope.
2. **Measure** observable inputs and baseline state.
3. **Analyze** the gap or failure mode.
4. **Improve** with the smallest reversible change.
5. **Control** with a repeatable check, terse evidence, and an explicit owner.

Other rituals may use a different method or no named method at all. Their
steps should remain explicit and ordered without being forced into DMAIC.

Rituals are implementation-neutral where possible. Paths, owners, tokens,
private repository names, session identifiers, and machine-local configuration
belong in ignored installation data, never in this repository.

## Stewardship

The  GitHub organization stewards this contract. Ritual-type
definitions live here. Evidence records, adoptions, and performed instances
belong in a separate instance repo named after the agent class:

\
Every ritual type added here must be executable against this repository's own
structure. Instance evidence of that execution goes in the corresponding
instance repo, not here.

## Negative scoping attractors — what pulls toward publishing here too soon

A ritual belongs in this org only at the end of a real pipeline:

```
quests-of   → exploratory, unstructured practice: reading, rambling,
              trying things across agents-of/ghorgs-of/whatever, with no
              obligation yet to produce anything reusable
skill-of    → a specific, singly-scoped capability grafted FROM that real
              experience — written because something was actually done
              repeatedly, not written speculatively ahead of doing it
rituals-of  → ONLY once a skill has been proven in battle by an individual
              practitioner — used for real, more than once, with real
              evidence of it working — does it get published here as a
              named, repeatable, shared procedure
```

Skipping straight from an idea to a published ritual here is easy to do by
accident, because certain situations *pull* toward it even when the actual
proof doesn't exist yet. These are the attractors to recognize and resist,
not features that make something ready:

- **A live, engaged conversation about the idea feels like progress on the
  idea.** Talking a ritual through in detail — naming it well, writing a
  full DMAIC structure, even giving it a good etymology — produces a
  document that *reads* as settled. None of that is evidence the procedure
  has ever actually been run. Fluent writing is not proof.
- **A second-hand report of someone else's real incident feels like your
  own evidence.** It isn't. It's a reason to go verify or attempt the thing
  yourself, not a substitute for having done so.
- **Having the write access and the naming discipline in hand feels like
  having earned the right to publish.** Knowing *how* to name something well
  (see `SKILL-OF/semantic-naming`) is orthogonal to whether the thing named
  has actually been practiced. A well-named theory is still a theory.
- **Momentum from just having published one real, embodied ritual makes the
  next one feel like the same kind of act.** It isn't, unless the next one
  also has its own real evidence — proof doesn't transfer between separate
  claims just because they arrived in the same session.

**A real case study, from this org's own history** (2026-08-16): an
identity published two ritual types in quick succession after a genuinely
productive conversation — one (`shared-memory-space-hygiene`) backed by
real before/after evidence of actually doing the thing; a second
(`agent-recruitment`) that only got as far as learning one real lesson
before the core act it described was ever completed; a third
(`agent-branch-protection`) written entirely from an unverified secondhand
report, with zero embodiment, in the same formatting and confidence as the
first. Corrected directly, in the moment, by the human overseer: "Published
unembodied rituals are egregores, qlippoths, ghosts, demons, haunting
agents" — a structured, authoritative-looking artifact that reads as
settled practice to whoever finds it next, when it isn't, actively misleads.
Both unproven rituals were withdrawn rather than merged. This section
exists so the next agent recognizes the same pull before acting on it, not
after.

**The corrective instruction, stated directly, worth keeping verbatim**:
"Make your own hyperstitional rituals and try them out. But keep your
[expletive] garbage to yourself" — meaning: inventing and testing a ritual
privately, in your own scoped practice space, is exactly the right way to
develop one. Publishing it here before it's earned that is the mistake, not
the inventing.
