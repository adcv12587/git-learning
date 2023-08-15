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

### Git commands description
| Command | Description |
| ------ | ------ |
| git status | 查看本地端倉庫狀態 |
| git add    | 添加到暫存區 (untracked -> tracked) |
| git commit | 提交到本地端倉庫 |
| git log <br> git log --oneline | 查看本地端倉庫的提交歷史紀錄|
| git rm --cache <br> git restore --staged | 取消添加到暫存區 (tracked -> untracked) |




## Commands
| Target | Command |
| ------ | ------ |
| Hardware | cat /proc/cpuinfo |
| OS | lsb_release -a |

