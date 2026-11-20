# Undoing Changes & Stashing

## 1. Git Revert

**What it is:** Revert creates a new commit that reverses the changes introduced by an earlier commit.

```bash
git revert <commit-hash>
```

**Key points:**
- Does not remove the original commit.
- Preserves existing history.
- Suitable for undoing changes in shared branches.

**Remember:** Revert undoes changes by adding another commit.

## 2. Git Reset

**What it is:** Reset moves the current branch pointer to another commit and changes the staging area and working directory depending on the selected option.

### Reset Options

| Option | Moves HEAD | Resets staging | Resets working files |
|---|---|---|---|
| `--soft` | Yes | No | No |
| `--mixed` | Yes | Yes | No |
| `--hard` | Yes | Yes | Yes |

**Examples:**

```bash
git reset --soft HEAD~1
git reset --mixed HEAD~1
git reset --hard HEAD~1
```

**Remember:**
- `--soft`: removes the latest commit but keeps changes staged.
- `--mixed`: removes the latest commit and unstages changes.
- `--hard`: resets the commit, staging area, and tracked working files.

**Warning:** `--hard` can permanently discard uncommitted changes. Use it carefully.

## 3. Revert vs Reset

| Revert | Reset |
|---|---|
| Creates a new commit | Moves the branch pointer |
| Preserves previous history | Changes branch history |
| Safer for shared branches | Mainly useful for local history |
| Reverses a commit's changes | Can remove commits from the current branch history |

**Remember:** Prefer revert when undoing changes already shared with others.

## 4. Git Stash

**What it is:** Stash temporarily saves local changes so you can work on something else without committing them.

### Essential Commands

```bash
git stash
git stash list
git stash pop
git stash apply
git stash drop
git stash clear
```

### Stash Differences

| Command | Purpose |
|---|---|
| `git stash` | Save current tracked changes |
| `git stash -u` | Also include untracked files |
| `git stash list` | List saved stashes |
| `git stash pop` | Apply and remove the latest stash |
| `git stash apply` | Apply without removing the stash |
| `git stash drop` | Remove a selected stash |
| `git stash clear` | Remove all stashes |

**Practical example:**

```bash
git stash
git switch main

# Work on another task

git switch feature-login
git stash pop
```

**Remember:** Use stash for temporary work that is not ready to become a commit.

## 5. Quick Decision Guide

| Situation | Command |
|---|---|
| Undo a commit on a shared branch | `git revert` |
| Undo a local commit but keep changes staged | `git reset --soft` |
| Undo a local commit and unstage changes | `git reset --mixed` |
| Discard local tracked changes and reset to a commit | `git reset --hard` |
| Apply one commit from another branch | `git cherry-pick` |
| Temporarily save unfinished changes | `git stash` |
| Integrate another branch while preserving its history | `git merge` |
| Replay commits on a new base | `git rebase` |

## Final Takeaway

Understand what each command changes before using it. In particular, know the difference between changing history (`reset` and `rebase`) and adding new history (`revert` and `merge`).