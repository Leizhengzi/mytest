Git使用说明

git help  -- git help a   查看帮助

git 全局配置项：
 
     git config --global user.name xx  --配置用户名
     git config --global user.email xx --配置邮箱 
     git config --unset --global user.name --删除用户名
     git config --list --显示配置列表
     
git 基本命令：

     git init --初始化版本库
     git add  --将文件添加到暂存区
     git commit -m 'xxxx' --将文件提交到本地版本库
     git diff --查看文件变更的内容  master..dev
     git mv --工作区的文件被添加到暂存区后，执行修改文件名
     git rm --删除暂存区的文件 --cached 本地保留文件  －f 同时删除本地文件
     git log --oneline 查看提交的次数
     git checkout --'xxx' --恢复刚才的操作，相当于回滚
     git revert HEAD --回撤上次提交的内容，回撤上两个版本＋^^, 回撤多个版本～n
     git reset HEAD^^ --mixed/--hard  --hard会影响工作区的内容
     git branch查看分支 ＋ 'xxx': 创建分支; -d 分支名字: 删除分支; －m 修改分支
     git checkout  + 分支的名称 --创建一个分支
     git merge 分支名字 --no-ff -m “说明”  no-ff 代表 no fastforword

bug 分支:

     git checkout -b “分支名字” 创建并切换分支
     git stash 封存文件;
     git stash pop 还原文件; 
     git stash list 显示封存列表; 
     git stash apply + 封存好的文件 // 不做要求

feature 分支：

github.com  远程平台：

     git remote add origin 远程仓库链接地址
     git push -u origin master 推动本地仓库内容到远程仓库
     git remote -v 显示远程仓库连接信息
     git remote remove name 移除远程仓库
     git remote rename 重命名远程连接仓库  相当于移除＋创建
     git fetch 更新远程分支

远程：git fork

别名：

     git config --global alias.别名    git 别名
     git config --get-regexp alias 查看别名列表
     git config --global --	unset alias.别名 取消别名远程：

本地搭建git服务器：

     git init --bare test.git

免密码登录:

     ssh-keygen -t rsa
     ssh-add ~/.ssh/文件名
     ssh -T git@github.com

本地服务器:

     创建用户：useradd git
     进入git目录
     mkdir .ssh
     设置权限：chown -R git:git .ssh
     进入.ssh文件下
     touch authorized_keys

初始化git仓库

回到客户端：

     ssh-keygen -t rss
     将pub文件内容copy 到 authorized_keys中
     chmod 600 authorized_keys   在改一下所属者
     chmod 700 .ssh
     .gitignore  忽略不需要的文件提交
全局忽略：

     touch ~/.gitignore_global
     git config --global core.excludesfile ~/.gitignore_global
     
目前开发机上的git别名系统：
git alias:

     gst <====> git status
     gci <====> git commit -a -m
     gco <====> git checkout
     gpull <====> git pull
     gpush <====> git push
     
     
开发过程中如同步时发生冲突，解决方法：
   
     grep "<<<<" -nr * 找到冲突文件的冲突位置，然后根据实际情况删去不需要的
     然后再次提交同步合并，结束后gpush推送即可。
     
git查看提交日志，显现详细修改内容，如被误删的内容，可从这里找到复制过去即可：
  
     git log -p --显示提交日志，显示详细信息






            
            
