## Reference
[w3schools](https://www.w3schools.com/git/git_branch_merge.asp?remote=github)
<!-- TOC tocDepth:2..3 chapterDepth:2..6 -->

- [Reference](#reference)
- [Git Tutorial](#git-tutorial)
  - [Check the git version](#check-the-git-version)
  - [Working with Git](#working-with-git)
  - [Configure Git](#configure-git)
  - [Initialize Git](#initialize-git)
  - [Git Staging Environment](#git-staging-environment)
  - [Git Commit](#git-commit)
  - [Git Commit without Stage](#git-commit-without-stage)
  - [Git Commit Log](#git-commit-log)
  - [Git Help](#git-help)
  - [Working with Git Branches](#working-with-git-branches)
  - [New Git Branch](#new-git-branch)
  - [Switching Between Branches](#switching-between-branches)
  - [Emergency Branch](#emergency-branch)
  - [Merge Branches](#merge-branches)
  - [Merge Conflict](#merge-conflict)
- [Git and GitHb](#git-and-githb)
  - [Push Local Repository to GitHub](#push-local-repository-to-github)
  - [Pulling to Keep up-to-date with Changes](#pulling-to-keep-up-to-date-with-changes)
  - [Git Fetch](#git-fetch)
  - [Git Merge](#git-merge)
  - [Git Pull](#git-pull)
  - [Push Changes to GitHub](#push-changes-to-github)
  - [Create a New Branch on GitHub](#create-a-new-branch-on-github)
  - [Pulling a Branch from GitHub](#pulling-a-branch-from-github)
  - [Push a Branch to GitHub](#push-a-branch-to-github)
  - [Working using the GitHub Flow](#working-using-the-github-flow)

<!-- /TOC -->
## Git Tutorial

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

### Configure Git

Now let Git know who you are. This is important for version control systems, as each Git commit uses this information:

#### Example

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

### Initialize Git

Once you have navigated to the correct folder, you can initialize Git on that folder:

#### Example

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

### Git Staging Environment

One of the core functions of Git is the concepts of the Staging Environment, and the Commit.

As you are working, you may be adding, editing and removing files. But whenever you hit a milestone or finish a part of the work, you should add the files to a Staging Environment.

**Staged** files are files that are ready to be **committed** to the repository you are working on. You will learn more about `commit` shortly.

#### Git Specific Files
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
#### Git Add More than One File
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

### Git Commit

Since we have finished our work, we are ready move from `stage` to `commit` for our repo.

Adding commits keep track of our progress and changes as we work. Git considers each `commit` change point or "save point". It is a point in the project you can go back to if you find a bug, or want to make a change.

When we `commit`, we should **always** include a **message**.

By adding clear messages to each `commit`, it is easy for yourself (and others) to see what has changed and when.

#### Example

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

### Git Commit without Stage

Sometimes, when you make small changes, using the staging environment seems like a waste of time. It is possible to commit changes directly, skipping the staging environment. The `-a` option will automatically stage every changed, already tracked file.

Let's add a small update to `README.md`:
And check the status of our repository. But this time, we will use the --short option to see the changes in a more compact way:

#### Example

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
### Git Commit Log

To view the history of commits for a repository, you can use the `log` command:

#### Example

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

### Git Help

If you are having trouble remembering commands or options for commands, you can use Git `help`.

There are a couple of different ways you can use the `help` command in command line:

- `git _command_ -help` -  See all the available options for the specific command
- `git help --all` -  See all possible commands

 Let's go over the different commands.

### Working with Git Branches

In Git, a `branch` is a new/separate version of the main repository.

Let's say you have a large project, and you need to update the design on it.

Branches allow you to work on different parts of a project without impacting the main branch.

When the work is complete, a branch can be merged with the main project.

You can even switch between branches and work on different projects without them interfering with each other.

Branching in Git is very lightweight and fast!

### New Git Branch
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

### Switching Between Branches
Now let's see just how quick and easy it is to work with different branches, and how well it works.

We are currently on the branch `hello-world-images`. We added an image to this branch, so let's list the files in the current directory:
```shell
$ls
README.md  file1.txt  file2.txt  new-branch-new-file.txt  test
```
We can see the new file `new-branch-new-file.txt`, and if we open the `README.txt`, we can see the code has been altered. All is as it should be.

Now, let's see what happens when we change branch to `master`
```shell
$git checkout master
Switched to branch 'master'
```
The new image is not a part of this branch. List the files in the current directory again:
```shell
$ls
README.md  file1.txt  file2.txt  test
```
`new-branch-new-file.txt` is no longer there! And if we open the `README.txt` file, we can see the code reverted to what it was before the alteration.

See how easy it is to work with branches? And how this allows you to work on different things?

### Emergency Branch
Now imagine that we are not yet done with hello-world-images, but we need to fix an error on master.

I don't want to mess with master directly, and I do not want to mess with hello-world-images, since it is not done yet.

So we create a new branch to deal with the emergency:
```shell
$git checkout -b emergency-fix
Switched to a new branch 'emergency-fix'
```
Now we have created a new branch from master, and changed to it. We can safely fix the error without disturbing the other branches.

Let's fix our imaginary error, add `assume we fix a error!` into `file1.txt`.

We have made changes in this file, and we need to get those changes to the master branch.

Check the status:
```shell
$git status
On branch emergency-fix
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   file1.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
stage the file, and commit:
```shell
$git add index.html
$git commit -m "updated index.html with emergency fix"
[emergency-fix dfa79db] updated index.html with emergency fix
 1 file changed, 1 insertion(+), 1 deletion(-)
```
Now we have a fix ready for master, and we need to merge the two branches.

### Merge Branches

We have the emergency fix ready, and so let's merge the master and emergency-fix branches.

First, we need to change to the master branch:
```shell
$git checkout master
Switched to branch 'master'
```
Now we merge the current branch (master) with emergency-fix:
```shell
$git merge emergency-fix 
Updating 7bf4a84..869e77c
Fast-forward
 file1.txt | 1 +
 1 file changed, 1 insertion(+)
```
Since the emergency-fix branch came directly from master, and no other changes had been made to master while we were working, Git sees this as a continuation of master. So it can "Fast-forward", just pointing both master and emergency-fix to the same commit.

As master and emergency-fix are essentially the same now, we can delete emergency-fix, as it is no longer needed:
```shell
$git branch -d emergency-fix
Deleted branch emergency-fix (was dfa79db).
```

### Merge Conflict

Now we can move over to hello-world-images and keep working. Add another image file (img\_hello\_git.jpg) and change index.html, so it shows it:

#### Example

```shell
$git checkout hello-world-images
Switched to branch 'hello-world-images'
```
Now, we are done with our work here and can stage and commit for this branch:
```shell
$git add --all
$git commit -m "added new image"
[hello-world-images 1f1584e] added new image
 2 files changed, 1 insertion(+)
 create mode 100644 img_hello_git.jpg
```

We see that index.html has been changed in both branches. Now we are ready to merge hello-world-images into master. But what will happen to the changes we recently made in master?
```shell
$git checkout master
$git merge hello-world-images
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.

```
The merge failed, as there is conflict between the versions for index.html. Let us check the status:
```shell
$git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:
        new file:   img_hello_git.jpg
        new file:   img_hello_world.jpg

Unmerged paths:
  (use "git add ..." to mark resolution)
        both modified:   index.html
```
**This confirms there is a conflict in `index.html`**, but the image files are ready and staged to be committed.

So we need to fix that conflict. Open `index.html` in our editor, and modify it manually.

Now we can stage index.html and check the status:
```shell
$git add index.html
$git status
On branch master
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:
        new file:   img_hello_git.jpg
        new file:   img_hello_world.jpg
        modified:   index.html
```
The conflict has been fixed, and we can use commit to conclude the merge:
```shell
$git commit -m "merged with hello-world-images after fixing conflicts"
[master e0b6038] merged with hello-world-images after fixing conflicts
```
And delete the hello-world-images branch:
```shell
$git branch -d hello-world-images
Deleted branch hello-world-images (was 1f1584e).
```
Now you have a better understanding of how branches and merging works. Time to start working with a remote repository!

## Git and GitHb

### Push Local Repository to GitHub
Since we have already set up a local Git repo, we are going to push that to GitHub:
```shell
$git remote add origin https://github.com/tyhiwzm/git-tutorial.git
# alternative command:
$ git remote add origin git@github.com:tyhiwzm/git-tutorial.git
```
`git remote add origin _URL_` specifies that you are adding a remote repository, with the specified `URL`, as an `origin` to your local Git repo.

check it:
```shell
$git remote -v
origin  git@github.com:tyhiwzm/git-tutorial.git (fetch)
origin  git@github.com:tyhiwzm/git-tutorial.git (push)
```

Now we are going to push our main branch to the origin url, and set it as the default remote branch:

#### Example
```shell
$git branch -M main
$git push -u origin main
```
**Note:** Since this is the first time you are connecting to GitHub, you will get some kind of notification you to authenticate this connection.

### Pulling to Keep up-to-date with Changes
When working as a team on a project, it is important that everyone stays up to date.

Any time you start working on a project, you should get the most recent changes to your local copy.

With Git, you can do that with `pull`.

`pull` is a combination of 2 different commands:

- `fetch`
- `merge`

Let's take a closer look into how `fetch`, `merge`, and `pull` works.

### Git Fetch
`fetch` gets all the change history of a tracked branch/repo.

So, on your local Git, `fetch` updates to see what has changed on GitHub:
```shell
$git fetch origin
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (3/3), done.
From github.com:tyhiwzm/git-tutorial
   855391f..c84c7d2  main       -> origin/main
```
Now that we have the recent `changes`, we can check our `status`:
```shell
$git status
On branch main
Your branch is behind 'origin/main' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)

nothing to commit, working tree clean
```
We are behind the origin/master by 1 commit. That should be the updated README.md, but lets double check by viewing the log:
```shell
$git log origin/main
commit c84c7d24bee2561a9677e1c0b098b5143047ba34 (origin/main)
Author: Tang Yuhan <125366634+tyhiwzm@users.noreply.github.com>
Date:   Tue Nov 19 19:25:43 2024 +0800

    Update README.md

commit 855391f3161039740b2c244cf3de59dbe7239a00 (HEAD -> main)
Author: tyhiwzm <nudt_tangyh@163.com>
Date:   Tue Nov 19 19:01:25 2024 +0800

    first commit
...
...
```
That looks as expected, but we can also verify by showing the differences between our local `main` and `origin/main`:
```shell
$git diff origin/main
diff --git a/README.md b/README.md
index 27c0a86..d5150a5 100644
--- a/README.md
+++ b/README.md
@@ -1,2 +1 @@
 # git-tutorial
-hello~
```
That looks precisely as expected! Now we can safely `merge`.

### Git Merge
`merge` combines the current branch, with a specified branch.

We have confirmed that the updates are as expected, and we can merge our current branch (`main`) with `origin/main`:
```shell
$git merge origin/main 
Updating 855391f..c84c7d2
Fast-forward
 README.md | 1 +
 1 file changed, 1 insertion(+)
```
Check our `status` again to confirm we are up to date:
```shell
git status 
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```
There! Your local git is up to date!

### Git Pull
But what if you just want to update your local repository, without going through all those steps?

`pull` is a combination of `fetch` and `merge`. It is used to pull all changes from a remote repository into the branch you are working on.

Make another change to the Readme.md file on GitHub.

Use `pull` to update our local Git:
```shell
$git pull origin 
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (3/3), done.
From github.com:tyhiwzm/git-tutorial
   c84c7d2..c2f2a52  main       -> origin/main
Updating c84c7d2..c2f2a52
Fast-forward
 README.md | 1 +
 1 file changed, 1 insertion(+)
```
That is how you keep your local Git up to date from a remote repository. In the next chapter, we will look closer at how `push` works on GitHub.

### Push Changes to GitHub
Let's try making some changes to our local git and pushing them to GitHub.
Change `index.html` and commit the changes:
```shell
$git commit -a -m "Updated index.html. Resized image"
[main 498ed35] Updated index.html. Resized image
 1 file changed, 16 insertions(+)
 create mode 100644 index.html
```
And check the status:
```shell
$git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```
Now push our changes to our remote origin:
```shell
git push origin 
Counting objects: 3, done.
Delta compression using up to 20 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 546 bytes | 546.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:tyhiwzm/git-tutorial.git
   c2f2a52..498ed35  main -> main
```
### Create a New Branch on GitHub
On GitHub, you can create a new Branch. Type in a descriptive name, and click Create branch, the name is "html-skeleton".

The `branch` should now be created and active. You can confirm which branch you are working on by looking at the branch button. See that it now says "html-skeleton" instead of "main"?

Start working on an existing file in this branch. Click the "`index.html`" file and start editing:

If you are happy with the change, add a comment that explains what you did, and click Commit changes.

You now have a new `branch` on GitHub, updated with some changes!

### Pulling a Branch from GitHub
Now continue working on our new `branch` in our local Git.

Lets `pull` from our GitHub repository again so that our code is up-to-date:
```shell
$git pull
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (3/3), done.
From github.com:tyhiwzm/git-tutorial
 * [new branch]      html-skeleton -> origin/html-skeleton
Already up to date.
```

Now our main `branch` is up to date. And we can see that there is a new `branch` available on GitHub.

Do a quick `status` check:
```shell
$git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```
And confirm which branches we have, and where we are working at the moment:
```shell
$git branch
* main
```
So, we do not have the new `branch` on our local Git. But we know it is available on GitHub. So we can use the `-a` option to see all local and remote branches:
```shell
$git branch -a
* main
  remotes/origin/html-skeleton
  remotes/origin/main
```
**Note:** `branch -r` is for remote branches only.
We see that the branch `html-skeleton` is available remotely, but not on our local git. Lets check it out:
```shell
$git checkout html-skeleton 
Branch 'html-skeleton' set up to track remote branch 'html-skeleton' from 'origin'.
Switched to a new branch 'html-skeleton'
```
And check if it is all up to date:
```shell
git pull
Already up to date.
```
Which branches do we have now, and where are we working from?
```shell
$git branch
* html-skeleton
  main
```
Now, open your favourite editor and confirm that the changes from the GitHub branch carried over.

That is how you pull a GitHub branch to your local Git.

### Push a Branch to GitHub
Let's try to create a new local branch, and push that to GitHub.

Start by creating a branch, like we did earlier:
```shell
$git checkout -b update-readme
Switched to a new branch 'update-readme'
```
And we make some changes to the README.md file. Just add a new line.

So now we check the `status` of the current branch.
```shell
$git status
On branch update-readme
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```
We see that `README.md` is modified but not added to the Staging Environment:
```shell
$git add README.md
```
Check the `status` of the branch:
```shell
$git status
On branch update-readme
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   README.md
```
We are happy with our changes. So we will `commit` them to the `branch`:
```shell
$git commit -m "Updated readme for GitHub Branches"
[update-readme 7508c27] Updated readme for GitHub Branches
 1 file changed, 1 insertion(+)
```
Now `push` the `branch` from our local Git repository, to GitHub, where everyone can see the changes:
```shell
$git push origin update-readme
Counting objects: 3, done.
Delta compression using up to 20 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 323 bytes | 323.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote: 
remote: Create a pull request for 'update-readme' on GitHub by visiting:
remote:      https://github.com/tyhiwzm/git-tutorial/pull/new/update-readme
remote: 
To github.com:tyhiwzm/git-tutorial.git
 * [new branch]      update-readme -> update-readme
```
Go to GitHub, and confirm that the repository has a new branch.

In GitHub, we can now see the changes and `merge` them into the master `branch` if we approve it.

If you click the "Compare & pull request", you can go through the changes made and new files added:

**Note:** This comparison shows both the changes from `update-readme` and `html-skeleton` because we created the new branch FROM `html-skeleton`.

If the changes look good, you can go forward, creating a `pull request`.

A pull request is how you propose changes. You can ask some to review your changes or pull your contribution and merge it into their branch.

Since this is your own repository, you can  `merge` your pull request yourself.

To keep the repo from getting overly complicated, you can delete the now unused branch by clicking "Delete branch".

An after you confirm that the changes from the previous branch were included, delete that as well.

At this point, the remote repository only has the master branch.

View the remote repository branch list:
```shell
$git branch -r
  origin/html-skeleton
  origin/main
  origin/update-readme
```
Very weird! Because we took one less step:
```shell
$git remote prune origin 
Pruning origin
URL: git@github.com:tyhiwzm/git-tutorial.git
 * [pruned] origin/html-skeleton
 * [pruned] origin/update-readme
```
Now check it:
```shell
$git branch -r
  origin/main
```

### Working using the GitHub Flow
On this page, you will learn how to get the best out of working with GitHub.

The GitHub flow is a workflow designed to work well with Git and GitHub.

It focuses on branching and makes it possible for teams to experiment freely, and make deployments regularly.

The GitHub flow works like this:

- Create a new Branch
- Make changes and add Commits
- Open a Pull Request
- Review
- Deploy
- Merge

You should already have a good understanding of how this works from the previous chapters. This chapter focuses on understanding how the flow makes it easy for you to work together.


#### Create a New Branch

Branching is the key concept in Git. And it works around the rule that the master branch is ALWAYS deployable.

That means, if you want to try something new or experiment, you create a new branch! Branching gives you an environment where you can make changes without affecting the main branch.

When your new branch is ready, it can be reviewed, discussed, and merged with the main branch when ready.

When you make a new branch, you will (almost always) want to make it from the master branch.

**Note:** Keep in mind that you are working with others. Using descriptive names for new branches, so everyone can understand what is happening.

#### Make Changes and Add Commits

After the new branch is created, it is time to get to work. Make changes by adding, editing and deleting files. Whenever you reach a small milestone, add the changes to your branch by commit.

Adding commits keeps track of your work. Each commit should have a message explaining what has changed and why. Each commit becomes a part of the history of the branch, and a point you can revert back to if you need to.

**Note:** commit messages are very important! Let everyone know what has changed and why. Messages and comments make it so much easier for yourself and other people to keep track of changes.

#### Open a Pull Request

Pull requests are a key part of GitHub. A Pull Request notifies people you have changes ready for them to consider or review.

 You can ask others to review your changes or pull your contribution and merge it into their branch.

#### Review

When a Pull Request is made, it can be reviewed by whoever has the proper access to the branch. This is where good discussions and review of the changes happen.

Pull Requests are designed to allow people to work together easily and produce better results together!

If you receive feedback and continue to improve your changes, you can push your changes with new commits, making further reviews possible.

**Note:** GitHub shows new commit and feedback in the "unified Pull Request view".

#### Deploy

When the pull request has been reviewed and everything looks good, it is time for the final testing. GitHub allows you to deploy from a branch for final testing in production before merging with the master branch.

If any issues arise, you can undo the changes by deploying the master branch into production again!

**Note:** Teams often have dedicated testing environments used for deploying branches.

#### Merge

After exhaustive testing, you can merge the code into the master branch!

Pull Requests keep records of changes to your code, and if you commented and named changes well, you can go back and understand why changes and decisions were made.

**Note:** You can add keywords to your pull request for easier searching!

## Git Contribute
### Add to Someone Else's Repository
At the heart of Git is collaboration. However, Git does not allow you to add code to someone else's repository without access rights.

In these next 3 chapters we will show you how to copy a repository, make changes to it, and suggest those changes be implemented to the original repository.

At the end of these chapters, you will have the opportunity to add a message to our public GitHub page: `https://w3schools-test.github.io/`

### Fork a Repository
A `fork` is a copy of a repository. This is useful when you want to contribute to someone else's project or start your own project based on theirs.

`fork` is not a command in Git, but something offered in GitHub and other repository hosts. Let's start by logging in to GitHub, and `fork` our repository:  
https://github.com/w3schools-test/w3schools-test.github.io

Now we have our own copy of `w3schools-test.github.io`.

Now let's look at how we add a local copy of this for us to work with.

### Clone a Fork from GitHub
Now we have our own `fork`, but only on GitHub. We also want a `clone` on our local Git to keep working on it.

A `clone` is a full copy of a repository, including all logging and versions of files.

Move back to the **original** repository, and click the green "Code" button to get the `URL` to `clone`.

Open your Git bash and `clone` the repository:
```shell
$git clone git@github.com:w3schools-test/w3schools-test.github.io.git
Cloning into 'w3schools-test.github.io'...
remote: Enumerating objects: 10838, done.
remote: Counting objects: 100% (2241/2241), done.
remote: Compressing objects: 100% (409/409), done.
remote: Total 10838 (delta 1958), reused 2017 (delta 1832), pack-reused 8597 (from 1)
Receiving objects: 100% (10838/10838), 11.20 MiB | 4.14 MiB/s, done.
Resolving deltas: 100% (6528/6528), done.
```

Take a look in your file system, and you will see a new directory named after the cloned project:
```shell
$ls
w3schools-test.github.io/
```

**Note:** To specify a specific folder to clone to, add the name of the folder after the repository `URL`, like this: `git clone git@github.com:w3schools-test/w3schools-test.github.io.git _myfolder_`

Navigate to the new directory, and check the `status`:
```shell
$cd w3schools-test.github.io
$git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```

And check the `log` to confirm that we have the full repository data:
```shell
$git log
commit facaeae8fd87dcb63629f108f401aa9c3614d4e6 (HEAD -> master, origin/master, origin/HEAD)
Merge: e7de78f 5a04b6f
Author: w3schools-test 
Date:   Fri Mar 26 15:44:10 2021 +0100

    Merge branch 'master' of https://github.com/w3schools-test/hello-world

commit e7de78fdefdda51f6f961829fcbdf197e9b926b6
Author: w3schools-test 
Date:   Fri Mar 26 15:37:22 2021 +0100

    Updated index.html. Resized image
    
.....
```
Now we have a full copy of the original repository.

### Configuring Remotes
Basically, we have a full copy of a repository, whose `origin` we are not allowed to make changes to.

Let's see how the `remotes` of this Git is set up:
```shell
$git remote -v
origin  git@github.com:w3schools-test/w3schools-test.github.io.git (fetch)
origin  git@github.com:w3schools-test/w3schools-test.github.io.git (push)
```

We see that `origin` is set up to the original "`w3schools-test`" repository, we also want to add our own `fork`.

First, we `rename` the original `origin` `remote`:
```shell
$git remote rename origin upstream
$git remote -v
upstream        git@github.com:w3schools-test/w3schools-test.github.io.git (fetch)
upstream        git@github.com:w3schools-test/w3schools-test.github.io.git (push)
```
Then fetch the `URL` of our own `fork`. And add that as `origin`:
```shell
$git remote add origin git@github.com:tyhiwzm/w3schools-test.github.io.git
$git remote -v
origin  git@github.com:tyhiwzm/w3schools-test.github.io.git (fetch)
origin  git@github.com:tyhiwzm/w3schools-test.github.io.git (push)
upstream        git@github.com:w3schools-test/w3schools-test.github.io.git (fetch)
upstream        git@github.com:w3schools-test/w3schools-test.github.io.git (push)
```
**Note:** According to Git naming conventions, it is recommended to name your own repository `origin`, and the one you forked for `upstream`
Now we have 2 remotes:

- `origin` - our own `fork`, where we have read and write access
- `upstream` \- the original, where we have read-only access

Now we are going to make some changes to the code. In the next chapter, we will cover how we suggest those changes to the original repository.

### Push Changes to Our GitHub Fork
We have made a lot of changes to our local Git.

Now we `push` them to our GitHub `fork`:

`commit` the changes:

```shell
$git push origin
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 16 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 393.96 KiB | 32.83 MiB/s, done.
Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/kaijim/w3schools-test.github.io.git
   facaeae..ebb1a5c  master -> master
```

Go to GitHub, and we see that the repository has a new commit. And we can send a Pull Request to the original repository.

Click that and create a pull request.

Remember to add an explanation for the administrators.

Pull Request is sent.

### Approving Pull Requests
Now any member with access can see the Pull Request when they see the original repository.

And they can see the proposed changes.

Comment on the changes and merge.

Confirm.

And changes have been `merged` with `master`.

