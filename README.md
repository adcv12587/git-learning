# git-learning
## Hardware
- Raspberry Pi 4 Model B Rev 1.2


## OS
- Ubuntu 22.04.3 LTS


## Git GUI
- Github desktop (only for github) => 功能簡單, 但夠用
- Sourcetree => 功能強大  `[推薦]` &#x2705;
- GitKraken


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
git reset --hard _Commit_Hash_ // restore
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
| git status | 查看本地端倉庫詳細狀態 |
| git status -s | 只顯示本地端倉庫[文件狀態](#git-file-status) |
| git add _檔名_ | 添加到暫存區 (untracked -> tracked) |
| git commit | 提交到本地端倉庫 |
| git log <br> git log --oneline | 查看本地端倉庫的提交歷史紀錄|
| git log --graph --oneline --decorate --all | 圖形化分支狀態 |
| git rm --cache _檔名_ <br> git restore --staged _檔名_ | 取消添加到暫存區 (tracked -> untracked) |
| git ls-files | 列出暫存區目前的檔案清單 |
| git reflog | 列出所有git操作紀錄 |
| git reset (--mixed) _HEAD_/_Commit_Hash_  | 撤銷修改內容或是回退到某個版本, 資料狀態: 工作區(✓) 暫存區(✕)  [Default] |
| git reset --soft _HEAD_/_Commit_Hash_ | 撤銷修改內容或是回退到某個版本, 資料狀態: 工作區(✓) 暫存區(✓) |
| git reset --hard _HEAD_/_Commit_Hash_ | 撤銷修改內容或是回退到某個版本, 資料狀態: 工作區(✕) 暫存區(✕) |
| git diff _HEAD_ | 查看差異, 工作區與暫存區的差異 [Default] |
| git diff --cached <br> git diff --staged | 查看差異, 暫存區與repo的差異 |
| git rm _檔名_ | 刪除文件, 資料狀態: 工作區(✕) 暫存區(✕) |
| git rm --cached _檔名_ | 刪除文件, 資料狀態: 工作區(✓) 暫存區(✕) |
| 1. git remote add _遠端倉庫名稱_ _遠端倉庫地址_ <br> 2. git push -u _遠端倉庫名稱_ _分支名稱_ | 添加已存在的遠端倉庫 |
| git remote -v | 查看遠端倉庫 |
| git branch _new_branch_name_ | 創建新分支 |
| git branch -a | 查看分支清單 |
| git switch _branch_name_ | 切換分支 `[推薦]` &#x2705; |
| git checkout _branch_name_ | 切換分支 |
| git checkout -b _branch_name_ _commit_hash_ | 恢復分支到某一個狀態 |
| git merge _branch_name_ | 合併分支 (不會更動歷史紀錄) |
| git rebase _branch_name_ | 合併分支 (會更動歷史紀錄) <br> 1. 在main分支rebase dev分支, 則會將main分支的紀錄移至dev分支後 <br> 2. 在dev分支rebase main分支, 則會將dev分支的紀錄移至main分支後|
| git merge --abort | 取消合併分支 |
| git branch -d _branch_name_ | 刪除分支 (已合併) |
| git branch -D _branch_name_ | 刪除分支 (未合併) |
| git revert | **TBD** |
| git stash | **TBD** |
| git cherry-pick | **TBD** |

### Git file status
| Symbol | Definition |
| ------ | ------ |
| ?? | Untracked 未跟蹤 |
| M  | Modified 已修改|
| A  | Added 已添加暫存|
| D  | Deleted 已刪除|
| R  | Renamed 重命名|
| U  | Updated 已更新未合併|


### Git reset file status
|  | work directory | staging area |
| ------ | ------ | ------ |
| hard | &#x2716 | &#x2716 |
| soft | &#x2714 | &#x2714 |
| mixed | &#x2714 | &#x2716 |


## Commands
| Target | Command |
| ------ | ------ |
| Hardware | cat /proc/cpuinfo |
| OS | lsb_release -a |






