
### Windows 客户端

https://git-scm.com/download/win


### MacOS 客户端

苹果系统git客户端包含在Xcode Command Line Tools里，可以使用命令：
```sh
xcode-select --install
```

### Linux 客户端

Fedora/RedHat/CentOS
```sh
sudo yum install git
```

debian/ubuntu

```sh
sudo apt-get install git
```


### 文档

[Git Book](https://git-scm.com/book/zh/v2)

[git简明指南](http://rogerdudler.github.io/git-guide/index.zh.html)


### 代码递交规范

###### 梳理将要递交的文件
在做完一系列改动后，可以根据功能或问题的分类把一组变动梳理为一个commit。这样做的目的是便于代码review以及将来对问题进行追踪。

例如下面针对文件file1, file2, file3, file4的代码变动归纳为2个commit。
```sh
git commit file1 file2 -m "#3 bug1"
git commit file3 file4 -m "#4 bug2"
```


###### 注视信息规范

在注视的开头写明该commit关联的大功能模块分类，这样做可以方便的匹配注释来筛查代码。（此规范为linux内核等成功项目的要求）

```sh
git commit -a -m "payment/paypal: 修复支付系统错误。"
```

`commit与issue关联` 此规范为github开源项目通行标准，可以方便在关联issue页review代码变动。

代码递交时如果有存在的关联issue, 在comment里以#issues_id的形式与该issue关联

例如 issue(id=3) 为内容为报告bug 1，递交代码时通过在注释里添加`#issue—id`来进行关联。
```sh
git commit -a -m "#3 修复bug1"
```

### rebase (本地递交合并)
在推送代码到远程分之前，有时候可能需要对本地递交进行整理合并到一个commit，可以使用git rebase。

例如需要合并最后3个commit为一个：
```sh
git rebase -i HEAD~3
```
运行后会弹出编辑器让我们选择需要合并那个commit，把需要合并的commit由`pick`修改为`squash`
```sh
pick 033beb4 b1
squash d426a8a b2
squash c237a54 b3
```
保存离开后即可把commit b1 b2 b3 合并为一个commit



### 忽略文件模式
```sh
git config core.fileMode false
```
