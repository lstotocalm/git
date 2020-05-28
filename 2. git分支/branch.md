## 分支管理

1. 查看本地分支
  code: git branch

2. 查看本地分支&最后一次提交记录
  code: git branch -v

3. 查看已经合并到当前分支的分支
  code: git branch --merged

4. 查看还未合并到当前分支的分支
code: git branch --no-merged

5. 查看分支指向的对象(commit)
code: git log --oneline --decorate

6. 新建并切换分支
code: git checkout -b 新分支名
他是下面两条命令的缩写：
  git branch 新分支名
  git checkout 新分支名

7. 本地分支&远程分支不同名
code: git checkout -b new-xxx origin/xxx

8. 删除本地分支
code: git branch -d hotfix

9. 设置默认远程分支
code: git clone -o xxx

10. 修改跟踪分支
code: git checkout --track origin/xxx

11. 修改跟踪的上游分支
code: git branch -u origin/xxx

12. 查看所有分支详细信息
code: git branch -vv

13. 删除远程分支
code: git push origin --delete xxx