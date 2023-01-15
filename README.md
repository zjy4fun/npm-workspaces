## npm workspaces

link: https://docs.npmjs.com/cli/v7/using-npm/workspaces

node.js v18.13.0
npm     8.19.3


### 使用方式

1. 在已有项目下（已经含有 package.json），执行命令
```bash
npm init -w ./packages/a
```
创建工作区 a

2. 给一个工作区添加依赖

```bash
npm install abbrev -w a
```

3. 使用工作区(演示了工作区之间引用依赖)

```bash
// ./workspace-a/index.js
module.exports = 'a'

// ./lib/index.js
const moduleA = require('workspace-a')
console.log(moduleA) // -> a
```

4. 多工作区执行命令
```bash
npm run dev --workspace=a
```
```bash
npm run dev --workspace=a --workspace=b
```

5. 忽略缺失的脚本

不需要所有工作区都实现使用 npm run 命令运行的脚本

```bash
npm run dev --workspaces --if-present
```
