---
title: Github & hexo for free blogs
date: 2021-01-03 22:13:25
tags: 
- Blog
- hexo 
- bash
- vscode
- git
categories: 
- [Tools, Write]
---

# References
1. [Hexo官网](https://hexo.io/zh-cn/docs/)
2. [主题Next官网](http://theme-next.iissnan.com/theme-settings.html)
3. [博客园文章，主要是环境准备](https://www.cnblogs.com/jie-fang/p/13445913.html)

# Github & Hexo 建立博客
## Comments
- 优点：方便免费，一次准备好环境后，只需要进行写作上传即可。
- 缺点：暂时还没有被搜索引擎抓取？（用来回顾学的东西）

## Rough Flow
### 环境准备
- Github
- Git bash
  - 官网下载，安装的时候注意各种选项是否勾选，细看（虽然不影响结果，使用舒适度上有区别）
  - 在vscode中设置terminal为bash，可以使用shell命令。
- node.js
  - 官网下载及其慢，找到版本后，[淘宝镜像](https://developer.aliyun.com/mirror/NPM?from=tnpm)
  - `npm -version` 测试
- Hexo
  - [官网中文安装教程](https://hexo.io/zh-cn/docs/), 安装`npm install -g hexo-cli`。
  - `npm install hexo-deploy-git --save`，防止depoly出现问题。
- Next theme(在后面安装)


### 初次配置(Windows下使用vscode bash terminal/git bash，流程和Linux下一样)
1. github操作添加ssh-key，新建一个`${MyAccountName}.github.io`的repo。
2. 本地新建一个文件夹，方便同步建在OneDrive。
  - `mkdir -p ~/OnDrive/StefanChaos.github.io`
3. 初始化hexo
  - `cd ~/OnDrive/StefanChaos.github.io`
  - `hexo init`
  - `git clone https://github.com/iissnan/hexo-theme-next themes/next` 安装next主题，并在`_config.yaml`中修改`theme: next`。
4. 个性化功能
  - `code ./_config.yaml`修改title等，[Hexo官网](https://hexo.io/zh-cn/docs/)。
  - `code ./themes/next/_config.yaml`修改排版，我改了codeblock/menu/search_local[主题Next官网](http://theme-next.iissnan.com/theme-settings.html)。
5. 配置tags & categories
  - `hexo new page tags/categories`, 打开`source/tags/*.md`加入。根据两次安装分别选择对应的type写入。
  ```markdown
  type: tags
  # type: categories
  comments: false
  ```
6. 远程部署地址(重要)
```yaml
# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
  type: 'git'
  repo: 'https://github.com/StefanChaos/StefanChaos.github.io'
  branch: 'master'

## for local search
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
```


### 本地预览
`hexo server`会在`http://localhost:4000`上生成网页预览。

### 上传到远端
1. `hexo generate`
2. `hexo deploy`

### 日常使用流程
1. `hexo new "xxxxxxx"`
2. `hexo server`预览效果
3. `hexo generate`
4. `hexo deploy`上传到远端

<!-- more -->