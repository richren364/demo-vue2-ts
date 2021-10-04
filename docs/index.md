### `@vue/cli`创建的项目添加路由
```
vue add router
```

### 添加 typescript 支持
#### 已存在的项目添加ts支持
```
vue add @type/typescript
```
自动安装 dependencies 和 devDependencies：
- dependencies
  - `vue-class-component`: 提供使用 class 语法写 vue 组件
  - `vue-property-decorator`: 提供装饰器
- devDependencies
  - `@typescript-eslint/eslint-plugin`: 使用eslint校验ts代码
  - `@typescript-eslint/parser`: 将Typescript转换为AST供ESLint校验使用
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
    "types": [
      "webpack-env"
    ],
    "paths": {
      "@/*": [
        "src/*"
      ]
    },
    "lib": [
      "esnext",
      "dom",
      "dom.iterable",
      "scripthost"
    ]
  },
  "include": [
    "src/**/*.ts",
    "src/**/*.tsx",
    "src/**/*.vue",
    "tests/**/*.ts",
    "tests/**/*.tsx"
  ],
  "exclude": [
    "node_modules"
  ]
}
```

#### 其他相关文件说明
- `src/shims-vue.d.ts`
- `src/shims-tsx.d.ts`

### 代码规范
- demo1: eslint + standard
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
- demo2: eslint + prittier
  ```js
  module.exports = {
    root: true,
    env: {
        node: true,
    },
    extends: [
        // eslint-plugin-vue
        "plugin:vue/essential",
        "eslint:recommended",
        "@vue/typescript/recommended",
        // @vue/eslint-config-prettier
        "@vue/prettier",
        // @vue/eslint-config-typescript
        "@vue/prettier/@typescript-eslint",
    ],
    parserOptions: {
        ecmaVersion: 2020,
    },
    rules: {
        "no-console": process.env.NODE_ENV === "production" ? "warn" : "off",
        "no-debugger": process.env.NODE_ENV === "production" ? "warn" : "off",
    },
  };
  ```