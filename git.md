### git
三个区域：工作区、暂存区、git仓库
三种状态：modified已修改、staged已暂存、commited已提交
文件的4种状态：未跟踪、未修改、已修改、已暂存
全局配置文件目录：c:/用户/administrator/.gitconfig

$ git config --global user.name "zhk"

$ git config --global user.email "zhk@qq.com"

$ git config --list --global
core.editor="F:\Programs\Microsoft VS Code\bin\code" --wait
user.name=zhk
user.email=zhk@qq.com

$ git config user.email
zhk@qq.com

$ git config --help     打开帮助文档页面

$ git help config

$ git config -h         显示简单帮助提示


Administrator@DESKTOP-B8QTA0D MINGW64 /f/CloudSpace/BaiduSyncdisk/Study/3.git
$ git init
Initialized empty Git repository in F:/CloudSpace/BaiduSyncdisk/Study/3.git/.git
/

Administrator@DESKTOP-B8QTA0D MINGW64 /f/CloudSpace/BaiduSyncdisk/Study/3.git (master)
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        git.md

nothing added to commit but untracked files present (use "git add" to track)

Administrator@DESKTOP-B8QTA0D MINGW64 /f/CloudSpace/BaiduSyncdisk/Study/3.git (master)
$ git status -s
?? git.md   两个?表示未跟踪状态

修改了的文件如果没放入暂存区是红色的 modified，放入暂存区则是绿色的 M

git add filename // add 可以把未跟踪的新文件添加到暂存区，也可以把已跟踪并且修改了的文件添加到暂存区
git add .   // 将新增的和修改的一起加到暂存区

git reset HEAD file
git reset HEAD .    // 将所有文件从暂存区移除，上面是指定单个文件移除

git commit -m "comment" // 提交已暂存的文件
git commit -a -m "comment"  // 一般的流程是先把文件添加到暂存区再提交到仓库，加上 -a 则可以跳过添加到暂存区这环节，直接将跟踪（不包括未跟踪的）且修改了的文件提交到仓库

git checkout -- file  撤销对文件的修改

git rm -f file
git rm --cached file    // -f 是从工作区和仓库里都移除， -cached 是只从仓库中移除，移除之后还是需要提交

.gitignore 文件可以让 git 忽略某些符合条件的文件或文件夹，不会跟踪和记录它们
里面的格式规范：
\#开头 注释
/开头 不递归，当前目录下的文件或文件夹
/结尾 表示目录
!开头 取反，表示不忽略
另外还有glob匹配模式：*表示任意个字符，?[abc][0-9]和正则一样，**表示匹配任意中间目录，如dira/\*\*/dirz表示dira/dirb/dirz或dira/dirz或dira/dirb/dirc/dirz等都可以

git log
git log -3
git log -3 --pretty=oneline   // 在一行展示每次提交的更新记录
git log -3 --pretty=format:"%h | %an | %ar | %s"  // 一行展示且规范格式，%h 提交的简写哈希值 %an作者 %ar修订时间 %s提交说明。如 2fb267e | zhk | 23 hours ago | change git.md

git reset --hard id // 切换到某个版本
git reflog --pretty=oneline // 如果用 log，只会显示切换的那个版本和之前的版本历史，reflog 则能显示所有历史版本

GPL、MIT
开源的好处：使用者拥有更多的控制权、让学习更容易、更加安全

github远程仓库访问的：https和ssh
https: 
git remote add origin https://github.com/haikuosky/mypeoject.git  //远程创建
git push -u origin main