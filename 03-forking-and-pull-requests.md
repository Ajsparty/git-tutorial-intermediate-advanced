# Lesson 3: Forking and Pull Requests

Forking creates a personal copy of someone else's repository. Combined with pull requests, it is the standard way to contribute to open-source projects and many team workflows.

## What is a Fork?

A fork is a full copy of a repository under your GitHub account. You can freely experiment, commit, and push without affecting the original project.

## Forking a Repository

1. Navigate to the original repository on GitHub.
2. Click the **Fork** button in the top-right corner.
3. Choose your account as the destination.

GitHub creates a new repository under your username.

## Cloning Your Fork

```bash
git clone https://github.com/YOUR-USERNAME/original-repo-name.git
cd original-repo-name
```

## Adding the Upstream Remote

To stay synchronized with the original repository, add it as a remote named `upstream`:

```bash
git remote add upstream https://github.com/ORIGINAL-OWNER/original-repo-name.git
```

Verify your remotes:

```bash
git remote -v
```

You should see both `origin` (your fork) and `upstream` (the original).

## Keeping Your Fork Updated

```bash
git switch main
git fetch upstream
git merge upstream/main
# or: git rebase upstream/main
git push origin main
```

## Creating a Feature Branch and Opening a Pull Request

1. Create and switch to a new branch:

```bash
git switch -c fix/typo-in-readme
```

2. Make your changes and commit them.

3. Push the branch to your fork:

```bash
git push -u origin fix/typo-in-readme
```

4. On GitHub, navigate to your fork. You will see a banner offering to create a pull request. Click it.

5. Fill in the title and description. Explain what you changed and why. Reference any related issues.

6. Submit the pull request against the original repository's main branch.

## Responding to Review Feedback

If reviewers request changes:

```bash
# Make additional commits on the same branch
git add .
git commit -m "Address review feedback"
git push
```

The pull request updates automatically.

## Common Pitfalls

- Forgetting to add the upstream remote makes it harder to stay current.
- Opening a pull request from your `main` branch instead of a feature branch can complicate future updates.
- Not explaining your changes clearly in the pull request description slows down review.

## Practice Exercise

1. Fork a public repository you like (or this one).
2. Clone your fork and add the upstream remote.
3. Create a small documentation improvement on a new branch.
4. Push the branch and open a pull request (you can close it immediately if it is only for practice).

Next: [Cherry-picking, Stashing, and Interactive Rebase](./04-advanced-history.md)
