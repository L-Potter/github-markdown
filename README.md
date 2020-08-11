# github-markdown

git checkout 切換分支

git add <file> 添加某個文件到本次提交

git commit 提交本次commit

git commit -a 提交更新

git push origin [branch-name] 提交更新到遠程分支

git fetch orgin 獲取所有遠程分支的更新

git branch --track <new><remote> 用來第一次創建本地分支提交代碼

git rebase -i 在本地進行commit的合併 i 之後加相應的參數可以進行到某個時間點合併

git rebase -i~<num>使用d來刪除某個commit

可以通過git reset 和 git checkout 來修改代碼文件的工作區域

git remote add 用來添加不同的remote, 通常來說是

git fetch origin, git merge origin/another-branch 用來在更新本地分支(合併遠程分支)

git fetch origin, git rebase origin/another-branch 功能同上

當更新本地分支出現:First, rewinding head to replay your work on top of it...,並且要強制更新本地分支則 git fetch origin, git reset --hard origin/<branch>

當本地分支更新完成之後, 需要手動git push origin/<branch> 更新跟踪的遠程分支

git branch branch_name --set-upstream-to origin/branch_name git 切換跟踪的遠程分支

當提交merge request時,出現了衝突則git fetch git rebase origin/<branch>來解決衝突

git diff 用來查看當前改變和HEAD的區別, git diff HEAD^ HEAD查看上一次提交和當前HEAD的區別, git diff a b, a 早期提交, b後來提交

添加.gitignore文件echo '.idea' >> .gitignore, git rm -r --cached .idea, git add .gitignore

git config --local 配置當前項目的配置, git config --global配置全局配置

git reset HEAD@{3} 使用通常為git reset HEAD^之後查看git reflog來返回上一次提交

git reset --soft HEAD~1不提交上一次的commit

git revert <commit> undo the specific commit

git commit -a -amend 提交修改至最後一次commit中

git rm --cached <filename> 從git中刪除, 並不從文件系統中刪除

git branch -m <new-branch-name>: 重新命名一個新的分支的名字

git push origin :old-branch: 刪除一個遠程分支

git push origin :old-name new-name: 刪除遠程分支, 並push新分支名字

git branch -d <branch name>: 刪除本地分支

git branch -D <branch name>: 強制刪除本地分支

git branch -r: 列出所有遠程分支

git cherry-pick <commit A>將其他commit提取到本地分支上面

git cherry-pick <commit A>..<commit B>將A到B的commit提取到本地分支上面, 注意A比B更早的提交

git cherry-pick <commit A>..<commit B>將包含A到B的commit提取到本地分支上面

git cherry-pick是等同與一次提交, 如果想要undo某次cherry-pick, 使用git reset --hard <commit>

git checkout <commit A> -- <file> 去掉某次提交的文件

git reset HEAD <file>將某次提交的文件，放到暫存區

git checkout -- <file>恢復修改之前的文件

git 不提交某次更新：

* git reset --soft HEAD~1 軟reset到某個點
* git reset <file>將具體某個file從已提交的去除
* git commit -c ORIG_HEAD 使用原來的ORIG_HEAD的commit message信息
* git checkout -- <file>恢復對該文件的改變， 即恢復到之前一個commit版本
* git HEAD 指向當前的commit

git ORIG_HEAD 為在進行了一次危險的操作之後， HEAD已經改，ORIG_HEAD為前一個狀態的HEAD通常用來恢復狀態

git tag: 列出所有的tag

git tag <tagname>

git tag --list "meg*" 列出以meg開頭的tag

git checkout tags/<tagname> -b <branchname>: checkout 到<tagname> tag上

git push origin <tagname>: 將某個tag，push到遠程

強制merge，dev 分支overwrite master分支，結果即為master分支的內容變成了dev的內容。 （使用了ours merge strategy ）

* git checkout dev
* git merge -s ours master
* git checkout master
* git merge dev
