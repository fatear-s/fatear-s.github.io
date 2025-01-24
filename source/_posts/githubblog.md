---
title: githubblog
date: 2024-11-10 22:10:38
tags:
---

# github blog pages error&solve

## get github pages

url:https://pages.github.com/

## nodes.js、hexo、主题

https://gitcode.csdn.net/65aa2e27b8e5f01e1e44c4da.html?dp_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6NDE3NDY2OSwiZXhwIjoxNzMxNzU5OTczLCJpYXQiOjE3MzExNTUxNzMsInVzZXJuYW1lIjoicXFfNDU5NDE4NjYifQ.r6fm4uOpnxdFaKUjo6FtxG7PEAbyWyxLKbWn3FZHoVM&spm=1001.2101.3001.6650.4&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7Ebaidujs_baidulandingword%7Eactivity-4-119089190-blog-142594777.235%5Ev43%5Epc_blog_bottom_relevance_base3&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7Ebaidujs_baidulandingword%7Eactivity-4-119089190-blog-142594777.235%5Ev43%5Epc_blog_bottom_relevance_base3&utm_relevant_index=9

## git 问题

### 添加SSH

```bash
ssh-keygen -t rsa -C "@qq.com"
# 将SSH key 添加到 ssh-agent
ssh-add id_rsa
#如果出现“Could not open a connection to your authentication agent.”的错误
eval "$(ssh-agent -s)"
ssh-add id_rsa
#验证key
ssh -T git@github.com 
```

将SSH key 添加到你的GitHub账户

![img](/images/githubblog1.png)

链接

https://blog.csdn.net/m0_69057918/article/details/132139286

### 更换分支

```bash
git pull --rebase origin main
```

链接

https://www.bilibili.com/opus/464126252045553313

### 提交代码

```bash
git init
git add .
git commit -m "blog"
git remote add origin git@.com
git push origin main/git push -u origin main
```

链接

https://zhuanlan.zhihu.com/p/675458343

### 代码安全问题

 **error: GH013: Repository rule violations found for**

**问题描述：**

代码中包含明文密码等信息，会拒绝push

**解决方案：**

在push之后，后再错误信息中包含url(remove secret from commit...)访问url可以给当前push添加许可

![image-20241111194057209](/images/githubblog2.png)

链接https://blog.51cto.com/u_12763213/10979913

### git connext 问题

fatal: unable to access 'http://github.com/...':
Failed to connect to github.com port 443 after ... ms: Couldn't connect to server

解决方法：

手动配置代理与系统代理一致

```bash
git config --global http.proxy http://127.0.0.1:7890
git config --global https.proxy http://127.0.0.1:7890
```

### 下载hexo 提交工具连接问题

需要关闭系统代理或者设置系统代理
