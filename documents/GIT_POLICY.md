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
- Start a feature from code base branch: `[dev] $ git checkout -b feat/new-feature`
- Create a pull request to finish a feature
- TL/PM/Senior Dev will check such PRs and then merge to dev branch

### Note
1. [Commit convention](https://www.conventionalcommits.org/en/v1.0.0/#specification)

    ```bash
    type(scope?): subject  #scope is optional; multiple scopes are supported (current delimiter options: "/", "\" and ",")
    ```
    - **Type** (required): A type of change that you're committing: `build`, `ci`, `chore`, `docs`, `feat`, `fix`, `perf`, `refactor`, `revert`, `style`, `test`
    - **scope** (optional): Describes the module affected by your change or JIRA task ID

2. [Git Graph for VSCode](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph)

    - Let's use the graph to track commit history across branches

3. Keep commit history on working branches clean

    - Let's use rebase to update working branches
        ```bash
        git pull --rebase
        ```
        or
        ```bash
        git rebase [branch]
        ```

### Use SSH (REQUIRED)
1. [Create ssh key](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)
2. [Adding a new SSH key to your GitHub account](https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)
3. [Managing Multiple Git Accounts](https://medium.com/the-andela-way/a-practical-guide-to-managing-multiple-github-accounts-8e7970c8fd46)

### Setup Git local environment (REQUIRED)
1. Make pre-commit hook. At root directory of your project
```zsh
mkdir -p .git/hooks && touch .git/hooks/pre-commit && chmod +x .git/hooks/pre-commit
```
2. Get pre-commit script. At root directory of your project
```zsh
curl https://gist.githubusercontent.com/huyhavmodev/11581729cf4f1383a136a3f4bbcc327a/raw > .git/hooks/pre-commit
```
3. If you are using [husky@^7](https://github.com/typicode/husky) then run this command instead of 2 steps above
```zsh
npx husky add .husky/pre-commit ""
curl https://gist.githubusercontent.com/huyhavmodev/11581729cf4f1383a136a3f4bbcc327a/raw > .husky/pre-commit
```
**Once you're done with the configuration, the first commit will ask to configure git credentials locally in your terminal prompt.**

### More tool
1. Suggestion for vscode: 
    - [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
    
2. NPM package

    - [commitlint](https://commitlint.js.org/#/guides-local-setup)
    - [cz-jira-smart-commit](https://www.npmjs.com/package/@vmo11/cz-jira-smart-commit)
    
### Create PR from client (for second account)
1. Github
    - Install github CLI https://cli.github.com/
    - Main account create authentication token for second account (The minimum required scopes are `repo`, `read:org`, `admin:public_key`)
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

