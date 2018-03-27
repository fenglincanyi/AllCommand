| 命令      |     说明 |
| :-------- | --------:|
| git checkout -b name   |   新建一个分支|
| git rev-parse --short HEAD  |  查询最近一次 commit id （短：--short）|
| git show commit-id , git diff commit-id^! |  查询某次 commit 的更改信息|
|git log -n| 查询最近 n 次 提交|
|git branch -a (-a 包括远程的)| 列出所有分支|
|git pull --rebase; <br>git rebase --continue | rebase 相关:<br> 如果遇到冲突，请仔细看提示<br>1.解决冲突，并 add 冲突的文件<br>2.继续 rebase |
| git cherry-pick commit-id  会自动commit;<br>git push | git cherry-pick 的使用:<br>1.查询出有用的 commit-id<br>2.切换到当前需要的分支上 |
|git checkout -b new_branch commit_id | 以某次 commit id 拉分支|
|git fetch | 更新本地branch列表|
|git checkout -b local_name origin/branch_name | checkout out 远程分支到本地|
|git checkout -b local_name tag_name | 以tag来 checkout 一个新的分支|
|git format-patch commit-id |  打某次commit-id 的 patch|
|git format-patch commit-id -3   |  打某次commit-id及之前的几次 patch (如：3次之前)|
|git format-patch commit-id1..commit-id2   |  打某2次之前的提交的patch(commit-id1较早的时间点，commit-id2较晚的时间点)|
