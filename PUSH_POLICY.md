# Push Policy for Cowork-Managed Resume Repo

## Why lock files happen

When Claude (Cowork) commits files from the sandbox, git writes a `HEAD.lock`
(and sometimes `REBASE_HEAD.lock`) to `.git/`. The sandbox process can't clean
these up after it exits. They're harmless leftovers, but they block any
subsequent rebase until you remove them.

## Standard push command (use this every time)

```bash
cd /Users/abose1/69df216bc598c596402998e7
rm -f .git/HEAD.lock .git/REBASE_HEAD.lock
git pull github main --rebase --autostash && git push github master:main
git pull origin master --rebase --autostash && git push origin master
```

Run it as a block — copy-paste all four lines at once.

**What each part does:**
- `rm -f` — removes stale lock files (the `-f` flag means no error if they don't exist)
- `--rebase` — replays your local commits on top of any remote changes
- `--autostash` — automatically stashes/restores dirty working tree around the rebase

## If a push still fails

Run `git status` and look for:

| Symptom | Fix |
|---|---|
| `Staged deletions` of your new .tex files | `git restore --staged .` |
| `deleted` in unstaged (working tree) | `git restore <filename>` |
| `REBASE_HEAD.lock` after a crash | `rm -f .git/REBASE_HEAD.lock` |
| Diverged branches on both remotes | Run the pull+push for each remote separately |

## Skills Match Summary (generate after every tailored resume)

After displaying the GitHub push command, Claude must generate a skills match table comparing the JD requirements against Avishek's confirmed skill set. Rules:

- List up to 20 terms
- Two tiers:
  - **Exact match** — the term appears verbatim (or near-verbatim) in both the JD and Avishek's confirmed skills/experience
  - **Relevant match** — the JD requires a concept that Avishek covers with a closely related skill or experience (note the mapping)
- Source Avishek's skills only from `main_original.tex` and the Key Facts in `resume_tailoring_policy.md` — do not credit skills not confirmed there
- Format as a markdown table:

| # | JD Term | Match Type | Avishek's Coverage |
|---|---|---|---|
| 1 | e.g. RAG | Exact | LlamaIndex-based RAG platform at Tegna, 100K+ daily requests |
| 2 | e.g. Kubernetes | Relevant | Docker + Terraform containerization and IaC (no direct K8s, but orchestration-adjacent) |

**Print this table directly in the chat response. Do not save it to any file.**

## Overleaf sync (alternative to git)

If git pushes keep failing, you can always sync manually:
1. Open https://www.overleaf.com/project/69df216bc598c596402998e7
2. Menu → Git → Pull from GitHub
3. Edit and download PDF directly from Overleaf
