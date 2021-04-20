## JavaScript Style Guide

### React linter custom rules, [see more](https://github.com/vmodev11/react-test-eslint)

### Airbnb JavaScript Style Guide, [see more](https://github.com/airbnb/javascript)

### React+TypeScript Cheatsheets, [see more](https://github.com/typescript-cheatsheets/react-typescript-cheatsheet)

### Note
1. Use `kebab-case` for all package, folder and file names.
1. [Javascript naming conventions](https://github.com/airbnb/javascript#naming-conventions)
2. [React naming conventions](https://github.com/airbnb/javascript/tree/master/react#naming)
3. [CSS-in-JS naming conventions](https://github.com/airbnb/javascript/tree/master/css-in-javascript#naming)
4. Interface & Type
    ```typescript
    export interface IUser {
        name: string;
        email: string;
        ...
    }
    
    export type TMember = {
        name: string;
        email: string;
        ...
    }
    ```
### Compose React components
1. Structure
    ```typescript
    components
    -- common
    ---- common-component-1.tsx
    ---- common-component-2.tsx
    ---- index.ts // use named export for all of components
    -- group-components
    ---- component-c1.tsx
    ---- compoennt-c2.tsx
    ---- index.ts // use named export for all of components
    -- component-a.tsx
    -- component-b.tsx
    -- ...
    -- index.ts // use named export for all of components
    pages
    -- user
    ---- components
    ------ list-users.tsx
    ------ other-component.tsx
    ------ ...
    ------ index.ts // use named export for all of components
    ---- index.tsx
    ---- type.ts // local interface or type
    configs // config for anything as axios config
    layouts // master layout
    helpers // helper or utilities function
    hooks // react custom hooks
    services // login (API)
    -- user
    ---- user.services.ts
    ---- user.interface.ts // or user.type.ts
    types // global interfaces or types
    -- response.interface.ts
    ```
2. Named Export
    ```typescript
    // ComponentA.tsx
    export const ComponentA: React.FC = () => <></>;
    ```
     ```typescript
    // ComponentB.tsx
    export const ComponentB: React.FC = () => <></>;
    ```
     ```typescript
    // index.ts
    export * from './ComponentA';
    ```
    ```typescript
    // how to use
    // AnyComponent
    import { ComponentA, ComponentB } from './components';
    // or
    import * as ComponentC from './components';
    ```

### Tools
1. Suggestion for vscode:

    - [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
    - Create file `.prettierrc` at root folder
    ```json
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
