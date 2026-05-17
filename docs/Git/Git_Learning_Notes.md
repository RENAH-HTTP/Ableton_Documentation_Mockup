# Git Notes

Stuff I actually did and understand :)

---

## Mental model

- branch = full snapshot of repo, not a folder...
- commit = photo of every file at one moment, has a hash
- branch label = sticky note pointing at one commit
- `HEAD` = "you are here"
- switch branch → files swap to match that snapshot. nothing is lost.
- nothing reaches GitHub until `git push`

---

## Commands I used

### inspecting
```
git status         # what changed, what's staged, which branch
git branch         # list branches, * = current
git log --oneline --graph --all --decorate   # tree view
git log -n 3       # last 3 commits
```

press `q` to exit pager

### creating + switching branches
```
git switch -c writing-rules   # -c = create new branch
git switch main               # switch to existing
git switch writing-rules
```

### saving work (2 steps)
```
git add Writing_Rules/Writing_Rules.md   # stage
git commit -m "feat: add more writing rules"   # commit
```

I forgot to stage once and got "nothing to commit, working tree clean"
`git status` shows it. red = unstaged, green = staged.

### unstaging
```
git restore --staged <file>   # undo a git add
```

### undoing commits
```
git reset --soft HEAD~1    # undo last commit, keep changes staged
git reset --hard HEAD~1    # undo last commit + delete changes 
```

`HEAD~1` = one commit back

### pushing
```
git push -u origin writing-rules   # first push: -u links local↔remote
git push                            # after that, just this
```

### merging
```
git switch main             # go to destination
git merge writing-rules     # pull writing-rules into main
git push
```

merge opened Vim asking for a message. Vim = a text editor inside the terminal. no mouse, only keys.
exit Vim: `Esc`, then type `:wq`, Enter. (`:wq` = save and quit)

my merge said it used the 'ort' strategy. from what I get so far:
- if nothing new is on `main`, git just glues the new commits on the end → no message needed
- if both branches have new stuff, git makes one extra commit to join them → that's what needed a message
- 'ort' is just the name of the recipe git uses to combine them. don't really get the details yet, still looking into it.

### deleting a branch (local only)
```
git branch -d writing-rules
```
removes the local branch label after merging. remote branch on GitHub stays.

### .gitignore
plain text file at repo root. list of files/folders git should ignore.
example from other projects:
```
venv/
```
keeps virtual env folders out of commits.

---

## Flags I know

| flag | meaning |
|---|---|
| `-c` | create (git switch) |
| `-m` | message inline (git commit) |
| `-u` | set upstream (git push) |
| `--oneline` | one-line commits (git log) |
| `--graph` | ASCII tree (git log) |
| `--all` | every branch (git log) |
| `--decorate` | show branch labels (git log) |
| `--soft` | keep changes (git reset) |
| `--hard` | discard changes (git reset) |

look up flags: `git <command> -h`

---

## Things that confused me

- "nothing to commit" → forgot `git add` first
- `git tree` doesn't work by default — would need to set up an alias
- switching branches made `Writing_Rules/` disappear from VS Code → that's normal, it lives in another snapshot
- merge opened Vim → just `:wq`

---

## What I haven't tried yet

- merge conflicts
- `git rebase`
- `git stash`
- pull requests via GitHub UI (only done local merge + push so far)
