

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