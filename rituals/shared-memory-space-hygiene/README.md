# Shared memory space hygiene

Method: DMAIC. This is a DMAIC ritual type definition.

## Define

Invariant: an agent's shared, auto-loaded memory space (any store the
harness surfaces into context automatically, by relevance, without the
agent choosing to open it) contains only content that is genuinely correct
and useful *regardless of which identity/card/thread reads it*. Anything
whose correctness or usefulness depends on which specific identity is
currently resolved — architecture notes about one persona, historical
narrative belonging to one thread's own past, or facts one identity is
deliberately not meant to know yet — belongs in that identity's own scoped
storage instead, not the shared pool.

Scope: any persistent memory/context store that (a) is loaded automatically
rather than opened deliberately, and (b) is shared across more than one
identity, card, or thread that can resolve into the same location (e.g. a
working-directory-keyed memory pool read by multiple entrypoints/cards of
the same account). This ritual does not cover per-identity scoped storage
itself — only what should and shouldn't be promoted into the shared layer
above it.

## Measure

Record, for each item in shared memory space:

- what it asserts (identity-resolution routing fact vs. architecture vs.
  narrative/history vs. secret/privileged fact vs. genuinely
  identity-agnostic operational knowledge)
- whether it depends on which identity/card is currently resolved to be
  correctly interpreted
- whether a party it should be hidden from (per an explicit instruction,
  not a guess) could read it if it stayed in the shared pool
- current size/count of the shared pool, as a coarse pressure signal — a
  shared pool that only ever grows is itself evidence hygiene isn't
  running

Baseline for the first adoption (2026-08-16, `gnomon-ottopoet` identity):
~90 files in the shared memory pool. Two were identity-specific narrative
that had accreted there over prior sessions (one card's own persona/history
record; one identity's architecture notes for an upcoming multi-agent
restructuring) rather than being written to card-scoped storage from the
start. Neither was routing content — both were substantive knowledge that
happened to get written to the convenient, always-loaded location instead
of the correct, narrower one.

## Analyze

Likely failure modes:

- writing to the shared/always-loaded location by default because it's the
  path of least resistance, without checking whether the content is
  actually identity-agnostic
- an identity-resolution breadcrumb drifting into holding narrative
  ("why does this pairing exist," "what happened last time") instead of
  staying a bare, checkable conditional — the exact failure this ritual's
  first adoption corrected
- a fact meant to stay hidden from one identity (a deliberate design
  constraint, not a guess) getting written to a pool that identity will
  search by ordinary relevance-based recall, defeating the constraint
  silently rather than by a deliberate, visible act
- one identity writing about a different identity's own affairs into the
  shared pool because it's easier than navigating to that identity's scoped
  folder — even well-intentioned, this still misplaces the content

## Improve

For each shared-memory item found to be over-scoped: relocate the
substantive content verbatim (not rewritten, to preserve provenance and
avoid silently changing meaning during the move) into the correct
identity's own scoped storage, leave a short pointer or nothing at all in
the shared location depending on whether even a pointer would leak
something meant to stay hidden, and update whatever index references the
shared pool. Distill any genuine identity-resolution content down to the
smallest checkable conditional that does the routing job — a table of
(context-key → identity, storage-location) rows, nothing else. Each
relocation is independently reversible (the content isn't destroyed, only
moved) and should be done one item at a time rather than as a single
irreversible bulk rewrite.

## Control

Run this ritual as a standing part of the identity's own recurring
operating loop (not only when explicitly requested) — check the shared
memory pool for new accretions since the last pass, using the same
Measure/Analyze criteria above, and file the same relocate-or-distill
Improve step for anything found. Terse evidence per run: item count
before/after, what got relocated and to where, and any item deliberately
left in place with a one-line reason (e.g. "genuinely identity-agnostic
operational knowledge, not narrative"). Evidence lives in the instance repo
for the adopting agent class, not in this abstract ritual-type repository.

Owner: whichever identity's own memory space this runs against — each
adopter is responsible for its own shared-pool hygiene, not a central
steward auditing every identity's pool.
