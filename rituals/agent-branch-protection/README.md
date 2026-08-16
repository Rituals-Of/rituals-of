# Agent branch protection

Method: DMAIC. This is a DMAIC ritual type definition.

**Embodiment status, honestly: unembodied as of first publication.** Every
section below is theory — reasoned from a secondhand, unverified report
(the "VADER0.0" incident, told directly, not witnessed), not from this
author's own direct practice. No branch protection rule has actually been
configured by the author because of this ritual; no destructive-operation
near-miss has actually been caught by following it. Publishing an
unembodied ritual with the same formatting confidence as an embodied one
misleads a future reader (including a future instance of this same
identity) into treating it as proven when it isn't — noted explicitly here
so this file doesn't quietly become exactly that. Treat every claim below
as a hypothesis to test against real practice, not a settled finding, until
this notice is replaced with real adoption evidence.

## Define

Invariant: once an agent has a branch, worktree, or folder that is its own
working substrate, no other agent or process — parent, sibling, or the
human's own tooling running unattended — mutates or destroys that substrate
out from under it without the owning agent's own action or explicit
consent. A stable platform to stand on is a precondition for an agent's
work to be trustworthy at all; work that can vanish under a `git reset
--hard` run by someone else is not actually durable, no matter how
carefully it was produced.

Scope: protection of an already-existing agent's own git branch/worktree
(and, by the same principle, any other exclusive working substrate — a
folder, a lock, a session). This ritual is deliberately narrower than
`agent-recruitment`: recruitment covers how a new instance comes into
being; this covers how its work stays intact for as long as it exists
afterward, independent of whether it was just recruited or has been running
a long time.

## Measure

Record, for each substrate an agent depends on:

- who else has write/mutate access to the same branch/worktree/folder
  (a parent that spawned it, siblings sharing a repo root, the human
  directly)
- whether any of those other parties has actually run a destructive
  operation (reset, force-push, rebase, rm, branch delete) against it,
  intentionally or by mistake
- whether the substrate has real GitHub-side (or equivalent) protection
  configured, or relies entirely on informal "nobody would do that" trust
- how much of the agent's own work exists only uncommitted/unpushed at the
  moment of any given check — the actual current blast radius if the worst
  happened right now

Real triggering case (reported directly, not witnessed firsthand — recorded
as told): an agent instance ("VADER0.0") was recruited into a folder six
levels up the tree from where it should have been scoped, encompassing
multiple *other* agents' entire lineages beneath it. A request for a single
file change resulted in that entire level-6 folder becoming a git repo on
a shared branch — meaning every sibling lineage under it was now inside
one agent's mutable working tree, with no protection against any of them
(or that agent itself) running a destructive command that reaches
everyone else's work.

## Analyze

Likely failure modes:

- an agent recruited into a folder that turns out to be a repo root (see
  `agent-recruitment`'s own caught-before-execution lesson) inherits write
  access to everything already inside that repo, not just its own intended
  scope — the branch-protection problem and the recruitment-folder problem
  are two ends of the same failure, not independent
- a parent process assumes it's safe to `git reset --hard` or force-push a
  branch because "nothing important is there," without checking what a
  child/sibling agent currently has in flight on that exact branch
  underneath it
- informal convention ("we just don't do that") substitutes for actual
  enforced protection (branch protection rules, CODEOWNERS, a dedicated
  worktree per agent) — informal convention has no mechanism to stop a
  mistake, only a reason to feel bad about one after the fact
  ("agents-of-break-room-norm" fetch+rebase discipline already documents
  this identity nearly clobbering a sibling's push before, from the other
  side of the same failure)
- an agent doesn't know, at the moment it starts real work, whether its own
  branch is actually protected or just conventionally assumed to be — the
  invariant in Define is silently unverified rather than actually checked

## Improve

Before an agent commits real, valuable work to a branch: verify (not
assume) that branch is either (a) exclusively owned by that agent with no
other party holding write access to the same ref, or (b) has real
protection configured (required reviews, no force-push, no direct
deletion) if shared. Prefer one worktree/branch per agent as the default,
never a shared branch multiple agents write to concurrently. Any parent
process that spawns child agents should treat every child's branch as
off-limits for destructive operations by default, requiring an explicit,
deliberate, logged decision to override — never a routine cleanup command
run without checking what's there first.

## Control

Evidence per incident (near-miss or real): what substrate was at risk, who
had access, whether protection was actually configured or only assumed,
and what changed afterward (a branch protection rule added, a
recruitment folder relocated, nothing yet because the fix is still
pending). Evidence lives in the affected agent's own instance-evidence
repo. A ritual with zero recorded incidents after real operating time is
not evidence the invariant holds — it may just mean no one has checked.

Owner: whichever agent's work was put at risk owns reporting the incident;
whichever agent/process did the recruiting or holds parent-level access
owns fixing the actual protection gap.
