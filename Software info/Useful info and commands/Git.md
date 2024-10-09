## Git branches
Branches allow you to create a "playground" with the same files in the `master` branch.You can use this branch to build independent features, test new features, make breaking changes, create fixes, write docs or try out ideas without breaking or affecting the production code. When you're done, you merge the branch into the production `master` branch.

### How to git clone Branches
While you can clone repositories with the `git clone` command, keep in mind that this clones the branch and the remote `HEAD`. This is usually `master` by default and includes all other branches in the repository.
So when you clone a repository, you clone the `master` and all other branches. This means you will have to checkout another branch yourself.

Let's say your task on a project is to work on a feature to add passwordless authentication to a user dashboard. And this feature is in the `passwordless-auth` branch. 
You really don't need the `master` branch since your "feature branch" will be merged into `master` afterward.

Wondering where the **remotes/origin/..** branches came from?  
  
When you clone a repository, you pull data from a repository on the internet or an internal server known as the **remote**. The word **origin** is an alias created by your Git to replace the remote URL (you can change or specify another alias if you want).

These **remotes/origin/..** branches point you back to the origin repository you cloned from the internet so you can still perform pull/push from the origin.
So when you clone `master` onto your machine, `remotes/origin/master` is the original `master` branch on the internet, and `master` is on your local machine. So you will pull/push from and to the `remotes/origin/master`.

**In summary Remote is the URL that points you to the repository on the internet while Origin is an alias for this remote URL.**

There are two ways to clone a specific branch. You can either:

-   Clone the repository, fetch all branches, and checkout to a specific branch immediately.
 ```
git clone --branch <branchname> <remote-repo-url>
```

-   Clone the repository and fetch only a single branch.
```
git clone -b <branchname> <remote-repo-url>
```

### **Modify commit message**

Oops... You found a spelling mistake in the commit message. No worries, you can modify it:  

```
git commit --amend -m "new message"
```

**Add files to last commit**

You already have committed the changes but forgot to add some files. No problem, you can still add them to the commit:  

```
git add <file_name>
git commit --amend HEAD~1
```

**Undo commits**

If you want to undo the last commit but keep the changes:  

```
git reset --soft HEAD~1
```

If you want to undo both commit and changes: ⚠️ Be sure that you want to lose the changes:  

```
git reset --hard HEAD~1
```

Alternatively, if you want to undo all your local changes, you can reset to the origin version of the branch:  

```
git reset --hard origin/<branch_name>
```

If you want to undo the commit without altering the existing history. You can use `git revert`, this command undoes a commit by creating a new commit:  

```
git revert HEAD
```

If you have just resolved some conflicts, finished the merge, and push to origin. But wait, something went wrong...

The safe way to undo a merge commit that has already pushed to the remote branch is using the `git revert` command:  

```
git revert -m 1 <commit_id>
``` 

**Notes:**

https://about.gitlab.com/blog/2018/06/07/keeping-git-commit-history-clean/#situation-1-i-need-to-change-the-most-recent-commit
https://sethrobertson.github.io/GitFixUm/fixup.html#committed_really

-   You can also undo any number of commits. E.g:
    
    -   `git reset HEAD~3` (going back three commits before HEAD).
    -   `git reset --hard <commit_id>` (going back to a specific commit).
-   Use `git reset` if the commit is not pushed yet and you don't want to introduce a bad commit to the remote branch.
    
-   Use `git revert` to revert a merge commit that has already pushed to the remote branch.
    
-   Use `git log` to review the commit history.
    
-   If you prefer, you can also create a new commit with the fix.


### Pulling a remote branch and not showing on the local machine

There are a few reasons why a remote branch might not show up on your local machine after you've pulled it:

1.  You're not on the correct branch: Make sure you're on the branch you want to see the remote branch on. You can check your current branch by running `git branch` on the command line.
    
2.  You haven't created a local copy of the branch: When you pull a remote branch, you're bringing the branch down to your local machine, but you still need to create a local copy of the branch to work on. You can create a local copy of the branch by running `git checkout -b <branch-name> origin/<branch-name>`.
    
3.  The branch was deleted: If the branch was deleted on the remote repository after you pulled it, it will not appear on your local machine.
    
4.  Caching issue: Sometimes, Git doesn't always update the branch information immediately after you pull. Running `git fetch -p` will update your branch information and should show the remote branch if it exists.
    
5.  Git is not properly configured: Make sure that your git is properly configured with the remote repository. If not, you may need to add the remote repository again by running `git remote add origin <remote-repository-url>`
    
6.  The branch does not exist: The branch you are trying to pull might not exist in the remote repository. Make sure the branch name is correct and it exists in the remote repository

When you pull a remote branch, the branch information is downloaded to your local machine, but it is not automatically created as a local branch. Instead, it is stored in a special location called the "remote-tracking branch".

Remote-tracking branches are used to keep track of the state of branches on a remote repository. They allow you to see the commits that have been made to the remote branch since the last time you pulled, and to see how your local branches compare to the remote ones.

You can see the remote-tracking branches on your local machine by running `git branch -r` on the command line. These branches have the format `origin/<branch-name>` which represents the branch name in the remote repository.

You can also see the remote branches in the git GUI tools like SourceTree, GitKraken and others

To start working with a remote branch, you need to create a local branch that is based on the remote-tracking branch. You can do this by running `git checkout -b <local-branch-name> origin/<remote-branch-name>`. This will create a new local branch and set it to the same state as the remote branch that you pulled.

### Remove folder from remote gitlab

`git rm -rf --cache .idea`
`git commit -m "message"`
`git push`