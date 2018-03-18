* 新建一个分支

git checkout -b name

* 查询最近一次 commit id （短：--short）

git rev-parse --short HEAD  

* 查询某次 commit 的更改信息

git show commit-id
git diff commit-id^!

* 查询最近 n 次 提交

git log -n

* 列出所有分支

git branch -a (-a 包括远程的)

* rebase 相关

git pull --rebase
如果遇到冲突，请仔细看提示
1.解决冲突，并 add 冲突的文件
2.继续 rebase 
git rebase --continue

* git cherry-pick 

查询出有用的 commit id
切换到当前需要的分支上
git cherry-pick commit id  自动 commit 
git push 

* 以某次 commit id 拉分支

git checkout -b new_branch commit_id
