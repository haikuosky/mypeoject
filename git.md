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
