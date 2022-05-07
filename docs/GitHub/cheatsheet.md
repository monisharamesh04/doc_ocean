
## `vs` Questions

-----------------

1. <http://stackoverflow.com/questions/804115>  (`rebase` vs `merge`).
2. <https://www.atlassian.com/git/tutorials/merging-vs-rebasing> (`rebase` vs `merge`)
3. <https://www.atlassian.com/git/tutorials/undoing-changes/> (`reset` vs `checkout` vs `revert`)
4. <http://stackoverflow.com/questions/2221658> (HEAD^ vs HEAD~) (See `git rev-parse`)
5. <http://stackoverflow.com/questions/292357> (`pull` vs `fetch`)
6. <http://stackoverflow.com/questions/39651> (`stash` vs `branch`)
7. <http://stackoverflow.com/questions/8358035> (`reset` vs `checkout` vs `revert`)
8. <http://stackoverflow.com/questions/5798930> (`git reset` vs `git rm --cached`)

## GENERAL QUESTIONS

--------------------

1. <http://stackoverflow.com/questions/5788037> (Recover from `git reset --hard`).
2. <http://stackoverflow.com/questions/1146973/> (Revert all local changes to previous state)
3. <http://effectif.com/git/recovering-lost-git-commits> (Recovering lost commit)

## SHORT GIT REFERENCE

----------------------

0. All Git tips (<https://github.com/git-tips/tips>). Must See.
1. First download the cheatsheet from official site: <http://git-scm.com>
2. Now only these commands are important:
    * Configuring : `config, help`.
    * Creating : `init, clone`.
    * Make Changes: `status, diff, add, commit, reset, rm, mv (not important)`.
    * Branching & Merging: `branch, checkout, merge, stash`
    * Review History: `log, tag, diff, show`
    * Update and Publish: `fetch, pull, push, remote`.
    * Very Imp: `reflog` . <http://effectif.com/git/recovering-lost-git-commits>
3. Commands that are not in cheatsheet (and advanced): `revert, apply, cherry-pick, rebase, clean, show-ref, update-ref, ls-files`
    * `git stash` is lightweight alternative to `git branch`.
4. For fast reference see: <http://gitref.org/>
5. Git Tips: <http://gitready.com/>
6. Git has three stages:
    * Committed : means data is safely stored in your local database.
    * Modified :  means you've changed the file but not committed.
    * Staged : means you've marked a modified file in its current version to go into your next commit snapshot.
7. Workflow of git:
    * Working Directory: holds the actual files
    * Index: Acts as a staging area. That is, snapshot for next commit. Will be done by `git add` command.
    * HEAD : Points to the last commit (and current branch) you've made.
8. Anything that is committed in Git can almost be recovered. However files which are not committed can't be recovered.
9. Description of Update and Fetch Commands:
    * `remote`: it only manage set of track repositories.
    * `fetch`: You can fetch new work from that remote server after cloning. Not similar to `clone`. You can later merge that repo with your existing with `merge` command.
    * `pull`: Automatically fetch and merge newest commit from remote server to local branch. By default, it combines fetch and merge.
    * `push`: This will push to the remote server from local branch.
10. When you do branch switching, files in your working directory will change to match that branch.
11. Using `git reflog` you can get back your destroyed commit (done via `git reset --hard`) using either  
    * `git checkout -b newBranchName <shaViaReflog>`
    * `git reset --hard <shaViaReflog>`
    But use it in rare cases, because you reflog keep state via sha and it's hard to see which sha belongs to specific commit.
12. `git cherry-pick` is a low level version of `rebase`.

### GIT TIPS AND SHORTCUTS

--------------------------
Most used commands are: `init, clone, status, log, add, commit, reset, rm, branch, checkout, merge, stash`

```bash
    ## -- Initializing a new git repository
        $$ git init

    ## -- Useful git log commands
        $$ git log --oneline        ## print short sha in one line
        $$ git log -3               ## show only first 3 commit
        $$ git log --author="John"  ## show commits only by this author


    ## -- Cloning a git repository
    ## The other protocols are: ssh, ftp, file://, http(s):// etc...
        $$ git clone git://github.com/something/foo.git

    ## -- Show the status of file
        $$ git status -s  # in short format

    ## -- Add the file to staging area.
        $$ git add foo.js bar.js   ## `--` is used to seperate files from `add` options.
        $$ git add .    # add all the files

    ## -- Show what have changed since you last commit
        $$ git diff  ## with a `--cached` option, show the changes that will go into the next commit snapshot.

    ## -- Commit the changes after you add the files to staging area
        $$ git commit -m 'with an inline message'

    ## -- Auto-commit and track changes to modified file.
    ## NOTE: The files you've not added doesn't track by commit with `-a` command.
        $$ git commit -a -m 'with an inline message'

    ## -- Ammend last commit (i.e, merge to previous commit)
    ## https://nathanhoad.net/git-amend-your-last-commit
    ## After doing `git add .`
        $$ git commit --amend   # alternate is `git reset --soft HEAD~`.
        ## amend a commit without changing previous message
        $$ git commit --amend --no-edit


    ## -- Unstage file from the index only.  See `git reset` also.
    ## NOTE: `git rm` without `--cached` will simply remove the file from both index and working directory.
        $$ git rm --cached  # exact opposite of git add.

    ## -- Throw away local changes after commit (Use with caution)
        $$ git checkout <file>  
        # if the branch name and file name are same, then do this
        $$ git checkout -- <file>
        ## for all changes (it's perfect for time travel on previous commit)
        $$ git checkout -f # or `git reset --hard` (but previous one is more safer because with that you're in detached state.)


    ## Delete a single entry from git reflog. (git reflog is useful as it keeps 2 months history).
        $$ git reflog delete HEAD@{N}    ## `N`: 1,2 etc... or <sha>

    ## Undo the last commit, but keep the history and adds a new history
    ## http://stackoverflow.com/questions/27032850/ (for `git reset` vs `git revert` with image)
        $$ git revert

    ## -- check where HEAD is
        $$ git show-ref

    ## Remove the initial commit (git reset doesn't work here, it works only after second commit)
    ## http://stackoverflow.com/questions/6632191/how-to-revert-initial-git-commit
        $$ git update-ref -d HEAD


    ## Push a specific branch
        $$ git push origin <mylocalbranch>

    ## -- Detailed explaination of `git reset` (all three options). P.S. Use git checkout for time travel.
    ## http://stackoverflow.com/a/6866485/2092405
    ## NOTE: All the below three options remove log, so if you want to get back to previous state, you can pick
    ## <sha> from git reflog and do git reset on this.
    ## Suppose the structure is
         A-B-C
             ↑ (master)
    ## Then, nuke commit C and never see it again. Do this:
        $$ git reset --hard HEAD~1
        ## the result is:
             A-B
               ↑ (master)
       ## To undo this command, use;
           $$ git reset --hard <newShaOfReflog>  ## or (git reset --hard HEAD@{1})

    ## Undo the last commit, but keep your changes in working directory.
    ## It will delete the index the from git log also and show you untracked and unstaged files:
        $$ git reset HEAD~1  ## move the pointer one index back (or git reset --mixed HEAD~1)
        ## the result is:
        A-B-C
          ↑ (master)
        ## To undo this command, use;
            $$ git reset <newShaOfReflog>  ## or (git reset HEAD@{1})

    ## Undo the last commit, but don't touch the index and working directory.
    ## When you do git status, you'll see that the same files are in the index as before.
    ## In fact, right after this command, you could do `git commit` and you'd be redoing the same commit you just had.
        $$ git reset --soft HEAD~1


    ## Add a changed file to old commit (not last commit). I.E., fix up old commit
    http://stackoverflow.com/a/2719659/2092405

    ## merge a specific commit from one branch to another branch.
        ## make sure you're in the branch where you want merge.
        $$ git cherry-pick <commit-id-of-feature-branch>

    ## Merge two specific commit together (using rebase)
    http://stackoverflow.com/questions/2563632/how-can-i-merge-two-commits-into-one

    ## Modify a specific commit in git
    http://stackoverflow.com/questions/1186535/how-to-modify-a-specified-commit-in-git
    ## if you're getting this error. Needs a single revision. See this: http://stackoverflow.com/questions/26174757/
    ## Option: 2
    $ git checkout <shaToThatCommit>
    touch newfile.txt
    git add .
    git commit --amend --no-edit
    git rebase --onto HEAD <shaToThatCommit> master  ## it will do automatic git checkout to master branch


    ## Branching and Merging
    ## ---------------------
    ## List out all the branches
    $$ git branch
    ## Create a new branch `testing` at your last commit
    $$ git branch testing
    ## Switch to branch
    $$ git checkout testing
    ## Shortcut to create a new branch and checkout
    $$ git checkout -b newbranch
    ## Delete a branch
    $$ git branch -d testing
    ## Merge the <branch> on the current working branch
    ## Merge tip: If you're doing merge say, from `wip` to `live` branch and you've edit `live` branch files
    ## then it will not undo changed file which is what we want.
    ## Also, merge conflict occurs when same file changed in both branch, you merged. You can reverse the merge conflict
    ## with `--abort` option
    $$ git merge testing    ## this will merge `testing` branch onto current (`master`) branch.
    ## checkout arbitrary commits instead of branch
    $$ git checkout HEAD~2
    ## Undo deleted branch
    $$ git reflog    ## to see the hash code of branch before deletion.
    $$ git checkout <hashcodeFromReflog>  ## to restore, and then create the same branch from there.

```

## Git reset vs Git revert

--------------------------
**NOTE**: `git revert` is advanced command and it may accidently delete your files, if you haven't committed.
<http://stackoverflow.com/questions/8358035/whats-the-difference-between-git-revert-checkout-and-reset>
Basically `git revert` undo changes with new commit history (i.e., introduce a new commit that reverse the specified one) while `git reset` (with `--hard`) **BEWARE**. Any changes to tracked files in the working tree and index are discarded.
`git reset` (with `--soft`) option doesn't touch the index file nor working tree. In this case, index file is staged but not committed and right after this command you can use `git commit`.
`git reset` (with `--mixed`) option reset the index but not the working tree. In this case, index file is not staged, so after this command you have to use `git add` and `git commit`.

## Git rm and Git reset

-----------------------
`git rm` remove the file from the index (with `--cached` option).
`git reset` is specifically about updating the index, moving the HEAD.
These two options are `equivalent only when we first add a file`. After that with `git reset` you can move the index while with `git rm --cached`, you completly destroy the index.

## Fix a `head detached from` message

-------------------------------------
<http://stackoverflow.com/questions/10228760/fix-a-git-detached-head>
Basically checkout the branch using `git checkout branchname`

## Relative Refs

----------------
<https://www.atlassian.com/git/tutorials/refs-and-the-reflog/refspecs>
The `~` character lets you reach parent commits. For eg: The following display the grandparent of HEAD:
`git show HEAD~2`. The `~` character will always follow the first parent of a merge commit.
If you want to follow different parent, use `^` character
For eg: If HEAD is the merge commit, then following returns the second parent of HEAD:
`git show HEAD^2`
Some examples:

```sh
    # Only list commits that are parent of the second parent of a merge commit
    $$ git log HEAD^2
    # Remove the last 3 commits from the current branch
    $$ git reset HEAD~3
    # Interactively rebase the last 3 commits on the current branch
    $$ git rebase -i HEAD~3
```

## Git `fetch`, `pull`, `push`, `remote`

----------------------------------------
**NOTE: You can't push to non-bare repository if the branches are same on both remote and local server**
By default updating the current branch with non-bare repo is denied. If you're the only user, you can set git config
`git config --bool core.bare true` and then delete all files except `.git` in remote.
<http://stackoverflow.com/a/2933656/2092405>
Some common git urls:

```sh
    ssh://[user@]host.xz[:port]/path/to/repo.git/
    git://host.xz[:port]/path/to/repo.git/
    http[s]://host.xz[:port]/path/to/repo.git/
    ftp[s]://host.xz[:port]/path/to/repo.git/
    [user@]host.xz:path/to/repo.git/
    /path/to/repo.git/
    file:///path/to/repo.git/
```

`git pull` is basically shorthand for `git fetch` followed by `git merge FETCH_HEAD`
`git fetch`: Downlaod new data and branches from remote repository
`git push`: Push your new branches to remote repository.
`git remote`: Manage (list, add and delete) remote repository aliases.

1. To push local repository to your server

```sh
    ## On your server (create a bare repository)
    $$ git init --bare repo.git
    ## On local
    $$ git remote add origin ssh://server/var/www/frontend.git
    $$ git push origin master
    ## After that, use:
    $$ cd /var/www/; git init; git clone frontend.git

    ## or alternative way without bare repository
    ## switch to different branch locally
    ## and then on your server
    $$ git init
    ## from local repository
    $$ git push ssh://server/path/to/git otherBranch
    ## then merge the otherBranch to master in remote repository

    ## Shortcut without switching repository
    $$ git remote add origin ssh://server/path/to/git
    $$ git push origin master:someOtherBranch       ## this push from master to `someOtherBranch`.
```

#### END ####
