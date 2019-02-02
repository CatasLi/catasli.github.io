---
title: VS Code实现MarkDown同步预览
date: 2019-01-12 03:18:31
tags: 笔记
---
![AlterText](/images/logo.png)

基本方法如下

<kbd>command</kbd>+<kbd>shift</kbd>+<kbd>p</kbd>呼出命令行，键入“markdown”后在命令列表中选择
```bash
Markdown: Open Preview to the side
```
亦可直接使用快捷键<kbd>command</kbd>+<kbd>k</kbd> <kbd>V</kbd>实现（空格代表先松了之前的按键再按下一个按键）

## Tips
插入图片
```
![altertext](image_path)
```

图片可以直接存在`/images`下，但也可以通过将`config.yml`中的`post_asset_folder`设置为`true`，即可在新建post时在`/source/_post`下生成同名的文件夹供存放资源文件。

### 语法参考网址
- [常用的MarkDown语法](https://laravel-china.org/topics/621/you-will-be-able-to-master-these-markdown-grammars)
- [Hexo博客搭建之在文章中插入图片](https://yanyinhong.github.io/2017/05/02/How-to-insert-image-in-hexo-post/)