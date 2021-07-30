# 探索一个使用 typescript 的形式去开发 npm 包

## 设置为 npm 发包时的目录

package.json 里的 files, 这样对外的包只有/lib、package.json 和 README.md

##

### 存储 github

#### 每次需要重新打包因为打包文件不上传 github

通过.gitignore 处理

github 只存储开发流程的东西，打包后的东西不存。 git commit 的时候 format 缓存区的内容

### npm 发包

先 npm run build，build 后通过 prettierrc 来 format，打出来的那个包

### Commit message

> 引用阮一峰老师的文章 https://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html

运行下面的命令，使其支持 Angular 的 Commit message 格式
以后，凡是用到 git commit 命令，一律改为使用 git cz。这时，就会出现选项，用来生成符合格式的 Commit message。

### 生成 Change log

> conventional-changelog-cli 的 github 链接 https://github.com/conventional-changelog/conventional-changelog/tree/master/packages/conventional-changelog-cli

在 package.json 里也添加了个 changelog 命令,在 pre-push 时运行生成。
