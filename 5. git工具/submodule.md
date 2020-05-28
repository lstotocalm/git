## 子模块(submodule)
> 参考git: https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E5%AD%90%E6%A8%A1%E5%9D%97

##### 1. 简介
```
有种情况我们经常会遇到：某个工作中的项目需要包含并使用另一个项目。 也许是第三方库，或者你独立开发的，用于多个父项目的库。 现在问题来了：你想要把它们当做两个独立的项目，同时又想在一个项目中使用另一个。

ps: 以上所说的就是公共库，子模块某种意义上就是公共库，为了多个项目公用一个模块，减少维护成本
```


##### 2. 创建子模块
```
code: git submodule add https://github.com/chaconinc/DbConnecto [diy-project-name]

ps: 
  1. 默认拉下的子仓库名是 DbConnecto，如果想自定义仓库名的话可以在以上命令后面再添加 自定义仓库名就行
  2. 产生.gitmodule, 保存了项目 URL 与已经拉取的本地目录之间的映射
```


##### 3. 克隆含有子模块的项目
```
code: git clone https://github.com/chaconinc/MainProject

result: 总仓库拉取到了代码，但子仓库代码并没有拉取到。

solution-1: 
  1. 初始化本地配置文件: git submodule init 
  2. 更新提交记录: git submodule update

solution-2:
  添加recursive参数: git clone https://github.com/chaconinc/MainProject --recursive
```

##### 4. *拉取上游修改(了解即可)
```
code-1: git submodule update --remote [project-name]

ps:
  1. 不指定拉取子仓库分支的话，默认为master
  2. 如果不传子仓库名，默认拉取所有子仓库
  3. 一执行以上命令，当前分支会切换到‘游离HEAD状态’
  4. 可以执行code-2命令拉取代码，这条命令不会改变当前分支

code-2: git submodule foreach git pull

```

##### 5. *游离HEAD状态(了解即可)
```
简介：分支处于游离HEAD状态，代表当前不在任意分支，默认会拉取master分支的最新记录。

**指定拉取子仓库分支**
code: git config -f .gitmodules submodule.DbConnector.branch stable
ps: DbConnector是子仓库名，stable是分支名
```

##### 6. *合并子仓库分支(了解即可)
```
简介：当我们子仓库新创建了分支，想吧master分支的代码合并过来，可以通过--merge参数
code: git submodule update --remote --merge
```

##### 7. 检验or推送子模块修改
```
  1. 检验是否有子模块代码未提交:
  code: git push --recurse-submodules=check

  2. 推送未提交子模块代码:
  code: git push --recurse-submodules=on-demand
```


##### 8. 子模块遍历
```
1. 所有子仓库保留到stash区域
code: git submodule foreach 'git stash'

2. 切换所有子仓库分支
git submodule foreach git checkout branch-name

3. 拉取所有子仓库代码
git submodule foreach git pull

4. 推送所有子仓库代码
git submodule foreach git push

```