# rituals-of

A public, reusable catalog of agent rituals: repeatable operating procedures
that are measured, executed, checked, and improved without embedding private
instance state.

## Ritual contract

Each ritual is a small DMAIC loop:

1. **Define** the intended invariant and scope.
2. **Measure** observable inputs and baseline state.
3. **Analyze** the gap or failure mode.
4. **Improve** with the smallest reversible change.
5. **Control** with a repeatable check, terse evidence, and an explicit owner.

Rituals are implementation-neutral where possible. Paths, owners, tokens,
private repository names, session identifiers, and machine-local configuration
belong in ignored installation data, never in this repository.

## Stewardship

The `Rituals-Of` GitHub organization is dogfood for these rules. Every ritual
added here must be executable against its own repository and must leave a
small evidence record describing what was checked and what remains unknown.
