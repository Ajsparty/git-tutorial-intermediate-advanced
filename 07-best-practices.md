# Lesson 7: Best Practices and Workflows

Clear conventions and consistent habits make Git a reliable tool for individuals and teams.

## Commit Message Guidelines

Write messages that explain *why* the change was made, not just *what* changed.

Good format:

```
Add user authentication endpoint

Implement JWT-based login so mobile clients can authenticate
without storing passwords. Closes #142.
```

- Use the imperative mood ("Add feature" not "Added feature").
- Keep the first line under 50–72 characters.
- Separate the subject from the body with a blank line.

## Branch Naming Conventions

Adopt a consistent pattern so the purpose of a branch is obvious:

- `feature/user-profile`
- `fix/login-timeout`
- `docs/update-api-guide`
- `refactor/extract-auth-service`
- `chore/update-dependencies`

## Recommended Workflows

### GitHub Flow (Simple)

1. Create a feature branch from `main`.
2. Commit changes.
3. Open a pull request.
4. Review and merge into `main`.
5. Delete the feature branch.

### Git Flow (Structured)

- `main` — production-ready code
- `develop` — integration branch
- Feature branches from `develop`
- Release and hotfix branches as needed

Choose the simplest workflow that meets your team's needs.

## Protecting the Main Branch

On GitHub, configure branch protection rules:

- Require pull request reviews before merging
- Require status checks to pass
- Prevent force pushes
- Require linear history (optional)

## Useful Aliases

Add these to your `~/.gitconfig` for faster daily work:

```
[alias]
    st = status
    co = checkout
    br = branch
    cm = commit
    lg = log --oneline --graph --decorate --all
    last = log -1 HEAD
```

## Recovering from Mistakes

- Soft reset (keep changes staged): `git reset --soft HEAD~1`
- Mixed reset (default, unstage changes): `git reset HEAD~1`
- Hard reset (discard changes): `git reset --hard HEAD~1` (use carefully)
- Revert a public commit safely: `git revert <commit-hash>`

## Final Checklist Before Pushing

- [ ] Commits are focused and well-described
- [ ] Branch is up to date with the target branch
- [ ] Tests pass locally
- [ ] No secrets or large binary files are committed
- [ ] Pull request description explains the change and its motivation

## Further Learning

- Official Git documentation: https://git-scm.com/doc
- Pro Git book (free): https://git-scm.com/book/en/v2
- Practice repositories and open-source contributions

Congratulations! You now have a solid foundation in intermediate and advanced Git. Regular practice will make these tools second nature.

---

Return to the [main README](./README.md)
