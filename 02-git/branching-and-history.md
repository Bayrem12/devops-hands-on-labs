# Git Branching & History Management

## 1. Merge

**What it is:** Merge integrates changes from one branch into another.

**Practical example:**

```bash
git switch main
git merge feature-login
```

**Key points:**
- Combines changes from two branches.
- May create a merge commit.
- Can produce conflicts that need manual resolution.

**Remember:** Merge preserves the existing branch history.

## 2. Rebase

**What it is:** Rebase moves or replays commits onto a different base commit.

**Practical example:**

```bash
git switch feature-login
git rebase main
```

**Key points:**
- Replays your branch commits on top of another branch.
- Creates new commit IDs for the replayed commits.
- Can produce conflicts that need manual resolution.

**Remember:** Rebase creates a more linear history by replaying commits.

**Important:** Avoid rebasing shared commits that other people may already depend on.

## 3. Merge vs Rebase

| Merge | Rebase |
|---|---|
| Combines branch histories | Replays commits |
| May create a merge commit | Creates new commit IDs |
| Preserves branch history | Produces a linear history |
| Does not rewrite existing commits | Rewrites the replayed commits |

## 4. Interactive Rebase

**What it is:** Interactive rebase lets you edit, reorder, combine, or remove commits.

```bash
git rebase -i HEAD~4
```

Common actions:

| Action | Purpose |
|---|---|
| `pick` | Keep the commit |
| `reword` | Change its commit message |
| `edit` | Stop to modify the commit |
| `squash` | Combine with the previous commit |
| `fixup` | Combine and discard its message |
| `drop` | Remove the commit |

**Remember:** Interactive rebase is useful for cleaning up local commit history before sharing it.

## 5. Cherry-pick

**What it is:** Cherry-pick applies the changes introduced by a specific commit to your current branch.

```bash
git switch main
git cherry-pick <commit-hash>
```

**Key points:**
- Applies a selected commit without merging the entire source branch.
- Creates a new commit on the current branch.
- May produce conflicts.

**Remember:** Use cherry-pick when you need one specific commit from another branch.