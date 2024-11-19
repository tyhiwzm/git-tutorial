

## Introduction
### Check the git version
```shell
$git --version
```

### Working with Git
- Initialize Git on a folder, making it a **Repository**
- Git now creates a hidden folder to keep track of changes in that folder
- When a file is changed, added or deleted, it is considered **modified**
- You select the modified files you want to **Stage**
- The **Staged** files are **Committed**, which prompts Git to store a **permanent** snapshot of the files
- Git allows you to see the full history of every commit.
- You can revert back to any previous commit.
- Git does not store a separate copy of every file in every commit, but keeps track of changes made in each commit!

## Configure Git

Now let Git know who you are. This is important for version control systems, as each Git commit uses this information:

### Example

```shell
$git config --global user.name "w3schools-test"
$git config --global user.email "test@w3schools.com"
```

Change the user name and e-mail address to your own. You will probably also want to use this when registering to GitHub later on.

**Note:** Use `global` to set the username and e-mail for **every repository** on your computer.

If you want to set the username/e-mail for just the current repo, you can remove `global`

**Check:**
```shell
$git config --list  
```

## Initialize Git

Once you have navigated to the correct folder, you can initialize Git on that folder:

### Example

```shell
$git init 
```

You just created your first Git Repository!

**Note:** Git now knows that it should watch the folder you initiated it on.

Git creates a hidden folder to keep track of changes.

Then we check the Git `status` and see if it is a part of our repo:
```shell
$git status
```
Files in your Git repository folder can be in one of 2 states:

- Tracked - files that Git knows about and are added to the repository
- Untracked - files that are in your working directory, but not added to the repository

## Git Staging Environment

One of the core functions of Git is the concepts of the Staging Environment, and the Commit.

As you are working, you may be adding, editing and removing files. But whenever you hit a milestone or finish a part of the work, you should add the files to a Staging Environment.

**Staged** files are files that are ready to be **committed** to the repository you are working on. You will learn more about `commit` shortly.

### Git Specific Files
We can add specific file to the Staging Environment:
```shell
$git add README.md
```
The file should be **Staged**. Let's check the status::
```shell
$git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   README.md
```
### Git Add More than One File
You can also stage more than one file at a time. Let's add 2 more files to our working folder. 
```shell
$git add --all
```
Using --all instead of individual filenames will stage all changes (new, modified, and deleted) files.
```shell
$git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   README.md
        new file:   file1.txt
        new file:   file2.txt
```
**Note:** The shorthand command for `git add --all` is `git add -A`

## Git Commit

Since we have finished our work, we are ready move from `stage` to `commit` for our repo.

Adding commits keep track of our progress and changes as we work. Git considers each `commit` change point or "save point". It is a point in the project you can go back to if you find a bug, or want to make a change.

When we `commit`, we should **always** include a **message**.

By adding clear messages to each `commit`, it is easy for yourself (and others) to see what has changed and when.

### Example

```shell
$git commit -m "First release of Hello World!"
[master (root-commit) 221ec6e] First release of Hello World!
 3 files changed, 26 insertions(+)
 create mode 100644 README.md
 create mode 100644 bluestyle.css
 create mode 100644 index.html
```

The `commit` command performs a commit, and the `-m "_message_"` adds a message.

The Staging Environment has been committed to our repo, with the message:  
"First release of Hello World!"

## Git Commit without Stage

Sometimes, when you make small changes, using the staging environment seems like a waste of time. It is possible to commit changes directly, skipping the staging environment. The `-a` option will automatically stage every changed, already tracked file.

Let's add a small update to `README.md`:
And check the status of our repository. But this time, we will use the --short option to see the changes in a more compact way:

### Example

```shell
$git status --short
 M README.md
```

**Note:** Short status flags are:

- ?? - Untracked files
- A - Files added to stage
- M - Modified files
- D - Deleted files

We see the file we expected is modified. So let's commit it directly:
```shell
$git commit -a -m "Updated README.md"
[master 3fdfe28] Updated README.md
 1 file changed, 21 insertions(+)
```

**Warning:** Skipping the Staging Environment is not generally recommended.

Skipping the stage step can sometimes make you include unwanted changes.
## Git Commit Log

To view the history of commits for a repository, you can use the `log` command:

### Example

```shell
$git log
commit 09f4acd3f8836b7f6fc44ad9e012f82faf861803 (HEAD -> master)
Author: w3schools-test 
Date:   Fri Mar 26 09:35:54 2021 +0100

    Updated index.html with a new line

commit 221ec6e10aeedbfd02b85264087cd9adc18e4b26
Author: w3schools-test 
Date:   Fri Mar 26 09:13:07 2021 +0100

    First release of Hello World!
```

## Git Help

If you are having trouble remembering commands or options for commands, you can use Git `help`.

There are a couple of different ways you can use the `help` command in command line:

- `git _command_ -help` -  See all the available options for the specific command
- `git help --all` -  See all possible commands

 Let's go over the different commands.

## Working with Git Branches

In Git, a `branch` is a new/separate version of the main repository.

Let's say you have a large project, and you need to update the design on it.

Branches allow you to work on different parts of a project without impacting the main branch.

When the work is complete, a branch can be merged with the main project.

You can even switch between branches and work on different projects without them interfering with each other.

Branching in Git is very lightweight and fast!

## New Git Branch
Let add some new features to our `index.html` page.

We are working in our local repository, and we do not want to disturb or possibly wreck the main project.

So we create a new `branch`:
```shell
$git branch hello-world-images
```
Now we created a new `branch` called "`hello-world-images`"

Let's confirm that we have created a new `branch`:
```shell
$git branch
  hello-world-images
* master
```
We can see the new branch with the name "hello-world-images", but the `*` beside `master` specifies that we are currently on that `branch`.

`checkout` is the command used to check out a `branch`. Moving us **from** the current `branch`, **to** the one specified at the end of the command:
```shell
$git checkout hello-world-images
Switched to branch 'hello-world-images'
```
Now we have moved our current workspace from the master branch, to the new `branch`.

We have made changes to a file and added a new file in the working directory (same directory as the `main` `branch`).

Now check the status of the current `branch`:
```shell
$git status
On branch hello-world-images
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        new-branch-new-file.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
So let's go through what happens here:

- There are changes to our `README.txt`, but the file is not staged for `commit`
- `new-branch-new-file.txt` is not `tracked`

So we need to add both files to the Staging Environment for this `branch`:
```shell
$git add --all
```
Using `--all` instead of individual filenames will **Stage** all changed (new, modified, and deleted) files.

Check the `status` of the `branch`:
```
$git status
On branch hello-world-images
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   README.md
        new file:   new-branch-new-file.txt
```
We are happy with our changes. So we will commit them to the `branch`:
```shell
$git commit -m "Added image to Hello World"
[hello-world-images 0312c55] Added image to Hello World
2 files changed, 1 insertion(+)
create mode 100644 img_hello_world.jpg
```
Now we have a new `branch`, that is different from the master `branch`.

**Note:** Using the `-b` option on `checkout` will create a new branch, and move to it, if it does not exist

## Switching Between Branches
Now let's see just how quick and easy it is to work with different branches, and how well it works.

We are currently on the branch `hello-world-images`. We added an image to this branch, so let's list the files in the current directory:
```shell
$ls
README.md  file1.txt  file2.txt  new-branch-new-file.txt  test
```
We can see the new file `new-branch-new-file.txt`, and if we open the `README.txt`, we can see the code has been altered. All is as it should be.

Now, let's see what happens when we change branch to master