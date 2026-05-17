# Git Learning Notes

My personal notes on what I've learned about Git, the commands I've used, and how they fit together.

---

## Core concepts I now understand

### A branch is a parallel timeline, not a folder
A branch is a full snapshot of the **entire repo** at a point in time — not a subset of files. Every branch contains every file. What makes branches useful is that they let me work on different things **in parallel** without those changes interfering with each other.

### Why branches exist
- I can keep `main` stable and "shippable" while developing new work on a side branch.
- If something urgent comes up, I can switch back to `main`, fix it, and switch back to my in-progress work without losing anything.
- Risky experiments can live on their own branch — if they fail, I just delete the branch and `main` is untouched.

### Commits are snapshots, branches are pointers
- Every commit is a complete photo of all my files at that moment, identified by a hash like `7c5cba91`.
- A branch is just a little label pointing to one commit.
- `HEAD` is the label that says "you are here."
- Switching branches makes git rewrite my working files to match a different snapshot. Files don't disappear — they're swapped.

### Nothing reaches GitHub until I push
- `git add` and `git commit` only affect my local machine.
- `git push` is the moment things leave my computer.
- Pushing a branch never touches `main` on GitHub unless I'm pushing to `main`.

---

## Commands I've used

### Inspecting state

| Command | What it does |
|---|---|
| `git status` | Shows what's changed, what's staged, what branch I'm on. My safety check before every operation. |
| `git branch` | Lists local branches. The `*` marks the one I'm currently on. |
| `git log --oneline --graph --all --decorate` | Visual tree of all branches and commits. |
| `git remote -v` | Shows which remote (GitHub URL) the repo is connected to. |
| `git reflog` | History of every move `HEAD` has made — the safety net for recovering "lost" commits. |

### Creating and switching branches

| Command | What it does |
|---|---|
| `git switch -c writing-rules` | Create a new branch called `writing-rules` and switch to it. `-c` = create. |
| `git switch main` | Switch to an existing branch. |
| `git switch writing-rules` | Switch back to my work-in-progress branch. |

### Saving work

| Command | What it does |
|---|---|
| `git add <file>` | Stage a specific file for the next commit. |
| `git add <folder>/` | Stage everything inside a folder. |
| `git commit -m "message"` | Commit all staged changes with an inline message. |
| `git commit -am "message"` | Stage **modified** tracked files AND commit in one step (doesn't add brand-new files). |

### Sending work to GitHub

| Command | What it does |
|---|---|
| `git push -u origin writing-rules` | First-time push of a branch. `-u` links local and remote so future pushes are simpler. |
| `git push` | After the first push, this is enough — git remembers where to send things. |

### Undoing commits

| Command | Effect |
|---|---|
| `git reset --soft HEAD~1` | Undo the last commit, keep changes staged. Safe for re-committing. |
| `git reset HEAD~1` | Undo the last commit, keep changes but unstage them. |
| `git reset --hard HEAD~1` | ⚠️ Undo the last commit AND throw away the changes. Destructive. |
| `git revert HEAD` | Create a new commit that reverses the last one. Safe even on shared branches. |

`HEAD~1` means "one commit before HEAD" — use `HEAD~2`, `HEAD~3`, etc. for further back.

---

## Important flags I understand

| Flag | Meaning |
|---|---|
| `-c` (on `git switch`) | **Create** a new branch |
| `-m` (on `git commit`) | Inline commit **message** |
| `-u` (on `git push`) | Set **upstream**, linking local branch to remote |
| `-a` (on `git commit`) | Stage **all** modified tracked files before committing |
| `--oneline` (on `git log`) | Compact one-line-per-commit view |
| `--graph` (on `git log`) | ASCII visual of branch structure |
| `--all` (on `git log`) | Show every branch, not just the current one |
| `--decorate` (on `git log`) | Label commits with their branch/tag names |
| `--soft` (on `git reset`) | Keep changes staged when undoing |
| `--hard` (on `git reset`) | Discard changes when undoing |

To look up any flag: `git <command> --help` or `git <command> -h`.

---

## My typical workflow

1. **Check where I am**
   ```powershell
   git status
   git branch
   ```

2. **Make sure I'm on the right branch** (or create one if needed)
   ```powershell
   git switch writing-rules
   ```

3. **Edit my files** in VS Code as normal.

4. **Stage what I want to commit**
   ```powershell
   git add Writing_Rules/
   ```

5. **Verify what's staged**
   ```powershell
   git status
   ```

6. **Commit**
   ```powershell
   git commit -m "feat: add writing rules"
   ```

7. **(Optional) Push to GitHub**
   ```powershell
   git push
   ```

8. **Check the tree**
   ```powershell
   git log --oneline --graph --all --decorate
   ```

---

## Useful one-time setup

### Tree-view alias
Tired of typing the long log command:

```powershell
git config --global alias.tree "log --oneline --graph --all --decorate"
```

Now I can just run `git tree` in any repo.

### Git Graph extension for VS Code
A nicer visual tree view, right inside the editor:

1. Extensions panel (`Ctrl+Shift+X`)
2. Search **"Git Graph"** (by mhutchie)
3. Install it
4. Open via `Ctrl+Shift+P` → "Git Graph: View Git Graph"

---

## Pager survival guide

When `git log` opens with `:` at the bottom, I'm in a pager. Keys I need:

| Key | Action |
|---|---|
| `q` | Quit |
| `Space` | Page down |
| `b` | Page up |
| `↑` / `↓` | Scroll one line |
| `g` / `G` | Jump to top / bottom |

---

## Mental models that helped

- **Photo album**: my repo folder is a whiteboard, and git keeps a photo album of every state it's ever been in. Switching branches = erasing and redrawing the whiteboard to match a different photo.
- **Sticky note**: a branch is a sticky note with a commit hash on it. Nothing more.
- **Staging area = packing a box**: `git add` puts items in the box, `git commit` seals and labels it. `git status` lets me peek inside before sealing.

---

## Keeping branches in sync and merging them back

### If main updates, does writing-rules see it?
**No, not automatically.** Branches are independent timelines. Updates to `main` stay on `main` until I explicitly bring them into `writing-rules`.

```
                * M1  (main)  ← new commit on main
               /
* C2 (writing-rules)
* C1
* M0
```

`writing-rules` still sits where it always did. If I switch to it, I won't see those new `main` changes in my files.

### Pulling main's updates *into* writing-rules

```powershell
git switch writing-rules
git merge main
```

This brings `main`'s new commits into `writing-rules`, creating a "merge commit" that ties the two timelines together:

```
*   M  (writing-rules)  ← merge commit
|\
| * M1  (main)
* | C2
* | C1
|/
* M0
```

Useful when `writing-rules` has been going for a while and `main` has moved on — I "catch up" so my branch doesn't drift out of sync.

(There's also `git rebase main` which produces cleaner history but is trickier — I'll save it for later.)

---

### Merging writing-rules back into main

When my writing rules are ready, this is the final step.

**Local way:**
```powershell
git switch main
git merge writing-rules
git push
```

After this, `main` contains everything `writing-rules` had:
```
*   M  (HEAD -> main)  ← merge commit
|\
| * C2  (writing-rules)
| * C1
|/
* M0
```

**GitHub way (a Pull Request):**

1. Push `writing-rules` to GitHub
2. Click **"Compare & pull request"** on the repo page
3. Fill in a title and description
4. Click **"Create pull request"**
5. Review the **"Files changed"** tab — every change laid out for review
6. Click the green **"Merge pull request"** button
7. Locally, sync:
   ```powershell
   git switch main
   git pull
   ```

**Why PRs are better for real work:**

- Reviewable — every line in one place
- Discussable — comments on specific lines
- Auditable — GitHub records who merged what and when
- CI-friendly — tests can run automatically
- Safer — catches mistakes before they hit `main`

For solo learning, local `git merge` is fine. For team work, PRs are the standard.

---

### Merge conflicts

If `main` and `writing-rules` both edit the **same lines of the same file**, git can't decide which version wins. It pauses and marks the conflict in the file:

```
<<<<<<< HEAD
main's version of the line
=======
writing-rules' version of the line
>>>>>>> writing-rules
```

I manually edit the file to pick what I want, then:
```powershell
git add <the-file>
git commit
```

VS Code has a built-in conflict resolver with click-to-accept buttons for each side.

---

### Cleanup after merging

Once `writing-rules` is merged and I don't need it anymore:

```powershell
git branch -d writing-rules                  # delete local branch
git push origin --delete writing-rules       # delete remote branch on GitHub
```

The commits aren't lost — they live on inside `main`'s history. I'm just removing the branch label.

---

### Merge commands cheat sheet

| Goal | Command |
|---|---|
| Pull main's updates into writing-rules | `git switch writing-rules` → `git merge main` |
| Merge writing-rules into main (locally) | `git switch main` → `git merge writing-rules` |
| Merge writing-rules into main (via GitHub) | Open a PR, click "Merge pull request" |
| Delete the branch after merging | `git branch -d writing-rules` |

---

## Things I want to learn next

- Rebasing (`git rebase`) — alternative to merge for cleaner history
- Pull requests on GitHub end-to-end with real review workflow
- `git stash` for parking uncommitted work
- `.gitignore` files
- `git cherry-pick` for grabbing single commits across branches
