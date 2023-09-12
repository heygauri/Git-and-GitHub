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
```
git branch -d localBranchName
```

### Delete Branch Remotely
To delete a Git branch remotely, use the following command:
```
git push origin --delete remoteBranchName
```

## Pick/Squash/Drop Git Commits

To pick, squash, or drop Git commits, you can use Git rebase. Run the following command to interactively rebase your commits:
```
git rebase -i master
```

## Editing Your Git Commits

Say you need to make a change to a commit you've submitted for review by creating a pull request or submitted a patch. There are several ways to do this.

If the commit/patch is your HEAD commit, you can run:
```
git commit --amend -v
```

That will allow you to edit the commit message. If you add changes to the staging area with `git add`, you can add those changes to your commit with the above command, along with your previously committed changes.

If you want to take the previous commit out of the git history, but leave the changes in your working tree, you can run:
```
git reset --mixed HEAD^
```

If you want to completely get rid of all your changes, and revert all files to their state before your commit, you can use the --hard flag instead of the --mixed flag. Use this flag with care!

## Updating Your Fork Branch

To keep your forked branch up-to-date with changes from the original repository, follow these steps:

1. Checkout Your Master/Main Branch and Pull the Latest Changes:
```
git checkout master/main_branch
git pull origin master/main_branch
```

2. Add the Upstream Repository as a Remote:
```
git remote add upstream <original_repository_url>
```
Replace <original_repository_url> with the URL of the original repository.

3. Fetch the Latest Changes from Upstream:
```
git fetch upstream
```

4. Checkout Your Forked Branch from where you want to push your changes:
```
git checkout your_forked_branch
```

5. Merge or Rebase the Changes from Upstream:

- Merging:
```
git merge upstream/main  # or upstream/master
```

- Rebasing:
```
git rebase upstream/main  # or upstream/master
```

Resolve conflicts if necessary.

6. Push Updates to Your Forked Branch:
   
```
git push origin your_forked_branch
```

This command pushes your local changes to the remote repository (your fork) on the branch specified (your_forked_branch). This is typically used when you want to update your fork on GitHub or another Git hosting platform.

### Push with -u to Update an Existing Pull Request:

```
git push -u origin your_forked_branch
```

Adding the -u flag sets the upstream branch for the current local branch. If you've already created a pull request and want to push additional commits to that same branch for the pull request, using -u allows you to do so without specifying the remote and branch each time.

### Force Push to Overwrite Remote Branch:

```
git push --force origin your_forked_branch
```

The --force flag is used when you need to overwrite the remote branch with your local branch. Be cautious when using this option, as it can rewrite history and potentially disrupt collaboration with others. Force pushing is typically discouraged unless you have a specific reason to do so, such as resolving conflicts or cleaning up your branch.

7. Create a Pull Request (Optional):
If you intend to contribute back to the original repository, create a pull request via the GitHub interface.

Keep your codebase up-to-date and aligned with the latest project developments by updating your forked branch from the original repository's changes.

Feel free to explore the content and use these instructions as a reference for your Git and GitHub tasks. Happy coding!

