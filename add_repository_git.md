## Mac下使用GitHub仓库

### 安装Git

* 查看是否安装git
```
查看是否安装git
git --version
```

* 通过homebrew安装Git
```
brew -v
or
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### 创建ssh key 配置git

* 设置git配置
```
git config --global user.name "Kol"
git config --global user.email "xxx@qq.com"
```

* 通过终端命令创建ssh key
```
ssh-keygen -t rsa -C "xxx@qq.com"
```

* 添加key至github
```
Setting - SSH and GPG keys - SSH keys - New SSH key
```

* 添加host
```
vim ~/.ssh/config
Host github.com
    User zengzhiqian
    Hostname github.com
    IdentityFile ~/.ssh/github
```

* 测试链接
```
ssh -i /Users/zengzhiqian/.ssh/github -T git@github.com

Hi Kol-zengzhiqian! You've successfully authenticated, but GitHub does not provide shell access.

测试成功
```

### 链接github仓库

* 创建仓库

* 克隆仓库到本地
```
cd $directory
git clone git@github.com:Kol-zengzhiqian/mark_saas.git
```

* 上传代码至 GitHub
```
# 添加文件 
git add $directory/$filename

# 添加修改内容注释
git commit -m "first commit"

# git push
```

* 下载代码
```
git pull
```

### 简单报错处理

* Updates were rejected because the remote contains work that you do
```
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'git@github.com:Kol-zengzhiqian/mark_saas.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
看报错原因是我在远程做了改动

解决方案：
执行 git pull 远程分支名 本地分支名
再执行git push命令，没有报错