
<!-- TOC -->

- [git](#git)
    - [创建库或初始化库](#创建库或初始化库)
    - [记住密码](#记住密码)
    - [查看配置](#查看配置)
- [makedown](#makedown)
    - [插入图片](#插入图片)
    - [插入标题](#插入标题)
    - [插入空格](#插入空格)
    - [表格](#表格)
    - [超链接](#超链接)
- [vscode](#vscode)
    - [快捷键](#快捷键)
    - [html](#html)
        - [初始化创建html](#初始化创建html)
    - [python](#python)
        - [安装包的安装](#安装包的安装)

<!-- /TOC -->


# git
## 创建库或初始化库
创建一个空的Git仓库或重新初始化一个现有仓库。  
`git init`
## 记住密码
1. 设置记住密码（默认15分钟）：
`git config --global credential.helper cache`
2. 自己设置时间
`git config credential.helper 'cache --timeout=3600'`
注意：这样就设置一个小时之后失效  
3. 长期存储密码
`git config --global credential.helper store`  
增加远程地址的时候带上密码也是可以的。(推荐)  
4. 从仓库的config的里面修改url，后面加上密码
`http://yourname:password@git.oschina.net/name/project.git` 
补充：使用客户端也可以存储密码的。  
## 查看配置
使用`git config --list`查看已设配置

# makedown
## 插入图片
`![图书说明](/url)`   

## 插入标题
安装插件[makedown TOC]  使用方法，右键快捷菜单栏   

## 插入空格
- 插入一个空格 (non-breaking space)  
`&nbsp;`或 `&#160;`或`&#xA0;`   
- 插入两个空格 (en space)   
`&ensp;`或`&#8194;`或`&#x2002;`    
- 插入四个空格 (em space)   
`&emsp;`或`&#8195;` 或 `&#x2003;`    
- 插入细空格 (thin space)   
`&thinsp;` 或 `&#8201;` 或 `&#x2009;`    
**注意：不要漏掉分号。**
## 表格
```
| 左对齐标题 | 右对齐标题 | 居中对齐标题 |
| :------| ------: | :------: |
| 短文本 | 中等文本 | 稍微长一点的文本 |
| 稍微长一点的文本 | 短文本 | 中等文本 |
```
## 超链接
`[链接文字](链接网址 "标题")`    
# vscode
## 快捷键
1. 缩进快捷键  
选中文本；Ctrl  +  [      和   Ctrl  +  ]     实现文本的向左移动或者向右移动；
2. 代码对齐快捷键  
选中文本；Shift  +  Alt  + F     实现代码的对齐


## html
### 初始化创建html
在html文件里输入英文感叹号!，然后输入tab键，将自动生成标准的html代码。  

## python
### 安装包的安装
 使用镜像源:    
 `pip3 install -i https://pypi.tuna.tsinghua.edu.cn/simple 包名`   
