# Git and GitHub Repository

Welcome to the "Git and GitHub" repository! This repository serves as a handy reference for various Git and GitHub commands and instructions. Whether you're new to version control or looking to refresh your knowledge, you'll find useful tips and guidelines here.

## Table of Contents

- [Cloning a Git Repository](#cloning-a-git-repository)
- [Git Branch](#git-branch)
- [Delete Git Branch](#delete-git-branch)
- [Committing Your Changes](#committing-your-changes)
- [Pick/Squash/Drop Git Commits](#picksquashdrop-git-commits)
- [Updating Your Fork Branch](#updating-your-fork-branch)

## Cloning a Git Repository

To start, you'll need a Git repository to clone. You can either create one on a Git hosting platform like GitHub, GitLab, or Bitbucket, or you can clone an existing open-source project. For this example, let's assume you want to clone an existing repository from GitHub.

1. Open your terminal.

Navigate to the directory where you want to store the cloned project.
Use the following command to clone a repository:
```
git clone <repository_url>
```

Replace <repository_url> with the URL of the Git repository you want to clone. For example:

```
git clone https://github.com/exampleuser/example-repo.git
```

Git will create a new directory with the repository's name and copy the project files into it.

## Git Branch

### Looking at Branches:

To see a list of branches in the repository, use the following command:
```
git branch -a
```

This command will list all local and remote branches. The currently checked out branch will be highlighted.

### Creating a Branch:

To create a new branch, use the following command:
```
git checkout -b new-branch-name
```

Replace new-branch-name with the name you want for your new branch.

### Checking Out a Branch:

To switch to an existing branch, use the following command:
```
git checkout branch-name
```

Replace branch-name with the name of the branch you want to switch to.

### Checking Git Logs:

- To see a list of branches in the repository, you can use the following command:
```
git log
```

This command will list all local and remote branches. The currently checked out branch will be highlighted.

- To view a simplified commit history with one-line summaries, use the --oneline flag with git log:
```
git log --oneline
```

This command will display a condensed list of commits, showing only the first line of each commit message and the commit's SHA-1 hash.

- To view logs of specific branch.
```
git log --oneline branch_name
```


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

## Committing Your Changes

### Viewing your changes
Git keeps track of changes in the working directory. Git can be told to ignore binary files (like .o or .ko files), so it won't track changes to those files. You can see which files have been modified by running:
```
git status
```

git can also show you a diff stat of what changed:
```
git diff
```

### Commit your changes
Assuming we want to include all of our changes in one git commit, you can use git to add the changed file to the list of changes to be committed (the "staging area"):
```
git add <file>
```

If you run `git diff` again, you'll notice it doesn't list any changed files. That's because, by default, git diff only shows you the unstaged changes. If you run this command instead, you'll see the staged changes:
```
git diff --cached
```
That command will show you the changes to be committed.

### Reverting your staged changes
If you don't want to commit those changes, you can remove those changes from the staging area by running:
```
git reset <file>
```

### Committing changes
Finally, you can commit your staged changes:
```
git commit -s -v
```

The -s flag will add the Signed-off-by line that is needed at the end of your patch description. The -v flag will show you the diff that you're committing.

### Committing parts of files
You can also add parts of files to the staging area by using the following flag:
```
git add -p
```

That will allow you to add hunks of the file to the staging area, or even edit hunks that you want to commit. This is useful, for instance, if you've made whitespace changes, and also made a camel-case variable name fix, but those changes are on the same line. You can edit the line to revert the camel-case name change, and just add the whitespace change to the staging area. Then when you commit, you will just be committing the whitespace change.

### Viewing your commit
Make sure your commit looks fine by running these commands:
```
git show HEAD
```

This will show the latest commit. If you want git to show a different commit, you can pass the commit ID (the long number that's shown in `git log`, or the short number that's shown in `git log --oneline`). Read the "Specifying Revisions section" of the `git rev-parse` manual page for more details on what you can in place of a commit ID.

### Editing Your Git Commits

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

## Pick/Squash/Drop Git Commits

To pick, squash, or drop Git commits, you can use Git rebase. Run the following command to interactively rebase your commits:
```
git rebase -i master
```
Insert the words 'Pick,' 'Squash,' or 'Drop' in front of the commits you want to perform the respective operation on in the interactive rebase window. Note that when squashing a commit, you should ensure that you have one 'Pick' commit before the 'Squash' commit.

When you run git rebase -i master, it opens an interactive rebase window where you can choose what to do with each commit. Here's a bit more detail on each of these actions:

- Pick: This is the default action for each commit. It means you want to keep the commit as is.

- Squash: This action allows you to combine a commit with the one before it (the one above it in the list). It merges the changes from the selected commit into the previous one, and you'll be prompted to edit the commit message.

- Drop: This action removes the selected commit from the branch's history. The commit and its changes will be discarded.

Here's how the interactive rebase window might look:
```
pick c1a1f11 Commit message 1
pick b2b2b22 Commit message 2
pick d3d3d33 Commit message 3
```

To squash commit b2b2b22 into commit c1a1f11, you can change it to:

```
pick c1a1f11 Commit message 1
squash b2b2b22 Commit message 2
pick d3d3d33 Commit message 3
```

After saving and exiting the rebase window, you'll have the opportunity to edit the commit message for the squashed commit.

Interactive rebasing is a powerful feature in Git that allows you to clean up your commit history and make it more organized before merging it into a branch or repository. It's important to use it with care, especially when working on shared branches, as it can rewrite commit history and potentially cause conflicts for collaborators.

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

