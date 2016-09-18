---
title: hexo使用
date: 2016-06-29 10:43:07
tags:
---
### Hexo使用
- 注意hexo项目需要2个分支(master,hexo)  
先在github新建一个xxx.github.io的项目，开启github page功能，git拉取项目一个存放hexo生成的页面资源，另一个存放hexo源文件以便在其他电脑写文章

- 工具git，node  
```bash
#git
sudo apt-get install git
#使用
ssh-keygen -t rsa -b 4096 -C 邮箱
git config --global user.email 邮箱
git config --global user.name 名字
#找key文件，添加到github
cd ~/.ssh

#node
curl https://raw.github.com/creationix/nvm/master/install.sh | sh
或
wget -qO- https://raw.github.com/creationix/nvm/master/install.sh | sh
nvm install 4
```

- 使用
```bash
#全局安装hexo
npm install hexo -g

#拉取仓库
git clone 仓库地址

#切换仓库目录
cd 仓库目录名

#hexo初始化
hexo init

#git初始化，因为hexo init初始化会使git失效，需要重新关联仓库
git init
git remote add orign 仓库地址

#安装依赖
npm install

#安装一个插件，以便部署到github
npm install hexo-deployer-git --save

#先切换保存hexo源文件的分支提交源文件，以便日后在其他电脑上写文章
git checkout hexo
git add .
git commit -m '提交hexo源文件'
git push origin hexo

#切回master分支，可以开始写文章
git checkout master
hexo new 文章名

#生成静态资源，查看效果，提交文章
hexo generate
hexo server
hexo deploy #需要安装hexo-deployer-git
```
