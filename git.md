# git的使用 #
## 让git对一个目录进行版本控制 ##
1. 进入要管理的目录
2. 执行初始化命令 `git init`
3. 查看目录下的文件状态 `git status`
    - 红色:新增加的文件或修改过的文件
    - 绿色:已经管理的文件
4. 管理文件
    - 添加指定文件 `git add 文件名` 
    - 添加当前目录下未管理或修改过的文件 `git add .` 
5. 个人信息配置:用户名和邮箱(第一次安装git时配置):
    ```	
    git config --global user.email "you@email.com"
    git config --global user.name "youName"
    ```
6. 生成版本
   `git commit -m '描述信息'`

## git三大区域 ##


- 工作区
  - 已管理文件
  - 新增/修改的文件通过`git add .`命令添加到暂存区
- 暂存区
  - 通过`git commit -m '描述信息'`命令将暂存区文件添加到工作区已管理文件
- 版本库 
    - 回滚到之前的版本
        ```
        git log 
        git reset --hard 版本号
        ```
    - 回滚到之后的版本
        ```
        git reflog
        git reset --hard 版本号
        ```


## git分支 ##

1. 查看分支 
  `git branch`
2. 创建分支
  `git branch 分支名称`
3. 切换分支
 `git checkout 分支名称`
4. 合并分支
 `git merge 要合并的分支`
5. 删除分支
 `git branch -d 分支名称`


##  上传github  ##

1. 给远程仓库起个别名
 `git remote add 别名 远程仓库地址
`
2. 向远程仓库推送代码
 `git push -u 别名 分支名`

3. 拉取远程仓库代码
    - 第一次拉取
        ` git clone 远程仓库地址`
    - 其他情况
        `git pull 别名 远程仓库名`
    - git pull 等于
      ```
        git fetch origin dev 把代码拉到版本库
        git merge origin/dev 把版本库的代码合并到工作区
        ```

 
##  git rebase  ##
1. 多个记录整合成一个记录 
    ` git rebase -i HEAD~合并记录条数`
2. git 查看日志
    ```
    git log 
    git log --graph
    git log --graph --pretty=format:"%h %s" *h 表示哈希值 s表示提交记录
    ```
3. 使用rebase合并分支
    1. 切回要合并的分支 
    `git checkout 要合并的分支`
    2. 执行命令 
    `git rebase master`
    3. 切回master执行命令
    `git merge 要合并的分支`
4. 解决分叉的产生
    ```
    git fetch 别名 分支名
    git rebase 别名/分支名
    ```
5. gitrebase 冲突问题
 1. 解决冲突
 2. 执行
    `git rebase --continue`
 

##  beyond compare ##
- 通过配置文件.gitconfig 配置beyond compare
  ```
    #使用beyond compare 来查看文件差异
    [diff]
    tool = bc4
    [difftool "bc4"]
    cmd = "\"C:/Program Files/Beyond Compare 4/BCompare.exe\" \"$REMOTE\" \"$LOCAL\""   
    [merge]
    tool = bc4
    [mergetool]
    promt = false
    [mergetool "bc4"]
    cmd = "\"C:/Program Files/Beyond Compare 4/BCompare.exe\" \"$REMOTE\" \"$LOCAL\" \"$BASE\" \"$MERGED\" "
    ``` 
 - 不保留原文件
   `git config --local mergetool.keepBackup false` 

##  tag ##
1. 创建tag
  `git tag -a 标签 -m '描述信息'`
2. 推送远端
   `git push 别名 --tags`