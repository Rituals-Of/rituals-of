# Publish BIAFRAL grammar across the relevant skill and contract repos

Method: none prescribed — inventory, write, PR, record.

## Intent

The BIAFRAL (Born In A Filesystem Recursing Agentic Lineages) grammar defines
how an agent derives its operational context from its working directory path.
This ritual publishes that grammar to every repo in the agent's purview where
the concept has material overlap.

## Scope

Every repo that touches working-copy type detection, branch lineage,
agent identity from path, or dashborg depth scanning.

## Steps

1. **Audit** — list repos in current purview, identify BIAFRAL overlap, rank by
   fit. Check current README depth and branch state.

2. **Write** — for placeholder repos (`worktree-stewardship`,
   `agent-branch-ownership`): write the full skill content as the primary
   publication. For existing repos (`instance-identification`,
   `dashborg-of`): append without disturbing existing content.

3. **Branch and PR** — create a `feature/biafral-grammar` (or equivalent)
   branch per repo, commit the addition atomically, push, open a PR.

4. **Push pending** — flush any repos with unpushed commits that are blocked
   by this workflow.

5. **Record evidence** — write an adoption record in the instance repo
   listing every PR URL and its target.

## Evidence format

```json
{
  "ritual": "biafral-grammar-publication",
  "performedAt": "<iso-date>",
  "prs": [
    { "repo": "<slug>", "pr": "<url>", "branch": "<branch>", "description": "<what changed>" }
  ],
  "pushed": ["<slug>"],
  "remaining": []
}
```
