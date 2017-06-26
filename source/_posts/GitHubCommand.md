---
title: GitHubCommand
date: 2017-06-26 14:45:47
categories: GitHub
---
*在这记录一下GitHub的一些常用命令*
***
# Git Config
`git config --global user.name "cccy0"`
`git config --global user.email "cccy0@foxmail.com"`
`git remote add origin git@github.com:cccy0/cccy0.github.io.git`      这是我的远程库地址
`git remote set-url origin git@github.com:cccy0/cccy0.github.io.gi`   修改远程仓库地址

`git config --global alias.co checkout` 别名设置
`git config --global alias.c commit`
`git config --global alias.st status`
`git config --global alias.br branch`

`git config --global core.quotepath false` 显示中文名
# Git常用command
`git checkout  -- <file>`       抛弃工作区修改
`git checkout .`

`git add <file>`                文件修改提交暂存区
`git add .` 

`git rm <file>`                 从版本库中删除文件,同时删除本地文件
`git rm <file> --cached`        从版本库中删除文件，但不删除文件  
`git reset <file>`              从暂存区恢复到工作文件

`git reset .` 
`git reset --hard`              放弃上次提交后的所有本次修改  

`git commit <file>`             提交修改
`git commit .`
`git commit -m"*******"`        附加说明
`git commit -a add,rm,commit`   操作合并

`git log`
`git log <file>`                文件每次提交记录
`git log -p <file>`             查看每次详细修改内容
`git log -p -2`                 查看最近两次详细记录 
# Git分支管理
`git branch -r`                          查看远程分支
`git branch <new_branch>`                创建新的分支
`git branch -v`                          查看各个分支最后提交信息
`git branch --merged`                    查看已经被合并到当前分支的分支
`git branch --no-merged`                 查看尚未被合并到当前分支的分支
`git checkout <branch>`                  切换到某个分支
`git checkout -b <new_branch>`           创建新的分支，并且切换过去
`git checkout -b <new_branch> <branch>`  基于branch创建新的new_branch 
`git branch -d <branch>`                 删除某个分支
`git branch -D <branch>`                 强制删除(未合并时) 
`git merge <branch>`                     将branch分支合并到当前分支 

`git pull`                               抓取远程仓库所有分支更新并合并到本地
`git pull origin master`                 抓取远程主分支 "并" 和本地当前分支合并
`git merge origin/master`                将远程主分支合并到本地当前分支(仅合并)
`git push`                               push所有分支
`git push origin master`                 将本地主分支推到远程主分支
`git push -u origin master`              将本地主分支推到远程(如无远程主分支则创建，用于初始化远程仓库)

`git remote -v`                          查看远程服务器地址和仓库名称
`git remote show origin`                 查看远程服务器仓库状态
