# 探索一个使用 typescript 的形式去开发 npm 包

## 安装依赖

npm/cnpm install

## 设置为 npm 发包时的目录

package.json 里的 files, 这样对外的包只有/lib、package.json 和 README.md

## 打包后的内容不上传 github

通过.gitignore 处理
github 只存储开发流程的东西，打包后的东西不存。

eslint + prettier + husky + lint-staged + commitlint

### eslint 检查代码逻辑

### prettier 格式化代码样式使其更美观

两者会有一些配置上的冲突，但是有相关的库来解决这些不一致的规则，如 eslint-config-prettier。只需在.eslintrc 中,extend 中添加 "prettier" 就可以解决 eslint 和 prettier 的冲突。[github 传送门](https://github.com/prettier/eslint-config-prettier)

### husky

当您提交或推送时，您可以使用它来检查**您的提交消息**、**运行测试**、检查**代码**等。Husky 支持[所有 Git 钩子](https://git-scm.com/docs/githooks)。</br>

- [github 传送门](https://github.com/typicode/husky)</br>
- [官方文档](https://typicode.github.io/husky/#/)

#### 旧版 v4

```js
// .huskyrc.json (v4) 旧版
{
  "hooks": {
    "pre-commit": "npm test && npm run foo"
  }
}
```

#### 新版 v8

这个项目在.husky 里</br>

1. pre-commit 执行了代码风格检查 npx lint-staged
2. commit-msg 校验 commit 提交信息的规范

tips: 这个.husky 文件夹要上传到代码仓库。默认的.gitignore 会忽略掉这个文件夹

### lint-staged

对暂存的 git 文件运行 linter，不要让 💩 溜进你的代码库! [github 传送门](https://github.com/okonet/lint-staged)

- 从那`v10.0.0`以后，对原始暂存文件的任何新修改都将自动添加到提交中。如果您的任务之前包含一个`git add`步骤，请删除它。自动行为确保了较少的竞争条件，因为尝试同时运行多个 git 操作通常会导致错误。

### commitlint

commit 信息校验

### commitizen

通过命令行里添加引导流程，辅助 commit 信息规范提交信息

### standard-version

版本发布标准自动化</br>
standard-version 是一款遵循语义化版本（ semver）和 commit message 标准规范 的版本和 changlog 自动化工具 </br>
npm 仓库的主页上说明，**已弃用**。但是还是能用

## 总结

这一套组合拳下来，基本能满足日常的开发。

1. npm run build TS 转 JS
2. npm test 执行单元测试
3. git add . && npm run commit
4. git push
5. npm run changelog (可选）

## 思考

1. 这上面这一大堆如果每次都配是真的心累，如果能结合其中几项来做个包或插件就很方便了。
2. 结合发 npm 包场景还是不够方便，可以考虑做个工具，每次新开分支，能自动新增版本号。

> 参考文章</br> > https://juejin.cn/post/7038143752036155428 </br> > https://juejin.cn/post/7053730154710827045#heading-16
