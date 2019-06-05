## git 命令操作总结

### 1.安装git

* linux(Ubuntu) : sudo apt-get intall git

  > 终端输入git 如果有提示证明安装成功

* window版本===》git软件工具—-安装
* Mac Os—-terimal (自带终端) 第三方的终端工具 iterm2

### 2.git简介

* git ——分布式的版本控制工具

  ```
  现代化的代码版本控制工具 git  svn
  
  作用：对你的代码/项目的版本进行管理 （版本的更新 历史记录  回滚   删除的文件    多人协作  
  
  gitlab  公司内部服务器上搭建的版本控制系统 （git）
  
  github:全球级别的社交网站（git版本控制系统+程序猿交友平台 互相分享和学习对方代码）
  号称 全球最大的基友平台
  
  很多全世界范围优秀的框架和库 都在github有 官方存储的仓库
  开源：github是一个网站 （git）
  开源的生态系统：Android  
  
  git svn 是两种不同的代码版本控制方式
  git:分布式的版本控制系统
  svn：集中式的版本控制系统
  ```

  

### 2.git单人操作

* 2.1 创建空的git仓库: git init

  > 提示: git仓库和项目的根路径在一起,用来管理项目

* 2.2 配置git提交的用户名,邮箱

  例如: git config user.name 'zhangsan'

  &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; git config user.email '111@qq.com'

  > 如果没有配置,默认使用的: home/.gitconfig  根目录下的用户信息

* 2.3 查看文件状态: git status

  > 红色: 表示新建文件, 或者新修改了文件,目前位于工作区中
  >
  > 绿色: 表示文件在暂存区

* 2.4将工作区代码, 添加到暂存区(工作区-->暂存区)

* 例如: git add .  

   &nbsp; &nbsp; &nbsp; git add xxx.py

  > 点表示添加所有变动,  xxx.py表示指定文件

* 2.5将工作区代码,添加到仓库区(工作区—>仓库区)

* 例如: git commit -m '注释'

* 2.6将工作区,直接添加到仓库区(工作区-->暂存区—>仓库区)

* 例如: git commit -am '注释信息'

* 2.7查看版本历史

  例如: git log 查看版本的详细信息

   &nbsp; &nbsp; &nbsp;  git reflog  查看版本的大致信息

  > log查看详细信息, reflog查看简要信息

* 2.8回退版本

  例如: git reset --hard HEAD

  或者: git reset --hard 版本号

  > HEAD表示当前最新版本
  >
  > HEAD^表示当前最新版本的,  上一个版本
  >
  > HEAD^^表示当前最新版本的, 前两个版本, 依次类推
  >
  > HEAD~1 表示当前最新版本的,  上一个版本
  >
  > HEAD~2 表示当前最新版本的, 前两个版本, 依次类推

* 2.9撤销工作区,暂存区修改

  撤销工作区:  git checkout 文件名

  撤销暂存区: 

   &nbsp; &nbsp; &nbsp;  &nbsp; &nbsp; &nbsp;  &nbsp; &nbsp; &nbsp; git checkout HEAD 文件名 (暂存区-工作区)

   &nbsp; &nbsp; &nbsp;  &nbsp; &nbsp; &nbsp;  &nbsp; &nbsp; &nbsp; git checkout 文件名

  > 仓库区代码不能撤销

* 2.10 版本对比

  例如: git diff HEAD HEAD^ -- xxx.py

  > HEAD表示当前版本,   HEAD^表示上个版本, xxx.py对比的文件

* 2.11误删除文件,恢复

  格式1: rm 文件名

  恢复1: git checkout -- 文件名

  格式2: git rm 文件名

  恢复2: git reset --hard HEAD^

### 3.git多人操作

* 3.1 clone项目到本地

  例如: git clone 项目地址

* 3.2 推送项目到远程仓库

  例如: git push

  > 第一次推送会提示输入账号, 密码

* 3.3 配置是否输入登陆密码信息

  > git config --global  credential.helper cache 十五分钟有效期
  >
  > git config  credential.helper 'cache --timeout==3600' 一个小时有效期
  >
  > git config --global credential.helper store 长期有效

* 3.4 拉取远程最新代码到本地

  例如: git pull

### 4.标签

* 4.1 设置本地标签

  例如: git tag -a  标签名 -m '标签描述'

* 4.2 推送本地标签到远程

  例如: git push origin 标签名

* 4.3 删除本地标签

  例如: git tag -d 标签名

* 4.4 删除远程标签

  例如: git push origin --delete tag 标签名

### 5.分支

* 5.1查看当前分支

  例如: git branch

* 5.2创建本地分支,并切换到指定分支

  例如: git checkout -b 分支名

* 5.3推送本地分支,到远程

  例如: git push -u origin 分支名

* 5.4切换分支

  例如: git checkout master / dev

  > 切换到主分支,或者是其他分支
  >
  > 其他用户第一次pull代码后,切换切换后才能使用git branch查看

* 5.5合并子分支到主分支

  例如: git merge 分支

  > 需要在master分支下操作改命令

  