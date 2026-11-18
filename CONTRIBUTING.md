# Contributing

How we work together on this repo. Keep it simple, and ask in the group chat if anything is unclear.

## 1. Get the repo

```bash
git clone https://github.com/AlzGraph-Research/Graph-Based-Multi-Agent-System-for-Alzheimer-s-Desease.git
cd Graph-Based-Multi-Agent-System-for-Alzheimer-s-Desease
```

Ask the repo owner to add you as a collaborator (Settings → Collaborators) so you can push branches.

## 2. Workflow: never push directly to `main`

`main` must always work, because it is what we deploy and demo. All work goes through a branch and a pull request.

```bash
# 1. Start from an up-to-date main
git switch main
git pull

# 2. Create a branch for your task
git switch -c feat/pubmed-agent

# 3. Work, then commit small logical steps
git add <files>
git commit -m "feat(agents): add PubMed literature search tool"

# 4. Push your branch
git push -u origin feat/pubmed-agent

# 5. Open a pull request on GitHub into main
```

### Keeping your branch up to date

If `main` moved while you were working:

```bash
git switch main
git pull
git switch feat/pubmed-agent
git merge main        # resolve conflicts if any, then commit
```

## 3. Branch names

`<type>/<short-description>`, lowercase, with dashes.

| Type | Use for | Example |
|---|---|---|
| `feat/` | New feature | `feat/string-agent` |
| `fix/` | Bug fix | `fix/graph-merge-duplicates` |
| `docs/` | Documentation only | `docs/update-readme` |
| `refactor/` | Code restructure, no behaviour change | `refactor/ranking-module` |
| `exp/` | Experiments, notebooks | `exp/node2vec-link-prediction` |
| `chore/` | Setup, dependencies, config | `chore/add-requirements` |

## 4. Commit messages

Format: `<type>(<scope>): <what you did>`, written in the imperative ("add", not "added").

```
feat(agents): add Open Targets disease–gene agent
fix(graph): remove duplicate protein nodes after merge
docs(readme): describe evaluation method
```

Scopes we expect to use: `agents`, `graph`, `ranking`, `eval`, `app`, `data`, `docs`.

## 5. Pull requests

- Keep PRs small and focused on one task.
- Fill in the PR template: what it does, how you tested it.
- **At least one teammate reviews and approves** before merging.
- Merge with **Squash and merge**, then delete the branch.
- Link the issue it closes, e.g. `Closes #12`.

## 6. Tasks and issues

- Every task is a GitHub **Issue**. Assign yourself before you start, so two people don't do the same work.
- Use labels such as `agents`, `graph`, `evaluation`, `app`, `docs` and `bug`.

## 7. Never commit

- API keys, tokens or `.env` files. Secrets will be shared privately; how we store them will be decided later.
- Large raw data downloads. Commit the script that downloads them, not the data.
- Notebook outputs with huge images or data. Clear outputs before committing when possible.

If you commit a secret by mistake, tell the team immediately and **revoke the key**. Deleting the commit is not enough.
