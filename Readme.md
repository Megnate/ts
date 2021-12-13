配置 typescript 的开发环境的项目

生成原始的 package.json 文件：`npm init -y`

按照个人的编码习惯，在该文件顶部可以添加不同的模块加载方式：

- "type": "module" 表示作为 ES 模块进行加载

- "type": "commonjs" 或者是不修改，无扩展名的文件和.js 结尾文件将被视为 commonjs

- .mjs 文件是按照 ES 模块处理，.cjs 的文件都是按照 commonjs 模块来处理

若本地无安装 typescript，可输入一下命令进行全局安装：`npm install typescript -g`

初始化一份 TS 文件：`tsc --init`

将 tsconfig.json 文件中的 `"outDir: '/'"` 取消注释并修改，表示将转换好的 js 文件存放的位置.

开启 sourceMap

- 创建一个新的文件夹：`mkdir src`

- 创建一个新的 ts 文件：`echo "" >> index.ts`

- 修改 index.ts 文件

- 退回上一级：`cd..`

- `tsc`：进行转换。此时就会按照之前设定的路径生成一个文件夹以及其中转换好的文件，由于开启了 sourceMap，所以会存在一个 map 文件（出错之后会直接显式源代码，而不是转换之后的代码）

- 可以使用 node 命令来运行转换好的 js 文件

# 简化过程

以上的过程异常地繁琐，应当进行简化。

- 在 package.json 文件中的 script 选项添加一个键值对：`"watch": "tsc --watch"`

- 在终端中执行该指令: `npm run watch`

- 可以直接执行 js 文件

更加简化的过程：

- 新建一个文件夹 bin：`mkdir bin`

- 创建 js 文件：`echo "" >> bin.js`

- 在其中输入指令：`#!/usr/bin/env node`

- 引入编译好的 js 文件：`import * as bin from '../dist/index.js'`

- 如果是 苹果电脑，需要给 bin 文件夹加以权限啊：`chmod 755 bin/bin.js`

- 修改 package.json 文件，在其中添加 bin 对象，并给其添加一个指令

```json
"bin": {
    "run": "bin/bin.js"
}
```

- 终端输入：`npm link`。如果之前已经生成过一次指令，可以使用以下语句进行覆盖：`npm link --force`

- 终端执行：`run`，会执行 bin.js 这个文件。
  在该文件中声明了：会使用环境变量中的 node，并用 node 来执行下面的引入语句。引入语句会将编译后的文件进行执行。

至此简易的环境就构建成功了。

## 所有的来自于 B 站 up 主：-小左

==视频号：== BV1rP4y1p7sZ
