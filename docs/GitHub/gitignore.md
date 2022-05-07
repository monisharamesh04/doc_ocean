
## Adding a .gitignore into an exiting repository

1. Create a .gitignore file within your repo using the touch command:
    * `touch .gitignore`

2. Commit all your pending changes using

3. Then run this command, which removes everything from index:
    * `git rm -r --cached .`
    * The **_git rm_** command deletes files both from the Git repository as well as the filesystem. Using the **_cached_** flag, the actual file on disk will not be deleted.

4. Then just stage all the files again by running:
    * `git add .`

5. Next Commit the staged changes, using:
    * `git commit -m ".gitignore is now working"`

6. Finally push the commit to your repo:
    * `git push origin /<master/branch_name/>`

<mark>Please be careful, when you push this to a repository and pull from somewhere else into a state where those files are still tracked, the files will be DELETED</mark>

### References

:pushpin:{.pushpin} [Stackoverflow: Apply .gitignore on an existing repository already tracking large number of files](https://stackoverflow.com/questions/19663093/apply-gitignore-on-an-existing-repository-already-tracking-large-number-of-file)
