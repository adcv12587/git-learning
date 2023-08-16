# git-learning
## Hardware
- Raspberry Pi 4 Model B Rev 1.2


## OS
- Ubuntu 22.04.3 LTS


## Installation
Updated and install git
```sh
sudo apt update
sudo apt install git
```


## Configure git branch hints
1. edit ~/.bashrc and add below
```sh
# Git branch in prompt.
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
PS1="${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[31m\]\$(parse_git_branch)\[\033[00m\] $ "
```
2. restart env
```sh
source ~/.bashrc
```


## Git commands introduction
### Git configuration
```sh
git config --global user.name "lambert"
git config --global user.email "lambert@example.com"
git config --global credential.helper store // for saving username and password to avoid input per every time
```

### Check git configuration information
```sh
git config --global --list
```

### Recovery methods for git operation mistakes
```sh
git reflog               // show all action logs
git reset --hard $Commit_Hash // restore
git log --oneline        // check status
```

### .gitignore rules
Which files should be ignored?
1. 系統或者軟體自動生成的文件
2. 編譯產生的中間文件跟結果文件
3. 運行時生成的日誌文件、緩存文件、臨時文件
4. 包含有身分、密碼、密鑰等敏感資訊文件

### Common git commands
| Command | Description |
| ------ | ------ |
| git status | 查看本地端倉庫狀態 |
| git add $filename | 添加到暫存區 (untracked -> tracked) |
| git commit | 提交到本地端倉庫 |
| git log <br> git log --oneline | 查看本地端倉庫的提交歷史紀錄|
| git rm --cache $filename <br> git restore --staged $filename | 取消添加到暫存區 (tracked -> untracked) |
| git ls-files | 列出暫存區目前的檔案清單 |
| git reflog | 列出所有git操作紀錄 |
| git reset (--mixed) | 撤銷修改內容或是回退到某個版本, 資料狀態: 工作區(✓) 暫存區(✕)  [Default] |
| git reset --soft | 撤銷修改內容或是回退到某個版本, 資料狀態: 工作區(✓) 暫存區(✓) |
| git reset --hard | 撤銷修改內容或是回退到某個版本, 資料狀態: 工作區(✕) 暫存區(✕) |
| git diff HEAD | 查看差異, 工作區與暫存區的差異 [Default] |
| git diff --cached <br> git diff --staged | 查看差異, 暫存區與repo的差異 |
| git rm $filename | 刪除文件, 資料狀態: 工作區(✕) 暫存區(✕) |
| git rm --cached $filename | 刪除文件, 資料狀態: 工作區(✓) 暫存區(✕) |
| 1. git remote add $遠端倉庫名稱 $遠端倉庫地址 <br> 2. git push -u $遠端倉庫名稱 $分支名稱 | 添加已存在的遠端倉庫 |
| git remote -v | 查看遠端倉庫 |



## Commands
| Target | Command |
| ------ | ------ |
| Hardware | cat /proc/cpuinfo |
| OS | lsb_release -a |
