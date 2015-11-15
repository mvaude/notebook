+++
categories = ["Development", "golang"]
date = "2015-11-15T23:29:50+01:00"
description = ""
draft = true
image = "/img/about-bg.jpg"
tags = ["go", "golang", "templates", "themes", "development"]
title = "Github Training"

+++

# Github Training

## Introducing Git and Github

### What is Github ?

GitHub is a website that allows your team to collaborate more effectively. It is built on top of Git—a distributed version control system. GitHub and Git help teams to collaborate more effectively on projects.

With Git, each person has a local copy of the project to work on. As they make changes locally, they can upload them to GitHub and download any changes that others have made.

GitHub provides access to a central copy of the code, as well as features like Pull Requests and Issues that make collaborating easier.

### Key GitHub Features

In addition to being a place to host and share your Git projects, GitHub provides features, like Pull Requests and Issues, that make collaborating easier. Issues are general places for discussions about the project, from high-level planning to bug tracking. Pull Requests let you discuss and review specific changes to the project files themselves.

### The GitHub Ecosystem

You can also use all of your favorite tools with GitHub. You don't need to use a new text editor or bug tracker: your team gets to keep the tools they're comfortable with.

GitHub can also integrate into your current deployment process, and fully supports continuous integration and continuous deployment to help you and your team build software better, together.

For more information on integrating GitHub with the tools you already use, refer to GitHub's Integrations page.

## Getting Started with Collaboration

### Github Repositories

A repository is the most basic element of GitHub. It is easiest to imagine as a project's folder. However, unlike an ordinary folder on your laptop, a GitHub repository offers simple yet powerful tools for collaborating with others. A repository contains all of the project files, and stores the history of each file. Whether you are just curious or you are a major contributor, knowing your way around a repository is essential!

#### Summary

* The repository (or "repo") holds everything in your project—code, documentation, other important files.
* Everything in the Code View of the repo is tracked by git version control.
* The '''README.md''' file is shown at the bottom of the main page of the code view.
* Issues are used to track bugs and feature requests, and can be assigned to team members.
* A pull request represents a change that the author would like to make to the repo. PRs are used to resolve issues.

### Using Issues

Use GitHub issues to record and discuss ideas, enhancements, tasks, and bugs. They make collaboration easier in a variety of ways, such as:

* Replacing email for project discussions, ensuring everyone on the team has the complete story.
* Allowing you to cross-link to other issues and pull requests.
* Creating a single, comprehensive record of how and why you made certain decisions.
* Allowing you to easily pull the right people into a conversation.

#### Summary

* You can use Markdown to format issues.
* You can @mention somebody in order to alert them of the issue.
* The "Preview" tab shows how your comment will be rendered.
* Add screenshots or pictures to the issue by simply dragging and dropping them into the comment field.
* You can assign an issue to anyone with access to the repo.
* Labels can be used to organize issues.
* You can filter issues by label, author or assignee.

## The GitHub WorkFlow: Branching and Comitting

### Diving into Github

In this section we'll explore GitHub's functionality in depth.

You'll have the chance to practice all the skills that we teach in your GitHub repository, so make sure not to move on until you're sure you can perform these actions: you'll need them in your day-to-day job.
 
#### Summary


* Everything on GitHub lives on a branch.
* The "canonical" version of the code lives on the master branch by convention.
* Use new branches to experiment with the code without affecting master.
* When you're done experimenting and want to add the feature into master, you create a pull request (PR).
* PRs don't have to be perfect, but should be ready for other people to look at, comment on, and work on.
* Once the changes to the PR are completed, the branch is "merged" into master and can then be removed.

### Create a branch



* Create a branch by clicking on the branch drop-down and entering your branch name in the text field.
* Any files you create, edit, or delete will then be applied to that branch.
* Be careful; GitHub automatically puts you on master when you leave the repo and come back, so always make sure you're on the right branch before you start working.

### Creates Files on Github

* You can create a new file directly in the web interface.
* Once you're done editing the file, "commit" the changes.
* Make sure to include a commit message, and that you've chosen to commit to the branch you've already created.

## The Github Workflow: Pull Requests

### Pull Requests

In this section we'll go over how to use Pull Requests. Pull Requests, or "PRs", are one of the most important parts of the GitHub Flow.

A PR is a request to merge one branch into another. They're used to discuss the changes made in the branch, and to continue to make changes until the branch is complete and the team agrees it can be merged. You'll use PRs frequently when working with your team, as they're the primary way to bring code on the master branch up to date with your feature branch once it's ready for production.

#### Summary

* Pull Requests (or PRs) are used to add code to another branch, in this case master.
* A Pull Request asks that the team merge one branch into another.
* The "base" is the branch you want to merge into (often master), the "compare" is the branch you're merging, in this case the feature branch.
* Make sure to leave a comment to tell people what changes you made and why.
* In the comment, you should put number sign (#) in front of the number of the issue that you're fixing. This will automatically link your PR to that issue.
* Once you've made the PR, the Files changed view allows you to see what this PR will change on the base branch. Red means "deleted", green means "added". This view is often called the "diff".
* You can add comments directly to the diff, or in the Conversations view.

### Editing Pull Request Files

* You will be notified of all comments on your own PRs, unless you've unsubscribed from that PR or ignored the whole repository.
* You can make changes to files directly in the Files changed view.
* These changes, once committed, will be included in the PR.

### Merging Pull Requests

At this point, your pull request should be approved and you are ready to merge it in to the master branch. When you merge your branch, you are taking the content and history from your feature branch and adding it to the content and history of the master branch.

Many project teams have established rules about who should merge a pull request. Some say it should be the person who created the pull request since they will be the ones to deal with any issues resulting from the merge. Others say it should be a single person within the project team to ensure consistency. Still others say it can be anyone other than the person who created the pull request. There are also third party Continuous Integration (CI) tools you can integrate with GitHub to test the build before the merge is completed.

There are pros and cons to each approach and we will not attempt to prescribe a solution here, but these are good conversations to have within your project team.

Let's take a look at how you can merge the pull request and close the original issue at the same time.

#### Merging Pull Requests

* To merge your branch into the master branch, click the Merge pull request button in the Conversation view.
* Use the keyword Fixes followed by # and the issue number to close the issue at the same time as you merge the PR.
* A full list of keywords can be found here.
* Once the PR is successfully merged, you can delete your feature branch as it is no longer needed.

## Setting Up Git

### Using the Command Line

So far, all the work we've done has been using GitHub's web interface. However, if you prefer to work on the command line, you can easily integrate GitHub into your current workflow.

In this section, we'll teach you how to use Git and GitHub effectively through the command line. We assume a working knowledge of the command line interface, so if you're rusty you might want to brush up on using the CLI before forging ahead.

To get to the command line, you should do the following:

* Mac: Type command-space to bring up Spotlight search, then search for Terminal.
* Linux: Open up your prefered shell, such as bash or fish.
* Windows: We recommend that you download Git for Windows from GitHub, as it includes a bash emulator. Without it, the Windows CLI will look a lot different from the Mac / Linux CLI.

If you've never used the command line before, you might want to learn more about it here.

### Git vs. Github

When using the command line, you'll be working with Git. Git is the underlying version control system that GitHub makes use of. Some of the features we've discussed so far, such as pull request and issues, are functionality that GitHub adds. Others, like branching and commits, are Git functionality.

You can think of Git as a version control tool that you can use locally, and GitHub as a remote service that makes using that tool with other people on your team much more functional and seamless.

### Checking Git Version

Git is OS agnostic; the commands are essentially the same whether you are on Mac, Windows or Linux. You can use your favorite application to interact with the command line.

First, let's check the version of Git currently installed on your system by typing ```git --version``` into the command line. You should have the latest version of Git installed.

* Mac: 2.5.0
* Linux: 2.5.0
* Windows: 1.9.5

If you don't have the right version, or if you get an error saying Git isn't installed, then go to git-scm.com to download and install the latest version.

Once you've verified you have the latest version of Git installed, you're ready to move on to getting Git configured correctly.

### Git Configuration Levels

The first thing you should do when you get started using Git is to set your configuration options.

Git allows you to set configuration options at three different levels. The default value for Git config is ```--local```.

* ```--system``` - These are system-wide configurations. They apply to all users on this computer.
* ```--global``` - These are the user level configurations. They only apply to your user account.
* ```--local``` - These are the repository level configurations. They only apply to the specific repository where they are set.

### Pre-viewing Configuration Settings

If you would like to see which config settings have already been added, you can type ```git config --list```. This will automatically read from each of the storage containers for config settings and list them.

### Configuring User Name and Email

Go ahead and follow along as we set up our basic configurations. Git uses the config settings for your user name and email address to generate a unique fingerprint for each of the commits you create, so let's set our user name and email address first.

Type git config ```--global user.name "<your_full_name>"``` and type git config ```--global user.email "<your_email>"```.

Make sure to use the same email address that's associated with your GitHub account.

### Configuring Default Editor

Next, we will add a default text editor. This is the text editor Git will use when you need to edit things like commit messages or handle merge conflicts.

Typing git config ```--global core.editor "atom --wait"``` will tell Git to use the open source atom text editor.

### Configuring Autocrlf to Handle Whitespace

Different systems handle line endings and line breaks differently. If you open a file created on another system and do not have ```autocrlf``` set, Git will think you made changes to the file based on the way your system handles this type of file.

Type ```git config --global core.autocrlf```.

* If you are on a Windows machine, you will want to set this option to ```true```.
* If you are on a Mac or Linux machine, you will set it to ```input```.

And for those wondering, ```autocrlf``` stands for "auto carriage return line feed".

### Configuring Default Push Behavior

One final configuration option we will want to set is our default value for push.

When you push changes from your local computer to the remote you can choose whether you want Git to automatically push all of the local branches to their matching branches on the remote or whether you only want the currently checked out branch to be pushed.

The config setting we use to set this option is ```push.default```. We can set the default to ```matching``` if we want to push all branches automatically. OR, we can set it to ```simple``` if we only want to push the branch we are on.

For now, let's use ```git config --global push.default simple```. This way you don't make accidental pushes while you're still learning to use Git.

### Viewing Configuration Settings

Now that we have made some changes to your configuration options, let's take another look at ```git config --list```. You may notice duplicate settings if the same variable is set in multiple levels (such as ```--global``` and ```--local```). The lowest value on the list takes precedence.

## Using Github Locally

### Cloning a Repository

Part of what makes git such a well-loved VCS is that it easily lets everyone on the team have their own local working repository. It's expected that everyone will work on their own computer, and sync changes they've made with each other only when they need to.

But first, we have to make a local copy of your repository. To do this, we have to "clone" the repository that you have hosted on GitHub.

When you clone a GitHub repository you are creating a copy of everything in that repository, including its history. This is one of the benefits of a distributed VCS like git—rather than being required to query a slow centralized server to review the commit history, queries are run locally and are lightning fast.

#### Cloning a Repository

* Start a new branch on GitHub to work on.
* Copy the clone URL on GitHub.
* Using the command line, ```cd``` to the directory that you want to put your local repo in.
*Type ```git clone <clone_url>```.
* You might be prompted for your password. You should enter your GitHub password at this point.
* ```cd``` into the new cloned repo and type git status.
* ```git branch``` will show you the available branches. Only master appears.
* ```git branch -a``` will show all the remote branches.
* ```git checkout <branchname>``` will create a local branch that matches the remote branch. All edits you make locally with be applied to that branch until you checkout another one.

### Editing Local Files

Now that you have cloned the repository and checked out your branch, you are ready to make some changes to the local files. If you are familiar with using the command line to open and edit files, then much of this will be familiar to you. The only difference here is that we will be making our changes on a branch. Let's add more information to the bio we created earlier.

#### Summary

* ```git branch``` to make sure you're on the right branch.
* ```cd``` to the proper directory, then open the file with your text editor.
* Make the changes, then save them.

### The Two Stage Commit

After you have finished making your changes, it is time to commit them. When working from the command line, you will need to be familiar with the idea of the two stage commit.


When you work locally, your files exist in one of four states. They are either untracked, modified, staged, or committed.

An untracked file is one that is not currently part of the version controlled directory—such as any new files or files whose names have been changed.

Modified files are any files that you have edited and saved since the last time you committed.

Untracked and modified files exist in your working directory.


To add these files to version control, you will create a collection of files that represent a discrete unit of work. This way if you want to revert something in the future, it's easier to find and revert only the mistaken changes.

We build this unit of work in the staging area.

To add files to staging, you use the ```git add <filename>``` command.

Staging is important because it lets you only stage some of your new or modified files. For instance, if you've added a new variable and fixed a typo, you might want to commit those two changes separately. To do this, you stage and commit each one separately.


When we are satisfied with the unit of work we have assembled, we will commit everything in the staging area.

To commit files, use the ```git``` commit command.

Once changes are committed, the changes are added to the history of that branch, so that you can later see those specific changes, and even undo them if need be.


To review:

In order to make a file part of the version controlled directory we will first do a git add of only those files we want to commit together, and then we will do a git commit to add those changes to the Git version control history. Once the changes are commited, you'll always have a record of them in that state, even after you've changed them again in the working directory.

All of this happens locally, on your computer.

Let's do it now.

#### Summary

* ```git status``` lets you see which files have been changed since the last commit.
* ```git add <filename>``` adds that file to the staging area.
* ```git add .``` adds all the changed and untracked files to staging.
* ```git commit``` will submit all those file changes under one unit of work.
* This also opens your default text editor (as set earlier in this lesson) for you to add a commit message.
* This commit will happen locally, and only on the checked out branch. If you check out another branch, the changes will no longer show in that file.

### Pushing changes

Now that you've committed files locally, it's time to make sure that your remote repository also reflects those changes. So we'll '''push''' the files and version history up to GitHub.

#### Summary

* Check ```git status```: the working directory needs to be clean. If it's not, make sure there isn't anything that you meant to commit!
* Do ```git push```: assuming you set the default push behavior to simple, this will push your changes to the same branch on the remote system.
* Back in GitHub, you can easily start a new pull request to merge the changes into ```master``` using the same process you learned earlier.

## The Workflow End-to-End

### Updating Our Workflow

So far you've learned the most-used Git commands.

In this section, we'll show you how to do certain things locally instead of on GitHub, as well as some shortcuts to make you even faster when using the command line.

### Options for Creating a Repository

All of the work we do in Git and GitHub happens inside of a repository. There are two ways to get started working with a new repository. You can:

1. Clone the repository from a remote.
2. Initialize Git in an existing local directory.

Since this class is designed to teach you how to use Git and GitHub effectively, we will focus on how to structure our work to support collaboration.

If I want to collaborate with you on a project then I will start a repository on GitHub. Let's discuss some best practices for GitHub repositories now.

#### Summary

* Use the green New button on the Repositories tab of your GitHub profile page.
* The name of your repository must be unique to your account.
* Choose whether your repo will be public or private.
* Anyone can can view, clone, or fork a public repo, but only collaborators can push changes to it.
*  Private repositories can only be viewed, cloned, etc. by collaborators you have added.
* You are allowed an unlimited number of public repos on your account, but must have a paid account to have any private repositories.
* A ```.gitignore``` file tells git which types of files it shouldn't bother tracking. GitHub allows you to auto-generate your ```.gitignore``` file.
* You should add an open source license to your repository if you'd like to make it open source.
* Once you've created your repo, you can add collaborators by searching for their GitHub user name in the ```Collaborators``` section of the repo.

### Creating Branches


* ```git branch``` shows which branch you're on locally, and which other local branches exist.
* ```git branch <new_branchname>``` creates a new local branch.
* You still must check out this new branch to edit it. ```git checkout <new_branchname>```

### Workflow Review

* ```git add .``` adds all modified or new files to be committed, so you don't have to write out each file.
* You can write your commit message along with your commit command using the syntax: ```git commit -m "<commit_message>"```.
* You should then push your changes up to GitHub. ```git push -u origin <branch_name>``` will push your local branch changes to a branch with the same name on GitHub, as well as set a setting such that in the future, ```git push``` alone will complete the same command.
* Once this is finished, you must create a pull request on GitHub, and merge it on GitHub once it's completed.

### Pulling Changes from the Remote

Before we can go on, we will need to update our local copy of the file.

We use push to send our changes to the remote, but we use pull to retrieve changes from the remote. When we pull the files from the remote, Git downloads a copy of the new commits that have been added to the branch since our last pull and then attempts to merge them into our local branch.

#### Summary



* When the remote repository has been changed (such as after someone else's pull request is merged), your local repository will not be updated until you choose for it to be.
* The command ```git pull``` will make your local working branch up to date with the remote version of that same branch.
* This will not delete local branches that have been deleted on the remote repo.
* To delete local branches that do not have a remote counterpart, use the ```git branch --merged``` command to list all such local branches, and then ```git branch -d <branchname>``` to delete specific local branches.

## Working Local Files

### Modifying Local Files

Now that you understand the foundations of Git, and how Git and GitHub work together, we're going to do a deep-dive into using Git while you edit your local files.

#### Summary

* There is only one working and one staging area, so you can create a branch after you've changed or added a file, and still commit that file to the new branch.
* ```git checkout -b "<new_branchname>"``` is a quick way to both create a new branch and check it out.
* If you edit a file after git adding it, then when you commit only the changes made before the ```git add``` will actually be commited. You must ``git add``` it again in order to commit all the changes.

### Comparing Local File States

In the last section, we made several changes to a local file, causing the file to appear in different stages of the commit process. The ```git diff``` command allows us to see what has changed in these different versions of our files. Let's explore some of these options now.

* ```git diff``` allows you to compare different versions of a file against each other.
* On its own, ```git diff``` compares the working directory to the staged version of the file.
* ```git diff --staged``` compares the staged version to the most recent commited version.
* ```git diff HEAD``` combines the changes in your working and staged versions of the file, and compares them to the version of the file designated as HEAD (most often, the most recent commit).
* ```git diff --color-words``` displays a word-by-word comparision rather than a line-by-line comparison, helpful for small changes.

### What Happens When We Mege ?

Merging combines the history of two or more branches.

We have already learned how to merge our changes on GitHub using the pull request process, now let's learn how to merge our changes locally.

* When performing a merge, you need to have checked out the branch you are merging into.
* ```git merge <branchname_to_merge>``` will merge the branch locally.
* To send the merge to the remote, simply ```git push```. If you already have a PR for that branch open on GitHub, this will automatically close that PR.
* You must still delete the branch separately on GitHub (in the PR window) and locally (using ```git branch -d <branchname>```).

### Viewing Project History

* ```git pull``` updates the local directory to include all the changes made to the remote directory, even those done by other people.
* ```git log``` provides a list of all of the commits on the current branch, with the most recent commit first.
* ```Up``` and ```down``` arrows navigate, ```enter``` cycles through log entries, and q quits log viewing screen.
* ```git log --oneline``` shows a smaller version of the log.
* ```git log --oneline --graph``` shows a graph of the changes along with the one-line log.
* ```git log --oneline --graph --decorate``` includes information about the branches and the head.
* ```git log --oneline --graph --decorate --all``` also includes unmerged branches.
* ```git log --stat``` tells you which files were included in each commit.
* ```git log --patch``` shows the actual changes that were made in each commit as diffs.

## Fixing Common Issues with Git

### Using Git to Fix Mistakes

One of the most powerful features of any VCS is the ability to undo your changes long after you save them.

Git offers all of the functionality that you'd expect from a full fledged VCS. In this section, we'll walk you through using Git on your computer to undo any changes you've already made with Git.

### Creating a Repository the Command Line

You'll only be working locally for this section, so you won't need to interact with GitHub. Thus, it's a good chance to learn how to use Git on the command line to create a new local repo.

On the next slide you'll learn how to use ```git init``` to create a local repository, and then we'll use that repo in the rest of this lesson.

* To create a project from scratch, type ```git init <directoryname>```.
* This creates the directory as a subdirectory of the current location, and initializes a repo there.
* You will have to create your ```README.md``` file manually.

### Handling Merge Conflicts

* When you have a merge conflict, type ```git status``` and look for "unmerged paths" to see which files are creating the merge conflict.
* Open the file in your text editor. You will see some lines that look like the following:
```
<<<<<<<< HEAD
Some text here.
========
Different text here.
>>>>>>>> merge-me
```
* The text above and below the equal signs are what is causing the merge conflict. They appear on the same line but are different text.
* Decide how you want to resolve the conflict, and once that's completed delete the merge markers. Save and close your text editor.
* ```git status``` will show that the files are no longer in conflict, but that you are in the middle of a merge. ```git add``` the file and then ```git commit``` it, and the merge will then automatically complete.

### Renaming and Moving Files

* When moving files, use the command ```git mv``` rather than just the ```mv``` command.
* The syntax for this is ```git mv <filename> <new_directory>/<filename>```.
* ```git mv``` automatically adds the file to the staging area after it is moved, so it can be commited right away.
* Just as with ```mv```, you can use ```git mv``` to rename a file like so:```git mv <filename> <new_filename>```.

### Reverting Commits

* When reverting, you revert a specific commit.
* Find that commit, and copy the first several characters of the SHA-1 hash.
* ```git revert <commit_hash>``` will create a new commit that is the exact opposite of the commit you're reverting.

### Fixing Bad Commits

* The command ```git commit --amend``` will add whatever is in your staging area to your last commit, and allow you to edit that commit message.

### Unstaging Files

* ```git reset HEAD <filename>``` will remove a file from the staging area, putting it back in your working directory.

### Git Reset

Sometimes we are working on a branch and we decide things aren't going quite like we had planned. We want to reset some, or even all, of our files to look like what they were at a different point in history. We can do that with ```git reset```.

Remember that there are three different snapshots of our project at any given time. The first is the most recent commit. The second is the staging area (also called the index). The third is the working directory (i.e. whatever you currently have saved on disk). The ```git reset``` command has three modes, and they allow us to change some or all of these three snapshots.

It also helps to know what branches technically are: each is a pointer, or reference, to the latest commit in a line of work. As we add new commits, the currently checked-out branch "moves forward," so that it always points to the most recent commit.

### Git Reset Modes



The three modes for git reset are: ```--soft```, ```--mixed```, and ```--hard```. For these examples, assume that we have a "clean" working directory, i.e. there are no uncommited changes.

* ```git reset --soft <my-branch> <other-commit>``` moves ```<my-branch>``` to point at ```<other-commit>```. However, the working directory and staging area remain untouched. Since the snapshot that ```<my-branch>``` points to now differs from the index's snapshot, this command effectively stages all differences between those snapshots. This is a good command to use when you have made a large number of small commits and you would like to regroup them into a single commit.

* With the ```--mixed``` option, Git makes ```<my-branch>``` and the staging area look like the ```<other-commit>``` snapshot. This is the default mode: if you don't include a mode flag, Git will assume you want ```--mixed```. ```--mixed``` is useful if you want to keep all of your changes in the working directory, but change whether and how you commit those changes.

* ```--hard``` is the most drastic option. With this, Git will now make all 3 snapshots -- , the staging area, and your working directory -- look like they did at ```<other-commit>```. This can be dangerous! We've assumed so far that our working directory is clean. If it is not, and you have uncommited changes, git reset --hard will delete all of those changes. Even with a clean working directory, use ```--hard``` only if you're sure you want to completely undo earlier changes.


* ```git revert``` reverts a specific commit. ```git reset``` resets git to a specific commit.
* ```git reset --soft <to_commit>``` resets git to a specific commit, and puts the commits you're resetting into the staging area where they can be easily re-committed.
* ```git reset --mixed <to_commit>``` resets git to a specific commit, and puts the commits you're resetting into the working directory so you can edit them directly.
* ```git reset --hard <to_commit>``` resets git to a specific commit, and deletes the commits you're resetting.
* Just like with ```git revert``` you can use the commit ID, or you can use the syntax ```HEAD~<number>```. The number you put will be the number of commits backwards from the current ```HEAD``` that git will move the new ```HEAD``` to.
* You can always use ```git log``` to see all your previous history to know where to reset to.

### Discarding Changes in Modified Files

* You can remove changes in the working directory using ```git checkout```.
* This is destructive! You will throw away the changes and not be able to get them back.
* ```git checkout --<filename>``` is the syntax. The ```--``` lets Git know you're talking about a file. This will revert the file to the version found in the last commit.
* This only works for files in the working directory. Files in the staging area or already commited won't be reverted.

* Just as ```git mv``` exists to move or rename a file and instantly add the change to the staging area, ```git rm``` exists to remove a file.
* ```git rm <filename>``` will remove the file and add the change to the staging area.

## Creating Shortcuts

### Creating Command Shortcuts

* You can create aliases in git that let you call on the short alias instead of writing out a full long command.
* You do this by setting a global alias using ```git config```.
* ```git config --global alias.lol "log --oneline --graph --decorate --all"``` would let you type git lol instead of the entire log command with all its options.
* ```git config --global alias.co "commit -m"``` would let you write ```git co "Commit Message"``` to quickly commit with a message attached
