# Git Rebase Practice Kit

A small repository for practicing how to combine independent feature branches into a clean, linear history with `git rebase` and fast-forward merges.

## Repository layout

- `master` provides the shared starting point.
- `add-echo` contains an echo-route change.
- `add-reverse` contains a reverse-route change.

## Practice workflow

Clone the repository and fetch all branches:

```bash
git clone https://github.com/alirazawatoo/git-rebase-practice-kit.git
cd git-rebase-practice-kit
git fetch --all
```

Rebase each feature branch onto the latest `master`, then fast-forward `master` after each branch:

```bash
git switch add-echo
git rebase master
git switch master
git merge --ff-only add-echo

git switch add-reverse
git rebase master
git switch master
git merge --ff-only add-reverse
```

If Git reports a conflict, resolve the affected files, stage them, and continue with `git rebase --continue`.

## Verify the result

```bash
git log --graph --decorate --oneline --all
```

The final `master` history should contain both route changes without a merge commit.

## Learning goals

- Understand how rebasing changes commit ancestry
- Resolve rebase conflicts safely
- Use fast-forward merges to retain a linear history
- Inspect branch relationships with `git log --graph`
