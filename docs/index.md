### Git

```
git init
git remote add origin https://gitee.com/richren/demo-vue-ts.git
git remote set-url --add origin git@github.com:richren364/demo-vue2-ts.git
```

### `@vue/cli`创建的项目添加路由

```
vue add router
```

### 添加 typescript 支持

#### 已存在的项目添加 ts 支持

```
vue add @type/typescript
```

自动安装 dependencies 和 devDependencies：

- dependencies
  - `vue-class-component`: 提供使用 class 语法写 vue 组件
  - `vue-property-decorator`: 提供装饰器
- devDependencies
  - `@typescript-eslint/eslint-plugin`: 使用 eslint 校验 ts 代码
  - `@typescript-eslint/parser`: 将 Typescript 转换为 AST 供 ESLint 校验使用
  - `@vue/cli-plugin-typescript`: 使用 ts+ts-loader+fork-ts-checker-webpack-plugin 进行更快的类型检查
  - `@vue/eslint-config-typescript`: 兼容 eslint 的 ts 校验规则
  - `typescript`

#### typescript 常见配置

```json
{
  // 编译选项
  "compilerOptions": {
    "target": "esnext",
    "module": "esnext",
    "strict": true,
    "jsx": "preserve",
    "importHelpers": true,
    "moduleResolution": "node",
    "experimentalDecorators": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "sourceMap": true,
    "baseUrl": ".",
    "types": ["webpack-env"],
    "paths": {
      "@/*": ["src/*"]
    },
    "lib": ["esnext", "dom", "dom.iterable", "scripthost"]
  },
  "include": [
    "src/**/*.ts",
    "src/**/*.tsx",
    "src/**/*.vue",
    "tests/**/*.ts",
    "tests/**/*.tsx"
  ],
  "exclude": ["node_modules"]
}
```

#### 其他相关文件说明

- `src/shims-vue.d.ts`
- `src/shims-tsx.d.ts`

### 代码规范

### demo1: eslint + standard

```js
module.exports = {
    root: true,
    env: {
        node: true
    },
    extends: {
        // eslint-plugin-vue
        'plugin:vue/essential',
        // @vue/eslint-config-standard
        '@vue/standard',
        '@vue/typescript/recommanded'
    },
    parserOptions: {
        ecmaVersion: 2020
    },
    rules: {
        'no-console': process.env.NODE_ENV === 'production' ? 'warn' : 'off',
        'no-debugger': process.env.NODE_ENV === 'production' ? 'warn' : 'off',
    }
}
```

#### demo2: eslint + prittier

- eslint 配置文件
  ```js
  module.exports = {
    root: true,
    env: {
      node: true,
    },
    extends: [
      // eslint-plugin-vue
      'plugin:vue/essential',
      'eslint:recommended',
      '@vue/typescript/recommended',
      // @vue/eslint-config-prettier
      '@vue/prettier',
      // @vue/eslint-config-typescript
      '@vue/prettier/@typescript-eslint',
    ],
    parserOptions: {
      ecmaVersion: 2020,
    },
    rules: {
      'no-console': process.env.NODE_ENV === 'production' ? 'warn' : 'off',
      'no-debugger': process.env.NODE_ENV === 'production' ? 'warn' : 'off',
    },
  };
  ```
- .pritterrc 配置文件
  ```json
  {
    "tabWidth": 2,
    "useTabs": true, // 使用tab（制表符）缩进而非空格
    "singleQuote": true, // 单引号
    "printWidth": 175, // 一行超过175个字符就换行
    "semi": false, // 是否在行尾加分号
    "trailingComma": "none", // 数组、对象最后一个元素的尾逗号
    "bracketSpacing": true, // 花括号前后空格
    "jsxBracketSameLine": false, // 使多行JSX元素最后一行末尾的 > 单独一行
    "arrowParens": "avoid", //只有一个参数的箭头函数的参数是否带圆括号（默认avoid不带）
    "htmlWhitespaceSensitivity": "ignore" //  HTML 文件空格敏感度
  }
  ```
- vscode 配置文件

  ```json
  {
    "[html]": {
      "editor.defaultFormatter": "vscode.html-language-features"
    },
    "[javascript]": {
      "editor.formatOnSave": true,
      "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[vue]": {
      "editor.defaultFormatter": "octref.vetur"
    },
    "editor.codeActionsOnSave": {
      "source.fixAll": true
    }
  }
  ```
