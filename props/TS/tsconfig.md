
```
$ npx tsc --init
```

```
{
  "compilerOptions": {
    "target": "ES6",
    "module": "ESNext",
    "allowJs": true,
    "sourceMap": true,
    "outDir": "dist",
    "noEmitOnError": true,
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "strict": true
  },
  "include": ["src/**/*"],
  "exclude": ["**/*.spec.ts"]
}
```

```
 {
  "compilerOptions": {
    "target": "ES6",
    /=/ Версия ECMAScript, к которой будет компилироваться код
    "module": "ESNext",
    /=/ Формат модулей (ESNext для использования import/export)
    "allowJs": true,
  //"sourceMap": true,
    "noEmitOnError": true,
    /=/ Не создает файлы JS, если во время компиляции возникают ошибки.
    "forceConsistentCasingInFileNames": true,
    /=/ Гарантирует, что при импорте будет указан правильный регистр имени файла.
    "jsx": "react",
    /=/ Тип JSX, используемый в React
    "strict": true,
    /=/ Включить строгие настройки TypeScript
    "esModuleInterop": true,
    /=/ Разрешить импорт модулей в стиле ES6
    "moduleResolution": "node",
    /=/ Отключение ошибок для импортов
    "outDir": "./dist",
    /=/ Создает файлы JS в папке, а не рядом (иначе может заменять исходники)
    "skipLibCheck": true
    /=/ Отключение проверок библиотек
  },
  "include": ["src/**/*"],
  "exclude": ["**/*.spec.ts"]
  /=/ Папки, которые нужно включить в компиляцию
}
```

## _TS + React + Vite_

### _Vite_

```
npm init @vitejs/app my-react-app --template react-ts
cd my-react-app

bun vite-tsconfig-paths
```

```
bun install typescript @types/react @types/react-dom --save-dev
bun install eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin --save-dev
bun install @babel/core @babel/preset-env @babel/preset-react @babel/preset-typescript --save-dev
```

```
|> vite.config.ts

import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';
import viteTsconfigPaths from 'vite-tsconfig-paths';

export default defineConfig({
  plugins: [react(), viteTsconfigPaths()],
	resolve: {
    alias: {
      /=/ Используем алиасы из tsconfig.json
      '@/*': '/src/*',
    },
  },
});
```

[Полная статья](https://www.robinwieruch.de/vite-typescript/)

### _tsconfig.json_

```
bun install typescript @types/react @types/react-dom --save-dev
bun install @typescript-eslint/eslint-plugin @typescript-eslint/parser --save-dev
bun install	@babel/core @babel/preset-env @babel/preset-react @babel/preset-typescript --save-dev
```

```
$ touch tsconfig.json tsconfig.node.json
```

```
|> tsconfig.json
{
  "compilerOptions": {
    "target": "ES2020",
    "useDefineForClassFields": true,
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "skipLibCheck": true,

    /* Bundler mode */
    "moduleResolution": "bundler",
    "allowImportingTsExtensions": true,
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "react-jsx",
    "noEmit": true,

    /* Linting */
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true,

    "baseUrl": ".",
    "paths": {
      "src/*": ["src/*"],
      "public/*": ["src/public/*"],
      "components/*": ["src/app/components/*"],
    }
  },
  "include": ["src/**/*"],
  "exclude": ["**/*.spec.ts"]
  "references": [{ "path": "./tsconfig.node.json" }]
}
```

```
|> tsconfig.node.json
{
  "compilerOptions": {
    "composite": true,
    "skipLibCheck": true,
    "module": "ESNext",
    "moduleResolution": "bundler",
    "allowSyntheticDefaultImports": true
  },
  "include": ["vite.config.ts"]
}
```

### _Eslint_

```
 module.exports = {
  extends: [
	  'eslint:recommended', 
	  'plugin:@typescript-eslint/recommended'
	],
  parser: '@typescript-eslint/parser',
  plugins: ['@typescript-eslint'],
  root: true,
};
```

```
module.exports = {
  extends: [
    'eslint:recommended',
    'plugin:@typescript-eslint/recommended',
    'plugin:@typescript-eslint/recommended-type-checked',
    'plugin:@typescript-eslint/stylistic-type-checked',
  ],
  plugins: ['@typescript-eslint'],
  parser: '@typescript-eslint/parser',
  parserOptions: {
    project: './tsconfig.json',
  },
  root: true,
  overrides: [
    {
      files: ['*.js', '*.jsx'],
      extends: ['plugin:@typescript-eslint/eslint-recommended'],
    },
  ],
  settings: {
    'import/resolver': {
      typescript: {
        alwaysTryTypes: true,
        project: './tsconfig.json',
      },
      node: {
        extensions: ['.js', '.jsx', '.ts', '.tsx'],
        moduleDirectory: ['node_modules', 'src/'],
      },
    },
  },
};
```

### _Babel_

```
$ bun install --save-dev @babel/preset-typescript
```

```
|> babel.config.json
{
  "presets": [
    ["@babel/preset-typescript", {
      "rewriteImportExtensions": true
    }]
  ]
}
```

## _package.json_

```
"scripts": {
  "dev": "vite",
//"build": "vite build",
	"build": "tsc && vite build",
  "serve": "vite preview",
  "lint": "eslint . --ext .js,.jsx,.ts,.tsx",
  "lint-fix": "eslint . --ext .js,.jsx,.ts,.tsx --fix"
},
```
