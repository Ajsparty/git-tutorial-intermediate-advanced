# Lesson 4: Cherry-picking, Stashing, and Interactive Rebase

These tools give you precise control over individual commits and temporary work.

## Cherry-picking

Cherry-picking applies a specific commit from one branch onto another without merging the entire branch.

```bash
# Find the commit hash
git log --oneline

# Apply that commit to the current branch
git cherry-pick abc1234
```

Useful when you need a single bug fix from a feature branch without bringing in unfinished work.

If conflicts occur, resolve them, then:

```bash
git add .
git cherry-pick --continue
```

## Stashing

Stashing temporarily saves uncommitted changes so you can switch branches or pull updates cleanly.

Save your current work:

```bash
git stash push -m "Work in progress on login form"
```

Or simply:

```bash
git stash
```

List stashes:

```bash
git stash list
```

Apply the most recent stash and keep it in the list:

```bash
git stash apply
```

Apply and remove the stash:

```bash
git stash pop
```

Apply a specific stash:

```bash
git stash apply stash@{2}
```

## Interactive Rebase (Advanced Usage)

Beyond basic squashing, interactive rebase can:

- Reorder commits
- Split a commit into multiple commits
- Edit a commit deep in history

To split a commit:

1. Run `git rebase -i HEAD~5`
2. Mark the commit as `edit`
3. When Git pauses, run `git reset HEAD~1`
4. Stage and commit the changes in smaller pieces
5. Continue with `git rebase --continue`

## Common Pitfalls

- Cherry-picking creates a new commit with a different hash, even if the content is identical.
- Stashing untracked files requires `git stash -u`.
- Overusing interactive rebase on shared branches leads to coordination problems.

## Practice Exercise

1. Make two commits on a feature branch.
2. Switch to `main` and cherry-pick only the second commit.
3. Start work on another change, then stash it before switching branches.
4. Pop the stash later and continue.

Next: [Resolving Merge Conflicts](./05-conflict-resolution.md)
