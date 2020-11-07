# NCG Corp. ESLint rules

## Usage

```shell
npm i --save-dev @ngc-corp/eslint-rules
```

Create a `.eslintrc.js` file with the following content in the root of your project.

Please note that this is an example on how to configure a [React](https://github.com/facebook/react) based project written in [TypeScript](https://github.com/microsoft/TypeScript). Configuration highly depends on the project you are working on.

For this configuration you will also need a few extra packages.

```shell
npm i --save-dev babel-eslint eslint-plugin-babel eslint-plugin-react eslint-plugin-react-hooks @typescript-eslint/eslint-plugin @typescript-eslint/parser
```

```javascript
module.exports = {
  env: {
    browser: true,
    es2021: true
  },
  extends: [
    'eslint:recommended',
    './node_modules/@ngc-corp/eslint-rules/eslint/javascript.js',
    'plugin:react/recommended',
  ],
  parser: 'babel-eslint',
  parserOptions: {
    ecmaFeatures: {
      jsx: true,
    },
    ecmaVersion: 12,
    sourceType: 'module',
  },
  plugins: [
    'react',
    'react-hooks',
  ],
  overrides: [
    {
      files: ['*.ts', '*.tsx'],
      parser: '@typescript-eslint/parser',
      parserOptions: {
        project: ['./tsconfig.json'],
      },
      extends: [
        'plugin:@typescript-eslint/recommended',
        'plugin:@typescript-eslint/recommended-requiring-type-checking',
        './node_modules/@ngc-corp/eslint-rules/eslint/typescript.js',
      ],
      plugins: [
        '@typescript-eslint',
      ],
    }
  ],
};
```
