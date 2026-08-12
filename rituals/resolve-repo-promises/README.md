# Resolve repo promises

Method: none prescribed — adapt to each entry's state.

## Intent

Every `promise-only` entry in the Dashborg repo-promises panel is a filesystem
path that claims to represent a GitHub org/repo but has no `.git` behind it.
This ritual resolves that gap by grounding each promise in actual git and remote
state.

## Scope

The repo-promises panel at `http://127.0.0.1:43101/` (or any local Dashborg
instance). One execution per session of unresolved promises.

## Steps

1. **Fetch current promises** from `/api/snapshot` and list all entries where
   `status !== "honest"`.

2. **For each unresolved entry**, determine ground truth:
   - Run `gh repo view <implied-slug>` — does the remote exist?
   - Check whether the directory has a `.git` — does a local repo exist?

3. **Resolve by state:**

   | State | Remote exists? | Action |
   |---|---|---|
   | `promise-only` | yes | `git clone <remote> <path>` |
   | `promise-only` | no | `git init`, commit a seed file, `gh repo create <slug> --public --source=. --push` |
   | `local-only` | yes | `git remote add origin <remote-url>; git push -u origin <branch>` |
   | `local-only` | no | `gh repo create <slug> --public --source=. --push` |
   | `remote-mismatch` | — | investigate: either move the directory or update the remote |

4. **After each resolution**, wait one cache cycle (5 s) and re-fetch the
   snapshot to confirm the entry moved to `honest`.

5. **Record evidence** in `adoptions/resolve-repo-promises-<date>.json` inside
   the `rituals-of` checkout listing each resolved slug, its prior state, and
   the resolution action taken.

## Evidence format

```json
{
  "ritual": "resolve-repo-promises",
  "performedAt": "<iso-date>",
  "resolved": [
    { "slug": "<ghorg>/<repo>", "priorState": "promise-only", "action": "created-remote", "remote": "<url>" }
  ],
  "remaining": []
}
```
