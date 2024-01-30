# common git commands and fixes
## Branches

 ### Create new branch

`git branch <new-branch> // creates new branch based on the  checked out branch
git checkout -b <new-branch>`

### Deleting branches

* When you delete a branch from github online (remote) it does not automatically delete it from the local  (and vice versa)
* Note: deleting a branch does not delete or undo committing secrets
* Steps to delete:
    * (Switch from the branch you are about to delete first)
    * If it has been merged
        * `git branch -d branch-name`
    * If it hasn't been merged
        * `git branch -D branch-name`
* Note: Merge conflict happens when two different branches edit the  same file 

### List Branches

`git  branch -r`
 
### Create Branch from a previous commit

`git checkout <commit-id> `

### Rename a Branch
 * [Documentation](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/renaming-a-branch)  
 
### Reset  a branch to a specific commit 
* [Documentation](https://stackoverflow.com/questions/4372435/hobw-can-i-rollback-a-git-repository-to-a-specific-commit)

    * Be careful, this rewrites  history but may be necessary 


## Pull  Requests 
Best Practices

* To be done when you think  your branch is ready to be merged with the main/develop branch
* Reviewer will add comments  and ask for changes. 
    *  Make the changes on your local branch  and then push it again.
    * Your changes will show up  in the same pull request
    * 1 pull request == 1 branch
    * Once your branch has been  merged (either to main or dev), best practice to delete branch after

## Standard Adding and Committing Files Process

```git status (see what files have been modified)
git diff my_script_with_changes.py (look at changes)
git add my_script_with_changes.py (stage specific file(s))
git commit -m "my msg"
git push --set-upstream origin branch-name
```

## Random Tips and Tricks

### Clearing the Command Line
Depends on CLI:
* `Q + enter   //will clear the git commandcheck`
* `z + enter`
* `ctrl z `

### Cleaning  passwords from History
Several ways to avoid this terrible occurrence
  * Don't use `git add .` or `git add -A` to add files to the staging area. Instead, use `git add <file-name>` to add files individually.
  * Use a `.gitignore` file to prevent certain files from being added to the staging area.
  * Use a creds.ini file or other system to store passwords and other sensitive information outside of the repo.

BUT, if it does happen: 

[git Instructions](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository)

[BFG Instructions and Download](https://rtyley.github.io/bfg-repo-cleaner/#usage)
	

[How to create replacement text file instructions](https://dev.to/isaacadams/git-removing-or-replacing-sensitive-information-22n6)
* If replacement text or BFG  file is not found, try putting in the full path. Remember to switch the \  to / in the paths before running
* Follow the BFG  instructions plus a `git push —force `

 


### Rename  a file in the Repo

`git mv OLD-FILENAME  NEW-FILENAME`
 

### Remove file from repo
* stays in history, just removes from that commit

`git rm file_path`

### Bypassing Pre-Commit Hooks

If, for some reason, you want to make a commit without activating pre-commit hooks do the following:
`git commit -m "commit message" --no-verify`
