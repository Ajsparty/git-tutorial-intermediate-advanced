# Lesson 6: Tags, Bisect, and Advanced Tools

These commands help with versioning, debugging, and managing complex repositories.

## Tags

Tags mark specific points in history, commonly used for releases.

### Lightweight Tag

```bash
git tag v1.0.0
```

### Annotated Tag (Recommended)

Annotated tags store extra metadata and are preferred for releases:

```bash
git tag -a v1.0.0 -m "Release version 1.0.0"
```

Push tags to the remote:

```bash
git push origin v1.0.0
# or push all tags:
git push origin --tags
```

List tags:

```bash
git tag -l
```

## Git Bisect

Bisect performs a binary search through history to find the commit that introduced a bug.

```bash
git bisect start
git bisect bad          # Current commit is broken
git bisect good abc1234 # Known good commit
```

Git checks out a midpoint commit. Test it, then mark it:

```bash
git bisect good   # or git bisect bad
```

Repeat until Git identifies the first bad commit. Then exit:

```bash
git bisect reset
```

## Worktrees

Worktrees let you check out multiple branches simultaneously in different directories.

```bash
git worktree add ../project-hotfix hotfix/critical-bug
```

This creates a new directory with the specified branch checked out, while your main working directory stays on its current branch.

List worktrees:

```bash
git worktree list
```

Remove a worktree:

```bash
git worktree remove ../project-hotfix
```

## Reflog

The reflog records every movement of HEAD, even commits that are no longer reachable by any branch.

```bash
git reflog
```

This is invaluable for recovering "lost" commits after a bad reset or rebase:

```bash
git checkout abc1234   # Restore a commit from the reflog
```

## Common Pitfalls

- Lightweight tags are easy to move accidentally; prefer annotated tags for releases.
- Bisect requires a reliable way to test each commit (script or manual steps).
- Worktrees share the same repository object database, so disk usage is efficient, but you must remember to clean them up.

## Practice Exercise

1. Create an annotated tag for a recent commit and push it.
2. Intentionally introduce a bug, then use bisect to find the commit that caused it.
3. Use a worktree to examine another branch without switching your current working directory.

Next: [Best Practices and Workflows](./07-best-practices.md)
