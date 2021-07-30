
# 探索一个使用typescript的形式去开发npm包

## 设置为npm发包时的目录
package.json里的files, 这样对外的包只有/lib、package.json和README.md

## 每次需要重新打包因为打包文件不上传github
.gitignore

### 存储
github只存储开发流程的东西，打包后的东西不存。 git commit 的时候format缓存区的内容

### npm发包
先npm run build，build后通过prettierrc来format，打出来的那个包



