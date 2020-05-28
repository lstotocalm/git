## 储藏(stash)
**ps: x的值需要根据git stash list 获取**
1. 把代码存储到堆栈，类似存放到仓库
应用场景: 想要切换分支，但是还不想要提交之前的工作；所以储藏修改.
code: git stash  或  git stash save


2. 查看存储列表
code: git stash list

3. 应用储藏(恢复储存的代码)
**恢复最近储藏的代码**
code: git stash apply

**恢复指定储藏的代码**
code: git stash apply stash@{x}

4. 应用储藏2(在stage区域的文件不存储)
code: git stash --keep-index

5. 应用储藏3(储藏所有文件，包括未跟踪文件)
code: git stash -u

6. 应用储藏4(交互式储藏)
code: git stash --patch

7. 应用储藏5(merge储藏, 文件冲突也可以应用储藏)
code: git stash --index

8. 移除储藏记录
**移除指定储藏记录**
code: git stash drop stash@{x}

9. 应用并删除储藏记录
**应用并删除最近记录**
code: git stash pop

**应用并删除指定记录**
code: git stash pop stash@{x}

10. 从储藏创建一个分支
code: git stash branch new-branch



