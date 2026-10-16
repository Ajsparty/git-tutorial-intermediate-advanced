# Lesson 1: Branching and Merging

Branches let you work on features, bug fixes, or experiments without affecting the main codebase. This lesson covers creating, switching, merging, and deleting branches effectively.

## Why Branches Matter

- Isolate changes so the main branch stays stable
- Enable parallel development by multiple people
- Make code reviews and rollbacks easier

## Creating and Switching Branches

Create a new branch and switch to it in one command:

```bash
git checkout -b feature/user-authentication
```

Or with the modern syntax:

```bash
git switch -c feature/user-authentication
```

List all branches (local and remote):

```bash
git branch -a
```

Switch to an existing branch:

```bash
git switch main
```

## Making Changes on a Branch

Work as usual:

```bash
# Edit files
git add .
git commit -m "Add login form validation"
```

Push the branch to the remote for the first time:

```bash
git push -u origin feature/user-authentication
```

The `-u` flag sets the upstream tracking branch so future `git push` and `git pull` work without extra arguments.

## Merging Branches

When your feature is ready, merge it into the target branch (usually `main` or `develop`).

### Fast-forward Merge

If no new commits exist on the target branch, Git can simply move the pointer forward:

```bash
git switch main
git merge feature/user-authentication
```

### Merge Commit

When histories have diverged, Git creates a merge commit:

```bash
git switch main
git merge feature/user-authentication
```

This preserves the full history of both branches.

### Squash Merge

Combine all commits from the feature branch into a single commit on the target branch. Useful for keeping the main history clean:

```bash
git switch main
git merge --squash feature/user-authentication
git commit -m "Add user authentication feature"
```

## Deleting Branches

After merging, delete the local branch:

```bash
git branch -d feature/user-authentication
```

Delete the remote branch:

```bash
git push origin --delete feature/user-authentication
```

## Common Pitfalls

- **Working on the wrong branch**: Always check your current branch with `git status` or `git branch` before committing.
- **Forgetting to push**: A local branch is invisible to teammates until you push it.
- **Long-lived feature branches**: Regularly merge or rebase from the main branch to reduce conflict size.

## Practice Exercise

1. Create a new branch called `docs/update-readme`.
2. Make a small change to a file and commit it.
3. Switch back to `main` and merge the branch.
4. Delete the feature branch.

Next: [Rebasing](./02-rebasing.md)
