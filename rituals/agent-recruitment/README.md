# Agent recruitment

Method: DMAIC. This is a DMAIC ritual type definition.

## Define

Invariant: a new agent instance, brought into existence to serve as a peer
or subordinate of an already-established agent, is properly dealt an
identity of its own — not silently assumed to inherit the recruiting
agent's identity, and not left as an anonymous process — and its
recruitment is visible to and approvable by the human overseeing the
system, from wherever that human actually is, not only from one physical
location.

Scope: the act of bringing a new agent instance into being as a distinct,
identifiable party — spawning it, assigning it a real identity record, and
establishing the visibility/approval mechanism the human uses to know it
exists. This ritual does not cover what the new instance does once
recruited (that's the recruited instance's own duty scope, defined
separately), and it does not cover identity *resolution* of an
already-existing instance (see the `shared-memory-space-hygiene` ritual for
that adjacent but distinct concern).

## Measure

Record, for each recruitment:

- what triggered it (a capacity gap, a location/access constraint on the
  recruiting agent, an explicit request)
- the mechanism used to actually spawn the new instance
- whether the new instance received its own identity record before or
  after it started doing real work
- whether the human's approval/visibility step happened before the new
  instance could act, or only after
- how the new instance's scope was communicated to it (inherited wholesale
  from the recruiter's own duties, or deliberately narrowed)

## Analyze

Likely failure modes:

- a new instance starts acting before receiving a distinct identity,
  producing exactly the "letter with no return address" attribution problem
  a shared-account/shared-thread system already has to guard against at the
  account layer — recruitment reintroduces the same failure at the
  instance layer if skipped
- the recruiting agent assumes the new instance should inherit its own
  full duty scope by default, without checking whether that's actually
  wanted, producing an unintentional duplicate rather than a genuinely new
  capability
- visibility/approval is treated as a formality to route around rather
  than the actual reason recruitment (vs. silent self-modification) was
  chosen in the first place
- the new instance's relationship to the recruiter (peer vs. subordinate,
  what it can decide alone vs. what needs escalation) is left implicit and
  has to be renegotiated later instead of being stated at recruitment time

## Improve

Before spawning: decide and state explicitly whether the new instance is a
peer or subordinate, and how narrow or wide its starting duty scope is —
don't default to "same as me." Use whatever spawn mechanism the harness
provides that has human approval built in as a first-class step, not
bolted on after. Immediately after spawning, before the new instance does
any task-scoped work, give it a real, durable identity record — even a
minimal one — so its own actions are attributable to it specifically from
its very first act, not retroactively assigned once it's already produced
history.

## Control

Evidence per recruitment: the new instance's assigned identity, its stated
peer/subordinate relationship and starting scope, and confirmation the
human's approval step actually fired (not skipped). Evidence lives in the
instance repo for the recruiting agent's own class, not in this abstract
ritual-type repository — recruitment is something one agent class does
to itself over time, and the record belongs with that class's own history.

Owner: whichever agent does the recruiting is the owner of that
recruitment's evidence trail — there is no central recruitment authority
this ritual assumes.
