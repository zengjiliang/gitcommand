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
  - `git commit -m '描述信息'`

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

