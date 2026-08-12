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

The `Rituals-Of` GitHub organization stewards this contract. Ritual-type
definitions live here. Evidence records, adoptions, and performed instances
belong in a separate instance repo named after the agent class:

```
Rituals-Of/rituals-of   ← this repo: abstract class, schema, ritual types
Rituals-Of/walrus-man   ← walrus-man agent instances and evidence
Rituals-Of/<other>      ← any other agent class's instance collection
```

Every ritual type added here must be executable against this repository's own
structure. Instance evidence of that execution goes in the corresponding
instance repo, not here.
