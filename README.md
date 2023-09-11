# Git and GitHub Repository

Welcome to the "Git and GitHub" repository! This repository serves as a handy reference for various Git and GitHub commands and instructions. Whether you're new to version control or looking to refresh your knowledge, you'll find useful tips and guidelines here.

## Table of Contents

- [Delete Git Branch](#delete-git-branch)
- [Pick/Squash/Drop Git Commits](#picksquashdrop-git-commits)
- [Editing Your Git Commits](#editing-your-git-commits)
- [Updating Your Fork Branch](#updating-your-fork-branch)

## Delete Git Branch

### Delete Branch Locally
To delete a Git branch locally, use the following command:
git branch -d localBranchName

### Delete Branch Remotely
To delete a Git branch remotely, use the following command:
git push origin --delete remoteBranchName


## Pick/Squash/Drop Git Commits

To pick, squash, or drop Git commits, you can use Git rebase. Run the following command to interactively rebase your commits:
git rebase -i master


## Editing Your Git Commits

If you need to make changes to a patch you've submitted for review, you can use the following command to amend your commit:
git commit --amend -v

You can also reset the previous commit in the Git history or revert all files to their state before your commit, depending on your needs.

## Updating Your Fork Branch

To keep your forked branch up-to-date with changes from the original repository, follow these steps:

1. Add the Upstream Repository as a Remote:
git remote add upstream <original_repository_url>

Replace `<original_repository_url>` with the URL of the original repository.

2. Fetch the Latest Changes from Upstream:
git fetch upstream


3. Checkout Your Forked Branch:
git checkout your_forked_branch


4. Merge or Rebase the Changes:
- Merging:
  ```
  git merge upstream/main  # or upstream/master
  ```
- Rebasing:
  ```
  git rebase upstream/main  # or upstream/master
  ```
Resolve conflicts if necessary.

5. Push the Updates:
git push origin your_forked_branch


6. Create a Pull Request (Optional):
If you intend to contribute back to the original repository, create a pull request via the GitHub interface.

Keep your codebase up-to-date and aligned with the latest project developments by updating your forked branch from the original repository's changes.

Feel free to explore the content and use these instructions as a reference for your Git and GitHub tasks. Happy coding!

