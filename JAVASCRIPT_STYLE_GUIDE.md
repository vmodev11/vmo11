## JavaScript Style Guide

### Airbnb JavaScript Style Guide, [see more](https://github.com/airbnb/javascript)

### React+TypeScript Cheatsheets, [see more](https://github.com/typescript-cheatsheets/react-typescript-cheatsheet)

### Note
1. [Javascript naming conventions](https://github.com/airbnb/javascript#naming-conventions)
2. [React naming conventions](https://github.com/airbnb/javascript/tree/master/react#naming)
3. [CSS-in-JS naming conventions](https://github.com/airbnb/javascript/tree/master/css-in-javascript#naming)

### Composing React Components
1. Structure
    ```
    components
    -- ComponentA.tsx
    -- ComponentB.tsx
    -- ...
    -- index.ts // use named export for all of components
    pages
    -- User
    ---- components
    ------ ListUsers.tsx
    ------ OtherComponent.tsx
    ------ ...
    ------ index.ts // use named export for all of components
    ---- index.tsx
    ---- type.ts    
    ```

### Tools
1. Suggestion for vscode:

    - [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
    - Create file `.prettierrc` at root folder
    ```
    {
      "singleQuote": true,
      "semi": true,
      "trailingComma": "all"
    }

    ```
    
    - [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
    - **[Settings Sync](https://github.com/shanalikhan/code-settings-sync)**

        **Use Public GitHub Gist. Read the details [here](https://dev.to/shanalikhan/how-to-share-your-visual-studio-code-settings-and-extensions-39k)**
        
        `GitHub Gist: 39c7c93d80f3110422b3a77794423203`
        
        **Font: [Fira Code](https://github.com/tonsky/FiraCode)**
        
        **Terminal font: [Powerlevel10k](https://github.com/romkatv/powerlevel10k) - [Oh my zsh](https://github.com/ohmyzsh/ohmyzsh)**
