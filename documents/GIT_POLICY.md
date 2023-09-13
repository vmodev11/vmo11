## GIT POLICY
### Branch naming:
- **Protected branches:** We should have protected branches.
  Which is always not easy to be merged. They can be different name in different projects.
  For example, in this document, we have branches: `master` and `product`.
  `master` should include well tested code,
  feature branches need to be reviewed by other devs before merged into `master`.
  And `product` should be the final result after each milestone we reach
  and be ready for production.
- **Feature branches:**
  the branches the developers be working on it.
  Include bug fix, new feature.
  Every feature branch should be corresponding with an issue be created on git server
  (github ,gitlab , etc...). A `feature branch` should be named as a standard format.
  I would love to propose a standard: `{issue_id}_{issue_name}` in this document.
  For example: `1_init_source_base`, `205_fix_bug_when_send_marketing_email`, ...
<details>
<summary>See some examples for branch naming</summary>
<p>

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
</p>
</details>  

**The number of branches depend on the specific project*
### **Issue:** 
May can be different name on jira (task, bug,...).
An issue should be full detail and informative. If it is a bug.
  It should give the link to the bug, describe how to reproduce the bug,
  the old state and the expected state.
### **Pull request:** 
(or `merge request` in other word. In this doc I call it be `pr`.
  See [an example](https://github.com/decred/politeiagui/pull/2628))
  A `pr` is a proposal for merging a `feature branch` into `protected branch`.
  The `pr` should be fully informative of what issue it solves, what it does,
  what different it makes. A `pr` should be merged after code review and be tested by testers.
  This process ensure the code on `master` is always well structure and deliver correct features.
### **Review:** 
Everyone is advised to review other member's code.
  A full experience developer can help a newbie when he is reviewing the newbie's `pr`.
  While a newbie can learn from the senior dev's `pr`. But keep in mind that everyone can make mistake.
  So everyone is advised for reviewing.

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
1. Make `prepare-commit-msg` hook. At root directory of your project
    ```zsh
    mkdir -p .git/hooks && touch .git/hooks/prepare-commit-msg && chmod +x .git/hooks/prepare-commit-msg
    ```
    - Windows only
        ```zsh
        mkdir -p .git/hooks
        ```
2. Get pre-commit script. At root directory of your project
    ```zsh
    curl https://gist.githubusercontent.com/huyhavmodev/11581729cf4f1383a136a3f4bbcc327a/raw > .git/hooks/prepare-commit-msg
    ```
3. If you are using [husky@^7](https://github.com/typicode/husky) then run this command instead of 2 steps above
    ```zsh
    npx husky add .husky/prepare-commit-msg ""
    curl https://gist.githubusercontent.com/huyhavmodev/11581729cf4f1383a136a3f4bbcc327a/raw > .husky/prepare-commit-msg
    ```
    - Update `.husky\.gitignore` file
        ```
        _
        prepare-commit-msg
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
    - Main account create authentication token for second account https://github.com/settings/tokens (The minimum required scopes are `repo`, `read:org`, `admin:public_key`)
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

