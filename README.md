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
### Git 誤操作的恢復方法
```sh
git reflog               // show all action logs
git reset --hard $HashID // restore
git log --oneline        // check status
```
1. git reflog
2. 


### Git commands description
| Command | Description |
| ------ | ------ |
| git status | 查看本地端倉庫狀態 |
| git add "$filename" | 添加到暫存區 (untracked -> tracked) |
| git commit | 提交到本地端倉庫 |
| git log <br> git log --oneline | 查看本地端倉庫的提交歷史紀錄|
| git rm --cache "$filename" <br> git restore --staged "$filename" | 取消添加到暫存區 (tracked -> untracked) |
| git ls-files | 列出暫存區目前的檔案清單 |
| git reflog | 列出所有git操作紀錄 |
| git reset --mixed | 撤銷修改內容或是回退到某個版本, 資料狀態: 工作區(✓) 暫存區(✕) |
| git reset --soft | 撤銷修改內容或是回退到某個版本,  資料狀態: 工作區(✓) 暫存區(✓) |
| git reset --hard | 撤銷修改內容或是回退到某個版本,  資料狀態: 工作區(✕) 暫存區(✕) |






## Commands
| Target | Command |
| ------ | ------ |
| Hardware | cat /proc/cpuinfo |
| OS | lsb_release -a |

