# Git的命令详解及相关知识
- ## Git Cheat Sheet翻译
  以下内容为Git Cheat Sheet的中文翻译及自己新整理的一些命令，大部分来自于网友的分享，这里做一个汇总。  
- #### 配置
  **列出当前配置:**
  `$ git config --list`  

  **列出repository配置:** 
  `$ git config --local --list` 

  **列出全局配置:**
  `$ git config --global --list`

  **列出系统配置:**
  `$ git config --system --list`

  **设置用户名:**
  `$ git config --global user.name`  

  **设置用户邮箱:**
  `$ git config --global user.email`   

  **设置git命令输出为彩色:**
  `$ git config --global color.ui auto`  

  **设置git使用的文本编辑器:**
  `$ git config --global core.editor vi`  

- #### 创建
  **复制一个已创建的仓库:** `$ git clone git@github.com:<username>/learngit.git`  

  **创建一个新的本地仓库:** ``$ git init``

- #### 本地修改
  **显示工作路径下已修改的文件:**
  `$ git status`

  **显示与上次提交版本的不同:** `$ git diff`    

  **把对某个文件的修改添加到下次提交中:** `$ git add -p <file>`  

  **把当前所有修改添加到下次提交中:**  `$ git add .`  

  **提交本地的所有修改:** 
  `$ git commit -a`  

  **提交之前已标记的修改:** 
  `$ git commit -m "<commit message>"`

  **修改上次提交(请勿修改已发布的提交记录!):**`$ git commit --amend`  

- #### 提交历史
  **从最新提交开始，显示所有的提交记录（显示hash， 作者信息等信息）:** `$ git log`

  **显示所有提交（仅显示提交的hash和message）:**`$ git log --oneline`  

  **显示某个用户的所有提交:**`$ git log --author="username"`  

  **显示某个文件的所有修改:**`$ git log -p <file>`  

  **谁，在什么时间，修改了文件的什么内容:**`$ git blame <file>`  

  **显示reflog:**`$ git reflog show`

  **删除reflog:**`$ git reflog delete`

- #### 分支与标签
  **列出所有的分支:**`git brach`

  **基于当前分支创建新分支:**`$ git branch <branch name>`

  **切换分支:**`git checkout <branch name>`

  **基于当前分支创建并切换到新分支:**`$ git checkout -b <branch name>`

  **基于远程分支创建新的可追溯的分支:**`$ git branch --track <new-branch> <remote-branch>`  

  **删除本地分支:**`$ git branch -d <branch>`  

  **强制删除一个本地分支(将会丢失未合并的修改！):**`$ git branch -D <branch>`

  **给当前版本打标签:**`$ git tag <tag-name>`

- #### 更新与发布
  **列出当前配置的远程端:**`$ git remote -v`

  **显示远程端的信息:**`$ git remote show <remote>`

  **添加新的远程端:**`$ git remote add <remote> <url>`  

  **下载远程端版本，但不合并到HEAD中:**`$ git fetch <remote>`







> ### 在 .gitconfig 文件中定义 hist 别名
> `.gitconfig`文件的路径在`C:\Users\maccura`。
- [git revert HEAD 的详解](https://www.cnblogs.com/pansidong/p/8716226.html)

- [Git Cheat Sheet 中文版](https://blog.csdn.net/github_37515447/article/details/56840610)
- [Git Cheat Sheet](https://www.jianshu.com/p/c4ace9202a34)