# Lesson 5: Resolving Merge Conflicts

Conflicts occur when Git cannot automatically combine changes from two different commits. Learning to resolve them calmly and correctly is essential.

## When Conflicts Happen

Conflicts most often appear during:

- `git merge`
- `git rebase`
- `git cherry-pick`
- `git pull` (which is fetch + merge or rebase)

## Identifying Conflicts

After a conflict, Git marks the affected files:

```bash
git status
```

Conflicted files show as "both modified".

## Conflict Markers

Open a conflicted file. You will see markers like this:

```
<<<<<<< HEAD
This is the version on your current branch.
=======
This is the incoming version.
>>>>>>> feature/other-branch
```

- Everything between `<<<<<<<` and `=======` is your current branch.
- Everything between `=======` and `>>>>>>>` is the incoming change.

## Resolving a Conflict

1. Edit the file to produce the correct final content. Remove the conflict markers entirely.
2. Stage the resolved file:

```bash
git add path/to/file.md
```

3. Continue the operation:

```bash
# For merge:
git commit

# For rebase:
git rebase --continue

# For cherry-pick:
git cherry-pick --continue
```

## Using a Merge Tool

Configure a visual merge tool (VS Code, Vimdiff, Beyond Compare, etc.):

```bash
git mergetool
```

This opens a three-way view (base, yours, theirs) that many people find clearer.

## Aborting a Conflicted Operation

If you want to start over:

```bash
git merge --abort
# or
git rebase --abort
# or
git cherry-pick --abort
```

## Prevention Tips

- Pull or rebase frequently so conflicts stay small.
- Communicate with teammates about files you are both editing.
- Keep commits focused on single concerns.
- Use clear, descriptive commit messages.

## Practice Exercise

1. Create two branches that both edit the same line in a file.
2. Merge one into the other and deliberately create a conflict.
3. Resolve the conflict, commit, and verify the result with `git log --oneline --graph`.

Next: [Tags, Bisect, and Advanced Tools](./06-advanced-tools.md)
