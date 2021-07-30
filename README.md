# 探索一个使用 typescript 的形式去开发 npm 包

## 由于 husky 升级调用形式有调整

github 地址: https://github.com/typicode/husky

文档 https://typicode.github.io/husky/#/

### 当 commit 信息校验，不规范就不给 commit 通过

这个得先装才能执行 npm install，否则不生效

```js
  // 如果为yarn则需另外处理，请看上方文档里的Automatic (recommended)流程
  npx husky-init
  npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'
```

### 添加其他钩子辅助脚本

```js
  npx husky add .husky/pre-commit 'npm run pre-commit'
  npx husky add .husky/pre-push 'npm run pre-push'
  // 执行命令后需要在.husky/pre-commit 里删除npm test
```

## 安装依赖

npm/cnpm install

## npm 发包

先 npm run build，build 后通过 prettierrc 来 format，打出来的那个包

## Commit message

> 引用阮一峰老师的文章 https://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html

运行下面的命令，使其支持 Angular 的 Commit message 格式
以后，凡是用到 git commit 命令，一律改为使用 git cz。这时，就会出现选项，用来生成符合格式的 Commit message。

## 生成 commit 信息

CHANGELOG.md

> conventional-changelog-cli 的 github 链接 https://github.com/conventional-changelog/conventional-changelog/tree/master/packages/conventional-changelog-cli

在 package.json 里也添加了个 changelog 命令,在 pre-push 时运行生成。

## 设置为 npm 发包时的目录

package.json 里的 files, 这样对外的包只有/lib、package.json 和 README.md

## 打包后的内容不上传 github

通过.gitignore 处理

github 只存储开发流程的东西，打包后的东西不存。 git commit 的时候 format 缓存区的内容
