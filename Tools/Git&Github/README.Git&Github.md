## **Structure for Working with Git & GitHub**

1. **Working Directory**
   - `git add` → **Staging Area**
   - `git commit` → **Local Repo**
   - `git push` → **Remote Repo (GitHub)**

---

## **Common Commands**

### 1. **Configuring the Repository for Command Line**

```bash
git config --global user.email "you@example.com"
git config --global user.name "Github_userName"
```

### 2. **Working with Files**

- `git help init` (open help for git in the browser)
- `git clone http://repo_link` (clone the repository to the local device)
- `git status` (check the status of the repo in the local device)
- `git add file_name` or `git add .` (add files to the staging area)
- `git add -f file_name` (force add a file to the staging area, even if ignored)
- `git reset HEAD file_name` (remove file from the staging area)
- `git restore --staged file_name` (remove file from the staging area)
- `git clean -n` (show files about to be removed)
- `git clean -f` (remove files from the working directory that are not in the staging area)
- `git commit -m "description about your work"` (move changes from staging to local repo)
- `git branch` (list all branch names in the local repo)
- `git remote -v` (show remote repository names)
- `git push remoteName BranchName` (push changes from local branch to remote)
- `git push remoteName BranchName --force` (force push changes from local branch to remote)
- `git push origin local_branch:remote_branch` (push local branch to a remote branch)
- `git pull remote-repo_name` (fetch new files from the remote repo)
- `git pull remote-repo_name branch_name --no-rebase` (fetch and merge with conflict options)
- `git branch New_branchName` (create a new branch)
- `git checkout branchName` (switch to a branch)
- `git checkout -b newBranch_name` (create and switch to a new branch)
- `git branch -d branch_name` (delete a branch)
- `git branch -D branch_name` (force delete a branch)
- `git branch -m old_name new_name` (rename a branch)
- `git push origin --delete remote_branch_name` (delete a remote branch)
- `git rm fileName` (remove a file using git)
- `git rm -r --cached folder_name` (remove folder from the Git repo but keep it locally)
- `git merge branch_name1` (merge the current branch with branch_name1)
- `git log` (show all commits)
- `git stash` (hide changes from the staging area)
- `git stash pop` (apply the latest stashed changes)
- `git stash list` (list all stashed changes)
- `git stash show` (show details of the latest stash)
- `git stash show stash@{stash_id}` (show specific stash)
- `git stash apply` (apply stash without removing it)
- `git stash pop stash@{stash_id}` (apply a specific stash and remove it)
- `git stash drop stash@{stash_id}` (remove specific stash)
- `git stash clear` (remove all stashes)
- `git reset --hard commit_hash` (reset to a specific commit)
- `git fetch origin branch_name` (fetch a branch from the remote repo)

### 3. **Git Configuration**

- `git config -l` or `git config --list` (show all git configurations)
- `git help config` (open git documentation)
- `git config --global conf_name` (get the value of a specific configuration)
- `git config --global conf_name "new_value"` (set the value of a specific configuration)
- `git config -l --show-origin` (print all sources of configuration data)
- `git config --global --unset conf_name` (remove a specific configuration)
- `git config --global --edit` (edit the config file via a text editor)
- `git config --global alias.command_1 command_2` (create an alias for a command)

### 4. **Configuring SSH Connection (Secure)**

```bash
ssh-keygen -t rsa -b 4096 -C "email_name" (generate SSH key)
cat path_for_generated_public_id (show the generated public key)
# Add the generated key to your GitHub account via the browser
ssh -T git@github.com (test the SSH connection)
```

### 5. **Tags and Releases**

- `git tag version_Name_Number` (add a lightweight tag)
- `git tag -a version_Name_Number -m "commit message"` (add an annotated tag)
- `git push remote_repo_name tag_name` (push a tag to remote)
- `git tag -l` (list all tags)
- `git tag -l "version_name"` (search for specific tags)
- `git tag -d "Tag_name"` (delete a tag locally)
- `git push origin --delete "Tag_name"` (delete a tag remotely)
- `git ls-remote --tags origin` (list tags in the remote repo)

### 6. **Remote Repository Management**

```bash
git init
git remote add origin https://github.com/remote-repo-name (add a remote repo to origin)
git remote set-url origin https://github.com/remote-repo-name (rewrite remote repo link)
```

### 7. **Workflow Files**

- Workflow files are stored in `.github/workflows` in your repo.

---

## **Additional Notes**

- **Difference Between Main Branch and New Branch**: New branches require a pull request, while the main branch can push changes directly.
- Use `touch test.txt`, `git add test.txt`, and `git stash -m "message"` to stash changes.
- The **HEAD** pointer indicates the latest commit.
- **.gitignore file**: Used to ignore files you don't want to track. Example entries:
  ```
  *.log       # Ignore all .log files
  !vip.log    # Do not ignore vip.log
  mm.txt      # Ignore this specific file
  ```
- **Tags**: If a tag is deleted from GitHub, it must also be removed from your local machine.
- Always commit changes individually for better control when undoing changes.
- **Commit Message Recommendation**: Keep it under 50 characters for clarity.
- **.gitkeep**: Used to create an empty directory in GitHub.
