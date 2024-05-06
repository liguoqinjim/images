# 

|文件|简介|说明|
|---|---|---|
|script001.sh|从nas复制图片 |在m1上运行，而且是在finder里面连接服务器之后才能用 |

## 只保留最新的commit，以减小仓库大小
1. `git checkout --orphan new-main`
2. `git commit -m "Initial commit"`
3. `git branch -M new-main main`
4. `git push -f origin main`

## 删除github上所有除了main的分支
有的action会自动创建分支，也占用空间，定时删除。
1. `git fetch --prune origin '+refs/heads/*:refs/remotes/origin/*'`，更新远程分支列表
2. `git push origin --delete $(git branch -r | grep -v "main" | sed 's/origin\///')`，删除所有除了main的分支