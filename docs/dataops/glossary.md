---
title: Git Glossary
sidebar_position: 5
---

All the git-speak can be confusing and intimidating at first. Here is a hopefully helpful cheat sheet of some of most of the important terms.

For a more in-depth explanation of git concepts, *Atlassian*'s [git guides](https://www.atlassian.com/git/tutorials/what-is-version-control) are excellent resources. They have a [cheat sheet](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet) as well that's a little more concise and pragmatic than the one I've put together here.

### Git

Git is a **version control system** that tracks and organizes changes in a codebase mainly via its system of commits and branches.

### GitHub

An online service that hosts git repositories.

### Branches

The command `git branch <branch-name>` creates a new branch in your repository. A branch can be thought of as an alternate pathway of changes to your codebase, splitting off from the commit where you created the branch. When a branch is "checked out", all commits get added to the end of that branch. When you switch branches, your IDE or whatever program is reading code from the repo will completely switch the active files to the files in the branch you switched to. The state of the (committed) files in the branch you switched from will be saved, and you can pull them back up again by switching back to the branch.

The modern way to switch branches is by using the `git switch` command, but you'll see `git checkout` used most places.

### Commits

A commit is a snapshot of the state of your codebase at a given point in time. Commits are made by running the command `git commit -m "commit message"`. The commit message is a short description of the changes you made in the commit so that others can review the changes you made in your code. Commits are organized via a directed acyclic graph (DAG) that conveys the *commit history*. The commit history is a record of all the changes made to the codebase, and is the primary way to track changes in a codebase.

### HEAD

HEAD is fancy name for a "pointer" that labels the latest commit on the branch that you currently have checked out. You'll use this when you want to refer to that commit specifically, like if you want to revert your code to the checkpoint two commits ago, you can use `git reset HEAD~2` to reset your code to the commit that HEAD pointed to two commits ago.

### `git reset`

There are three types of resets: `--soft`, `--hard`, and `--mixed` (the default). Generally, a reset moves your HEAD pointer to a different commit, modifying the commit history to an earlier commit. The various types of resets apply these changes to the staging area and working tree as well. If you find yourself needing to perform a reset and needing to understand the difference between the options, check out this intro from [Atlassian](https://www.atlassian.com/git/tutorials/undoing-changes/git-reset).

### `git add` and the staging tree

The command `git add <file-name>` adds a file to the staging area. The staging area is a temporary holding place for files that you want to commit. People new and experienced with Git alike might struggle to see the value in the `add` process and the staging area, because it's often convienent to "forget" to add a file to the staging area until we are ready to commit all of our changes. Remember that commits are for sharing with others, and we want them to contain changes that logically go together. The staging tree provides an intermediate area where files that are "ready to commit" can be stored. Some common examples when this is useful:

- We're working on a large commit and finish working on some files before others. Staging our "ready-to-go" files lets us better focus on the unstaged changes still in progress in our working tree, especially when using `git diff` and other operations where we are reviewing our changes.
- We have changes from multiple unrelated tasks in our working tree. We can stage the changes for each task separately, and commit them separately. This makes it easier to break the commits up into logical chunks without needing to resort to some more complicated options like stashing or branching.

### Repositories, remotes, cloning, and origin

A repository is a collection of files and their commit history. Repositories are stored on a remote server, and can be cloned to your local machine. The command `git clone <repo-url>` clones a repository to your local machine. Cloning a repository creates a local copy of the repository on your machine, and sets up a remote called `origin` that points to the remote repository. The remote repository is usually hosted on a service like GitHub, GitLab, or BitBucket.

### Stashing

`git stash` is a very useful command to store changes in a temporary holding area. This is useful when you want to switch branches, but don't want to commit your changes yet. You can stash your changes, switch branches, and then pull your changes back up again when you're ready. This is also useful when you want to pull changes from a remote repository, but don't want to commit your changes yet. You can stash your changes, pull the changes from the remote, and then pull your changes back up again when you're ready. Very helpful for avoiding unnecessary merge conflicts.

### Merging

`git merge <branch-name>` incorporates the changes from `<branch-name>` the currently checked out branch. It's often used to combine changes from different people, or it might be used to combine changes from same person who working on different features on different branches.

### Fetch vs pull

`git fetch` downloads changes from a remote repository, but does not merge them into your active branch right away. It stores the updates from the remote locally in special remote branches that you can see with `git branch -r`. `git pull` is simply a shortcut for a `git fetch` followed by a `git merge` -- see [Pulling Updates](dev_env/pulling_updates).
