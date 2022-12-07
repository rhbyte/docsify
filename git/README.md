# Git & docsify

> Git 基本操作

### Git 更新代码基本操作

**step1：进入你的项目目录**

**step2：拉取服务器代码，更新本地代码，避免覆盖他人代码**

> 输入命令： git pull  （拉取master分支的代码）

                        git pull origin dev  拉取dev分支的代码

**step3：查看当前项目中有哪些文件被修改过**

> 输入命令：git status

具体状态如下：

1：Untracked: 未跟踪,一般为新增文件，此文件在文件夹中, 但并没有加入到git库, 不参与版本控制. 通过git add 状态变为Staged.

2：Modified: 文件已修改, 仅仅是修改, 并没有进行其他的操作.

3：deleted： 文件已删除，本地删除，服务器上还没有删除.

4：renamed：

**step 4：将状态改变的代码提交至缓存**

> 输入命令：git add .

使用上面的命令将所有的修改的文件提交到缓存区

git add + 文件

git add -u + 路径：将修改过的被跟踪代码提交缓存

git add -A + 路径: 将修改过的未被跟踪的代码提交至缓存

**step 5：将代码提交到本地仓库中**

> 输入命令： git commit -m “修改说明”

**step 6：将缓存区代码推送到远程仓库**

> 输入命令：git push   （推送代码到master分支）

                        git push origin dev     推送代码到dev分支

推送时，秘密需输入系统生成的access token。

### docsify支持mermaid

在index.html中增加以下代码：

```html
<script src="//unpkg.com/mermaid/dist/mermaid.js"></script>
<script src="//unpkg.com/docsify-mermaid@latest/dist/docsify-mermaid.js"></script>
<script>mermaid.initialize({ startOnLoad: true });</script>
```

项目来源:[GitHub - Leward/mermaid-docsify](https://github.com/Leward/mermaid-docsify)
