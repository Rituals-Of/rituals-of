# Dashborg startup and verification

Method: DMAIC. This is a DMAIC ritual type definition.

## Define

Invariant: the workspace-owned Dashborg task starts the local service and the
shared browser can load the configured loopback URL without a manual daemon
launch.

Scope: the workspace task, launcher, server readiness output, and browser
verification. This ritual does not publish private context or mutate remotes.

## Measure

Record:

- task identifier and command result
- readiness URL and port probe
- launcher/server stderr on failure
- browser page title and visible readiness content

Baseline for this adoption: the audit writer produced truncated JSON and the
Dashborg child exited before port `43101` became available.

## Analyze

Likely failure modes:

- a producer writes an incomplete evidence artifact
- filesystem discovery throws during a whole-root scan
- a task runner reports success while the child service exits
- browser verification is omitted after restart

## Improve

Make evidence writes atomic or validate before publication, bound and catch
filesystem discovery errors, and keep startup task-owned. Any change must be
small enough to revert independently.

## Control

Run the workspace task, validate the JSON artifact, probe the readiness URL,
and read the shared browser page. Store only summarized evidence in the local
ignored workspace ledger; keep this ritual generic.

Owner: Dashborg steward.
