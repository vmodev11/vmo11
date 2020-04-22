## GIT POLICY
### Update latest code from remote:

1. If remote feature branch has update và local feature branch has no update:

    `[feature] $ git pull origin/feature`

2. If both remote feature branch and local feature branch have new update:

    `[feature] $ git stash`
    `[feature] $ git rebase origin/feature`

3. or if ensure code would be committed

    `[feature] $ git commit -m "." `
    `[feature] $ git rebase origin/feature`

4. Do the same steps for develop branch
### Update code from parent branch(nearest parent)
1. After commit to parent branch, only need to rebase on feature branch:

    `[feature] $ git rebase dev`

2. Same steps for Develop branch when master has new update
### Resolve conflict during rebase
1. Merge code manually
    `[feature] $ git add <change-file>`
2. Continue rebasing when you have new file
    `[feature] $ git rebase --continue`
3. Continue rebasing when you don’t have new file
    `[feature] $ git rebase --skip`
4. Cancel rebase
    `[feature] $ git rebase --abort`

### Push code to remote
1. User push command
    `[feature] $ git push origin/feature`
2. In case of changing history on remote, add force option(need to confirm with TL/PM before run command)
    `[feature] $ git push --force origin/feature`

### Note
1. Commit format: 
    `Commit_Type Jira_Id: “action description on/for screen/function"`
    - **Commit_Type**: optional
    - **Jira_Id**: prefer to add, if not please create jira issue for this action
2. In case of processing commits separately, you can create a local branch then delete it after finished
3. Remove changes on local branch
    `[feature] $ git reset --hard origin/feature`

### Tools
1. Suggestion for vscode: 
    - [Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph)
    - [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
