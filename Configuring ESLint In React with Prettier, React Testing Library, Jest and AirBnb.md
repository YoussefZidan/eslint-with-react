
# Table of Contents <!-- omit in toc -->

- [1. Installing VSCode Extensions](#1-installing-vscode-extensions)
- [2. Installing the following packages as devDependencies](#2-installing-the-following-packages-as-devdependencies)
- [3. Creating configuration files](#3-creating-configuration-files)
- [4. Overriding VSCode Settings](#4-overriding-vscode-settings)
- [That's it!](#thats-it)

In this article we will configure linting in **React** projects with **VSCode**.

## 1. Installing VSCode Extensions

First you need to install the following extensions in VS Code.

- [ESLint Extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

## 2. Installing the following packages as devDependencies

- eslint
- eslint-config-airbnb
- eslint-config-prettier
- eslint-plugin-import
- eslint-plugin-jsx-a11y
- eslint-plugin-prettier
- eslint-plugin-react
- eslint-plugin-react-hooks
- eslint-plugin-testing-library
- prettier

by simply running the following command in terminal.

```
npm i -D eslint eslint-config-airbnb eslint-config-prettier eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-prettier eslint-plugin-react eslint-plugin-react-hooks eslint-plugin-testing-library prettier

```

## 3. Creating configuration files

Create the following files in the **root** _(same level as **/src** folder)_ of your project

- .eslintrc.json
- .eslintignore
- .prettierrc
- .prettierignore

.eslintrc.json

```json
{
  "root": true,
  "settings": {},
  "env": {
    "browser": true, // Enables browser globals like window and document
    "amd": true, // Enables require() and define() as global variables as per the amd spec.
    "node": true, // Enables Node.js global variables and Node.js scoping.
    "jest/globals": true,
    "es2021": true
  },
  "parserOptions": {
    "ecmaVersion": 2020, // Use the latest ecmascript standard
    "sourceType": "module", // Allows using import/export statements
    "ecmaFeatures": {
      "jsx": true // Enable JSX since we're using React
    }
  },
  "extends": [
    "airbnb",
    "prettier",
    "prettier/react",
    "plugin:testing-library/react",
    "plugin:jest/all"
  ],
  "plugins": ["prettier", "react", "react-hooks", "testing-library", "jest"],
  "rules": {
    "prettier/prettier": ["warn", {}, { "usePrettierrc": true }], // Use .prettierrc file as source
    "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }], // To allow importing .jsx files
    "no-console": 1,
    "no-unused-vars": 1,
    "import/no-unresolved": 2,
    "no-undefined": 2,
    "react/jsx-uses-vars": 2
    // add more rules here...
  }
}
```

.eslintignore

```
node_modules
```

.prettierrc

```json
{
  "printWidth": 100,
  "tabWidth": 2,
  "useTabs": false,
  "semi": true,
  "singleQuote": false,
  "trailingComma": "all",
  "endOfLine": "auto"
}
```

.prettierignore

```
node_modules
```

## 4. Overriding VSCode Settings

Create **.vscode** folder and inside of it **settings.json** file

> This is important due to different VSCode options among developers working on the same project.

settings.json

```json
{
  "eslint.options": {
    "configFile": ".eslintrc.json"
  },
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```

## That's it!

Now Press **Ctrl + Shift + U** to open the **Output** tap in VSCode, and from the Drop Down Menu select **ESLint** you should see something like this:

```
[Info  - 3:31:54 PM] ESLint server is starting
[Info  - 3:31:55 PM] ESLint server running in node v14.16.0
[Info  - 3:31:55 PM] ESLint server is running.
```

**Follow me on**

 <a href="https://www.linkedin.com/in/youssefzidan/" target="_blank">
    <img src="https://img.shields.io/badge/LinkedIn-%230077B5.svg?&style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn">
</a>
