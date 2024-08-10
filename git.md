### git ssh配置问题：git操作一直需要输入密码
在第一次配置git,生成ssh，rsa时，一路回车，不要单独输入密码，去创建就OK
<br>`ssh-keygen -t rsa -b 4096 -C "xxx@abc.com"`  一路回车，不设置密码

### 常用命令
| 命令      |     说明 |
| :-------- | --------:|
| git checkout -b name   |   新建一个分支|
| git rev-parse --short HEAD  |  查询最近一次 commit id （短：--short）|
| git show commit-id , git diff commit-id^! |  查询某次 commit 的更改信息|
|git log -n| 查询最近 n 次 提交|
|git log -p| 查询最近提交的完整历史，带有diff|
|git branch -a (-a 包括远程的)| 列出所有分支|
|git pull --rebase; <br>git rebase --continue | rebase 相关:<br> 如果遇到冲突，请仔细看提示<br>1.解决冲突，并 add 冲突的文件<br>2.继续 rebase |
| git cherry-pick commit-id  | git cherry-pick 的使用:<br>1.查询出有用的 commit-id<br>2.切换到当前需要的分支上 |
| git cherry-pick commit-id_old..commit-id_new (短id也可以)  | 多个连续的commit进行cherry-pick |
|git checkout -b new_branch commit_id | 以某次 commit id 拉分支|
|git fetch | 更新本地branch列表|
|git checkout -b local_name origin/branch_name | checkout out 远程分支到本地|
|git checkout -b local_name tag_name | 以tag来 checkout 一个新的分支|
|git format-patch commit-id |  打某次commit-id 的 patch|
|git format-patch commit-id -3   |  打某次commit-id及之前的几次 patch (如：3次之前)|
|git format-patch commit-id1..commit-id2   |  打某2次之间的提交的patch(commit-id1较早的时间点，commit-id2较晚的时间点)|
|git format-patch commit-id1^ commit-id2 > xxx.patch  |  比较2次之间的提交的patch, 写入到xxx.patch文件中|
|git apply xxx.patch  |  应用patch|
|git reflog (show branch_name)  | 查询分支的来源(加 show,查看某个分支的reflog)|




git reabse 简单使用说明：
分支：master
分支：feature_a, 从 master 拉出来的

1. 确保本地 master最新：
本地切换至：master，并pull
git pull --rebase
(如果使用 git pull, 远程master合并到本地master，会多一条merge commit)

2. 切分支到：feature_a：  
确保是最新的：git pull reabse
合代码： git rebase master

3. 如果遇到冲突：
报错：xxxx，那就解决冲突, 
解决完，git add . 

4. 完成后续的 rebase操作：
git rebase --continue

5. push 新feature
当前分支：分支：feature_a，
git push 


---
其他：
* 如果想要放弃本次变基：git rebase --abort
* 如果是2个 feature分支，那建议还是



<br>**文档**：
https://mp.weixin.qq.com/s/-GM2_wklRyv-j1Go1BbEpw
