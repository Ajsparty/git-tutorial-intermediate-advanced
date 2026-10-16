# Lesson 2: Rebasing

Rebasing rewrites commit history by moving a branch to a new base. It produces a linear history, which many teams prefer over merge commits.

## Rebase vs Merge

| Aspect          | Merge                          | Rebase                              |
|-----------------|--------------------------------|-------------------------------------|
| History         | Preserves exact timeline       | Creates a linear, cleaner history   |
| Commits         | Adds a merge commit            | Rewrites existing commits           |
| Safety          | Safe for shared branches       | Dangerous on shared branches        |
| Use case        | Integrating finished features  | Updating a feature branch           |

**Rule of thumb**: Never rebase commits that have been pushed and shared with others.

## Basic Rebase

Update your feature branch with the latest changes from `main`:

```bash
git switch feature/user-authentication
git rebase main
```

This takes your feature commits and replays them on top of the current `main`.

## Interactive Rebase

Interactive rebase lets you edit, reorder, squash, or drop commits before sharing them.

Start an interactive rebase of the last 3 commits:

```bash
git rebase -i HEAD~3
```

Git opens an editor with a list of commits. Common commands:

- `pick` — keep the commit as-is
- `reword` — change the commit message
- `squash` — combine with the previous commit
- `fixup` — combine and discard the message
- `drop` — remove the commit entirely
- `edit` — pause to amend the commit

Example: Squash the last two commits into one:

```
pick abc1234 Add login form
squash def5678 Add validation
pick ghi9012 Fix typo
```

Save and close the editor. Git will prompt you to write a combined commit message.

## Aborting or Continuing a Rebase

If conflicts occur during rebase:

```bash
# Resolve conflicts in the files, then:
git add .
git rebase --continue
```

To cancel the entire rebase:

```bash
git rebase --abort
```

## Force Pushing After Rebase

Because rebase rewrites history, you must force-push the updated branch:

```bash
git push --force-with-lease origin feature/user-authentication
```

`--force-with-lease` is safer than `--force` because it checks that no one else has pushed new commits to the branch.

## Common Pitfalls

- Rebasing a shared branch can cause teammates to lose work or experience confusing conflicts.
- Always communicate with your team before force-pushing.
- Prefer merge for integrating into the main branch; use rebase to keep your feature branch up to date.

## Practice Exercise

1. Create a feature branch and make two commits.
2. Make a change on `main` and commit it.
3. Rebase your feature branch onto `main`.
4. Use interactive rebase to squash your two commits into one.

Next: [Forking and Pull Requests](./03-forking-and-pull-requests.md)
