# Git Tutorial

Git is the open source distributed version control system for tracking changes in source code during software development.It is designed for coordinating work among programmers, but it can be used to track changes in any set of files -- [source: [Wikipedia Git](https://en.wikipedia.org/wiki/Git)].

There are several Git hosting services available. Some of them are [GitHub](https://github.com/), [GitLab](https://about.gitlab.com/), [Bitbucket](https://bitbucket.org/product/), [Assembla](https://www.assembla.com/home), [Beanstalk](https://beanstalkapp.com/), [CloudForge](http://www.cloudforge.com/), [Codebase](https://www.codebasehq.com/), [Fog Creek Kiln](https://www.fogbugz.com/version-control), [planio](https://plan.io/), and [RhodeCode](https://rhodecode.com/) -- [source: [Git Hosting Services Compared](https://www.git-tower.com/blog/git-hosting-services-compared/)].

Each of these host has their own trade-offs and they can influence ones decision of which to host their repository. There are cases where you can also _Roll your own_ -- ([GitHub Alternatives](https://opensource.com/article/18/8/github-alternatives)) project and have full control. This is possible because Git is open source and it can be self-hosted. For the purpose of this tutorial, we will be focusing on GitHub.

First you have to check if Git is installed on your OS and you can do so by typing `git --version`. If Git is installed, the version number should be displayed.

This tutorial will be focused on:

1. [Setting up Git](#session7)
2. [Git Overview](#session6)
3. [Creating a repository](#session1)
4. [Cloning a repository from remote](#session2)
5. [Branching and merging in Git](#session3)
6. [Git GUIs](#session4)
7. [Summary and other useful commands](#session5)

## 1\. Setting up Git

It is good practise to setup your computer so you do not repeat the same thing over again. `git config` is a feature in Git which can be used to setup up in your computer. To view the current configuration or setup, you can type;

```
$ git config --list                # to view only the current configuration
$ git config --list --show-origin  # to view the file path of the config
```

However, there are 3 different levels of `git config` namely; `local`, `global` and `system`.

- `local` configs are only available for the current project and stored in .git/config in the project's directory.
- `global` configs are available for all projects for the current user and is stored in ~/.gitconfig.
- `system` configs are available for all the users/projects and stored in /etc/gitconfig.

Below is an example of creating a `global` config.

```
  $ git config --global user.name "sammens1991"
  $ git config --global user.email samuelmensah@aims.ac.za
```

So now when you type `git config user.name`, you should see your username displayed.

## 2\. Git Overview

There are two states in Git. These states are _track_ and _untracked_ states. Files in the tracked states are known by Git. These files may be Unmodified, Modified or staged. Untracked files are not known by Git.

![](/home/samuel/Documents/DataScienceGroup/tutorial_git/images/lifecycle.png)_The lifecycle of files in Git [source: [Pro Git](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)]_

## 3\. Creating a repository

## Create repositories

There are two main ways of creating a repository; either you create it from local or from remote.

### Creating repository from local

The steps involved in creating a repository from local includes initialising the directory, adding the local directory to remote, staging files to be added to Git, committing, and pushing your files to remote. The functions involved are `init`, `remote add`, `add`, `commit`, `pull`, and `push`. Below are the steps involved in creating a repository from local.

```
$ cd </path/to/directory/>       # changing directory
$ git init                       # initialising directory
$ git add [filename]
$ git commit -m 'The commit message'
$ curl -u 'USER' https://api.github.com/user/repos -d '{"name":"REPO"}'
$ git remote add [remote_name] [remote_URL]
$ git remote -v                  # this is to check your remote version
$ git push [remote_name] [master]
```

This is an example from my computer.

```
$ cd tutorial/
$ git init
$ git add tutorial.md
$ git commit -m 'This is my initial commit message'
$ curl -u 'sammens1991' https://api.github.com/user/repos -d '{"name":"tutorial"}'
$ git remote add origin https://github.com/sammens1991/tutorial.git/
$ git push origin master
```

### Creating repository from remote

The steps involved in creating a repository from remote may vary from one hosting service to the other but not very different. GitHub will be used as an example for this session and the steps involved are below;

- Create or login your account on GitHub.
- Click on the `+` button which is located at the top right corner of your GitHub page and select `New repository`.
- Type in your repository name the field provided. You can give a description to the repository if you want. It is a good practise to have a README.md for your repository.
- Click on the `Create repository` button.

## 2\. Cloning a repository from remote

Cloning a repository from remote means to have a copy of a directory on local. However, cloning a repository enables you to make changes only on the local. To be able to make changes to remote, you have to **fork** the repository first (forking a repository will be discussed in the next section). Below are the steps involved in cloning a repository from remote.

```
$ cd </path/to/directory>
$ git clone [remote_URL]
```

For an example,

```
$ cd Repository/
$ git clone https://github.com/sammens1991/tutorial.git

## 3\. Branching and merging in Git

Another useful command in Git is **branching** and **merging**. This command comes in handy when a one seeks to include new feature(s) in a development. During branching, a new copy of master is created and changes are made to this copy which is later merged with the master. Below are the steps to follow to create a branch;

```
$ git branch [branch_name]
$ git checkout [branch_name]
```

or you can also use the shortcut.

```
$ git checkout -b [branch_name]
```

It is important to note that, changes made in the branch will have to be merged to the master. First, you have to checkout to the master branch and merge the copy branch to the master. Do that by typing

```
$ git checkout master
$ git merge [branch_name]
```

Just changing staff. # this change is by Shankar.

### Forking a repository

If you want to contribute to a development which you did not create or do not have access to, you may have to **fork**. According to [Wikipedia](https://en.wikipedia.org/wiki/Fork_(software_development)), forking is when a developer makes copy of source code from one software package and start independent development on it, creating a distinct and separate piece of software. For example, if a developer want to contribute to [keras](https://keras.io/), he/she will have to fork the [keras repository](https://github.com/keras-team/keras/). Currently, there are 17.2k contributors to keras. To fork a GitHub repository, click on the `fork` button which is located at the top right side of the repository. To _unfork_ a repository, you simply have to delete the repository from your account.

## 4\. Git GUIs

```
$ gitk
```

## 5\. Summary and other useful commands

1. `git rm` -- to delete files from the git directory.
2. `git log` -- to view history.
3. `git status` -- to view the states of the files.
4. `git diff` -- to view changes of files that have not been staged yet.
5. `git mv` -- to rename files or move files.
6. `git reset` -- to unstage staged files.
7. `git fetch`
8. `git tag` -- to tag specific points in the repository.
9. `git show` -- to show detailed information on tagged files/versions.
10. `git mergetool` -- to resolve conflicts visually.
11. `git branch` -- to list all your current branch.
12. `git switch` -- a function to check out branches.
13. `git commit -a -m` -- an alternate way of staging and committing files.

[ref_1]: https://en.wikipedia.org/wiki/Git "Wikipedia Git"
[ref_2]: https://opensource.com/article/18/8/github-alternatives "GitHub Alternatives"
[ref_3]: https://www.git-tower.com/blog/git-hosting-services-compared/ "12 Git Hosting Services Compared"
[ref_4]: https://git-scm.com/downloads/guis "Git GUIs"
[ref_5]: https://try.github.io/ "Resources to learn Git"
[ref_6]: https://git-scm.com/docs/gittutorial "Git -- distributed even if your work isnt"
[ref_7]: https://www.vogella.com/tutorials/Git/article.html "Git Tutorial"
[ref_8]: https://gist.github.com/lifuzu/9490352 "Git configurations"
