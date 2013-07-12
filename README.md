Test
====

測試git

設定你的 git


git config --global user.name "Your Name"
git config --global user.email "your@email.com"
git config --global alias.st status
git config --global color.ui true
git config --global core.editor vi
git init
git config --add core.quotepath false
git Alias 功能

使用終端機來操作 git 常會讓人覺得一直打指令很繁瑣，因此 git 也有提供 alias 的功能，例如你可以將 git status 縮寫為 git st，git checkout 縮寫為 git co 等，你只要這樣設定：

git config --global alias.st status

git 預設輸出是沒有顏色的，我們可以讓他在輸出時加上顏色讓我們更容易閱讀：

git config --global color.ui true

Git 顯示中文檔名

git 的一些指令 (如 status, diff) 在顯示非 ASCII 檔名有點問題, 會顯示成亂碼！ 有兩個方法解決

git config --add core.quotepath false
修改 ~/.gitconfig，找到 [core] 的位置後面，加上

[core]
    quotepath = false
如果還有問題，提醒在 bash 設定 export LANG=zh_TW.UTF-8

After doing this, you may fix the identity used for this commit with:

git commit --amend --reset-author
Git的基本功(status, .gitignore, add, commit, log)

git status

在一個 git 的 Repository 中你可以輸入git status來檢查目前 Git 的狀態

git status

設定不被追蹤的檔案(Untracked files) .gitignore


vi .gitignore
*.swp
*~
設定不被追蹤的檔案(Untracked files) .gitignore

Latex 範例


*.swp
*~
.DS_Store
*~
*.lo?
*.toc
*.fdb*
*.aux
*.bbl
*.out
新增檔案(tracked files)，進入 stage 狀態

git add file.xxx

Create a new repository on the command line

當你建立新的 repository 時，會自動提示下列的指令


touch README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/yourname/xxx.git
git remote add origin git@github.com:petani/ubuntu.git   # 使用 ssh key
git push -u origin master
Push an existing repository from the command line (git push)


git remote add origin https://github.com/petani/vim.git
git push -u origin master
你有兩種方法查看歷史紀錄

git log
git show HEAD 這個指令能顯示更詳細的變更內容
你可以使用 git blame 來查詢，誰把程式改到攔掉了！

git blame xxx.c
git log -- xxx.c
復原檔案, 這個方法很常用，但也很容易忽略。

git checkout 檔名 回復上一次 commit 的內容
get reset HEAD 檔名:
團隊合作篇

要和別人協同工作，最重要的幾個關鍵如下:

先在 github 上 fork repositary
git clone xxxxx *
Github update fork

首先 fork leader 到自己的 github 中。
git clone git@github.com:leader/xxx.git
for write and read access
注意事項

由 project/.git/config 可知: (若有更多, 亦可由此得知)

origin(remote) 是 Repository 的版本
master(branch) 是 local 端, 正在修改的版本
平常沒事不要去動到 origin, 如果動到, 可用 git reset --hard 回覆到沒修改的狀態.

另一種受歡迎的版本控制系統

bitbucket.org
Generating SSH Keys

如果還沒安裝 xclip 請先安裝
apt-get install xclip *ssh-keygen
xclip -sel clip < ~/.ssh/your.pub
參考資料:

寫給大家的 Git 教學 第三版，2012
Git 教學(1) : Git 的基本使用
Git 教學(2)：Git Branch 的操作與基本工作流程
[Git] 從 Git 開始進入版本控制的世界 (Git in a Nutshell)
Why Git 為什麼要版本控制？為什麼要用 Git？
The four buckets — how Git considers content
Creating Project Pages manually
