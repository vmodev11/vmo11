## GIT POLICY
### Branch naming:
- `prod`, `release/x.x.x`, `stag`, `pre-stag`, `test`, `dev`, `feat/[tag-name]`, `bugfix/[tag-name]`, `feat/[tag-name]-stag`, `bugfix/[tag-name]-stag`, `hotfix/[tag-name]`
- `prod`: for production environment
- `release/x.x.x`: for release version
- `stag`: for staging environment
- `pre-stag`: prepare features for deployment in the `stag`
- `test`: for testing environment. Maybe called `dev` in some cases
- `dev`: whole code of project, prepare features for deployment in the `test`. Maybe called `pre-dev` in some cases
- `feat/[tag-name]` eg: `feat/auth`, `feat/user-management`, `feat/JIRA-TASK-ID`, `feat/[username]` ... for specific feature. If we have any different setting for other environment, add more suffix like that `feat/auth-stag`, `feat/[username]-stag`
- `bugfix/[tag-name]`: for fix bugs
- `hotfix/[tag-name]`: for hotfix on production enviroment (from production branch). After hotfix done, all of branches must be rebased this branch to get updated code.

**The number of branches depend on the specific project*

### Git flow
- Start a feature: `[dev] $ git checkout -b feat/new-feature`
- Create a pull request to finish a feature
- TL/PM/Senior Dev will check such PRs and then merge to dev branch

### Update latest code from remote:

1. If remote feature branch has update and local feature branch has no update:

    ```
    [feat/auth] $ git pull origin/feat/auth
    ```

2. If both remote feature branch and local feature branch have new update:

    ```
    [feat/auth] $ git stash
    [feat/auth] $ git rebase origin/feat/auth
    ```

3. or if ensure code would be committed

    ```
    [feat/auth] $ git commit -m "specific message"
    [feat/auth] $ git rebase origin/feat/auth
    ```

4. Do the same steps for develop branch
### Update code from parent branch(nearest parent)
1. After commit to parent branch, only need to rebase on feature branch:

    ```
    [feat/auth] $ git rebase dev
    ```

2. Same steps for Develop branch when master has new update
### Danger!!! Resolve conflict during rebase
1. Merge code manually

    ```
    [feat/auth] $ git add <change-file>
    ```
2. Continue rebasing when you have new file

    ```
    [feat/auth] $ git rebase --continue
    ```
3. Continue rebasing when you don’t have new file

    ```
    [feat/auth] $ git rebase --skip
    ```
4. Cancel rebase

    ```
    [feat/auth] $ git rebase --abort
    ```

### Push code to remote
1. Check other commits

    ```
    [feat/auth] $ git reabase origin/feat/auth
    ```
2. User push command

    ```
    [feat/auth] $ git push origin/feat/auth
    ```
3. **Danger!!!** In case of changing history on remote, add force option(need to confirm with TL/PM before run command)

    ```
    [feat/auth] $ git push --force origin/feat/auth
    ```

### Note
1. Commit format: 

    ```
    <Type>: <[JIRA_ID]> action description on/for screen/function
    ```
    - **Type** (required): A type of change that you're committing. eg: feat, fix, docs, style, refactor,...
    - **JIRA_ID** (optional): prefer to add, if not please create jira issue for this action
2. In case of processing commits separately, you can create a local branch then delete it after finished
3. Remove changes on local branch

    ```
    [feat/auth] $ git reset --hard origin/feat/auth
    ```

### Use SSH (REQUIRED)
1. [Create ssh key](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)
2. [Adding a new SSH key to your GitHub account](https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)
3. [Managing Multiple Git Accounts](https://medium.com/the-andela-way/a-practical-guide-to-managing-multiple-github-accounts-8e7970c8fd46)

### Tools
1. Suggestion for vscode: 
    - [Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph)
    - [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
    
2. NPM package
    
    ```
    $ yarn add -D commitizen
    $ ./node_modules/bin/commitizen init huyhq-cz-jira-smart-commit --yarn --dev --exact
    ```
    
    **package.json**
    ```json
    {
        ...
        "scripts": {
            ...
            "commit": "git cz"
        }
    }
    ```
    **Use**
    
    ```
    $ yarn commit
    ```
    
    ![](https://i.imgur.com/lZJLOaa.png)

3. GIT practice

    You can practice command with git at repo: https://github.com/vmodev11/git-practice

### Create PR from client (for second account)
1. Github
    - Install github CLI https://cli.github.com/
    - Main account create authentication token for second account (The minimum required scopes are 'repo', 'read:org', 'admin:public_key')
    - Second account login github CLI by SSH key and authentication token
    - How to use?
    ```
    $ gh auth login
    ```
    ![](https://i.imgur.com/2KFiaSW.png)

    ```
    $ gh pr create --base stag --head feat
    ```
    ![](https://i.imgur.com/OXQiLfL.png)

