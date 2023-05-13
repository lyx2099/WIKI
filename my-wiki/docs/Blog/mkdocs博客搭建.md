

## 1.安装 mkdocs
```python
pip install mkdocs
```



## 2.创建项目

新建一个文件夹，例如我的是 `WIKI` 。在 `WIKI` 文件夹下新建一个项目,比如 `my-wiki`。
```python
mkdocs new 项目名
mkdocs new my-wiki
```



## 3.文档预览

```shell
cd wiki
mkdocs serve
```



## 4.更换主题

```python
pip install mkdocs-material mkdocs-windmill
```
在 mkdocs.yml 里进行配置
```yml
theme:
  name: 'material'
```



## 5.进行 mkdocs.yml 配置

```yml
site_name: lyx
site_description: python selenium 数据分析
site_author: lyx
copyright: Copyright &copy; 2023 - 2099
site_url: https://lyx2099.github.io/WIKI
repo_url: https://github.com/lyx2099/WIKI
repo_name: mkdocs
edit_uri: ""

# 主题配置
theme:
  name: material
  language: en
  search_index_only: true
  # 调色板
  palette:
    - media: "(prefers-color-scheme)"
      toggle:
        icon: material/brightness-auto
        name: Switch to light mode

    # Palette toggle for light mode
    - media: "(prefers-color-scheme: light)"
      scheme: default
      toggle:
        icon: material/brightness-7
        name: Switch to dark mode

    # Palette toggle for dark mode
    - media: "(prefers-color-scheme: dark)"
      scheme: slate
      toggle:
        icon: material/brightness-4
        name: Switch to system preference

  features:
    #- navigation.instant # 点击内部链接时，不用全部刷新页面
    - navigation.tracking # 在url中使用标题定位锚点
    - navigation.tabs # 顶部显示导航顶层nav（也就是第一个节点）
    # - navigation.tabs.sticky # 滚动是隐藏顶部nav，需要配合navigation.tabs使用
    # - navigation.sections # nav节点缩进
    - navigation.expand # 不折叠左侧nav节点
    - navigation.indexes # 指定节点index pages ，跟instant不兼容
    # - toc.integrate # 右侧生产目录
    - toc.integrate #导航集成
    - toc.follow # 侧边栏自动滚动
    - navigation.top # 一键回顶部
    - header.autohide
    - search.share # 搜索分享
    - search.suggest # 搜索建议
    - search.highlight #搜索高亮
    - navigation.instant
    - navigation.path

plugins:
  - search:
      jieba_dict: user_dict.txt

# 图标
icon:
  admonition:
    note: octicons/tag-16
    abstract: octicons/checklist-16
    info: octicons/info-16
    tip: octicons/squirrel-16
    success: octicons/check-16
    question: octicons/question-16
    warning: octicons/alert-16
    failure: octicons/x-circle-16
    danger: octicons/zap-16
    bug: octicons/bug-16
    example: octicons/beaker-16
    quote: octicons/quote-16

# 扩展
markdown_extensions:
  - admonition
  - pymdownx.details
  - pymdownx.superfences
  - abbr
  - pymdownx.snippets
  - def_list
  - tables
  - pymdownx.tasklist:
      custom_checkbox: true
      # auto_title: true  # 显示编程语言名称
  - attr_list
  - md_in_html
  - meta
  - pymdownx.highlight:
      anchor_linenums: true
  - pymdownx.inlinehilite
  - pymdownx.caret #下划线
  - pymdownx.mark #文本高亮
  - pymdownx.tilde #删除线
  - pymdownx.arithmatex: # latex支持
      generic: true
  - toc:
      permalink: true # 固定标题位置为当前位置

# 自定义css
extra_css:
  - "//cdn.staticaly.com/gh/codeslive/cdn@main/css/imageszoom.css" #图片放大css
  #- '//cdn.staticaly.com/gh/codeslive/images-pages@main/cdn/css/custom.css'
  #- '//cdn.staticaly.com/gh/codeslive/images-pages@main/cdn/css/simplelightbox.min.css' #图片放大css

# 自定义js
extra_javascript:
  - "//cdn.staticaly.com/gh/codeslive/cdn@main/js/busuanzi.pure.mini.js" # 网站访问统计
  - "//cdn.staticaly.com/gh/codeslive/cdn@main/js/imageszoom.js" # 图片放大js
  #- '//cdn.staticaly.com/gh/codeslive/cdn@main/js/jquery-3.2.1.min.js'
  #- '//cdn.staticaly.com/gh/codeslive/cdn@main/js/simplelightbox.min.js'  #图片放大js
  #- '//cdn.staticaly.com/gh/codeslive/cdn@main/js/custom.js'

# 设置
extra:
  social:
    - icon: fontawesome/brands/github
      link: https://github.com/lyx2099
      name: Visit my github
    - icon: fontawesome/brands/slack
      link: https://lyx2099.github.io/WIKI
      name: Visit myblog
    - icon: fontawesome/solid/paper-plane
      link: mailto:leeyx0913@foxmail.com
      name: Email me

# 文档区
nav:
  - Python:
      - 数据分析:
          - Numpy: Python/DataAnalysis/01 什么是Numpy.md
      - 自动化:
          - Selenium: Python/AutoTest/01 什么是Numpy.md
  - 文学:
      - 历史:
          - 唐史: literary/Tang.md
      - 诗词:
          - 唐诗: literary/TangPoetry.md
  - 旅行:
      - 家乡: trip/GZ.md
      - 广东: trip/GuangDong.md
  - 关于:
      - 个人履历: about/geren.md
```



## 6.部署站点

在 github 上创建一个仓库，例如我的是 `git@github.com:lyx2099/WIKI.git`。在 `WIKI` 目录下执行以下命令：
```shell
git init
git add .
git commit -m 'xxx'
git remote add origin git@github.com:lyx2099/WIKI.git
git push -u origin master
```
这样 `WIKI` 目录下的 `my-wiki` 项目将会被推送到远程仓库的 `master` 分支。  
进入到 `my-wiki` 目录，执行命令：`mkdocs gh-deploy` 会将内人部署到 github。  
稍等一会，访问 [https://lyx2099.github.io/WIKI/](https://lyx2099.github.io/WIKI/) 就可以看到在线博客了。



## 7.如何构建本地博客

首先，博客的导航是在 `mkdocs.yml` 的 `nav` 里面进行设置的，如下：
```yml
nav:
  - Python:
      - 数据分析:
          - Numpy: Python/DataAnalysis/01 什么是Numpy.md
      - 自动化:
          - Selenium: Python/AutoTest/01 什么是Numpy.md
  - 文学:
      - 历史:
          - 唐史: literary/Tang.md
      - 诗词:
          - 唐诗: literary/TangPoetry.md
  - 旅行:
      - 家乡: trip/GZ.md
      - 广东: trip/GuangDong.md
  - 关于:
      - 个人履历: about/geren.md
```

在线访问时的效果如下：

![image-20230513162141282](https://img2023.cnblogs.com/blog/2056203/202305/2056203-20230513162143508-1792648189.png)

其次，所有的文档都应该放在 `docs` 目录下，且每个小分类都应该有一个对应的文件夹，如下：

![image-20230513162449163](https://img2023.cnblogs.com/blog/2056203/202305/2056203-20230513162449781-1101607566.png)


## 8.博客内容
为了提供额外的上下文，可以通过在短代码后面直接使用 title="<custom title>" 选项将自定义标题添加到代码块中，例如显示文件名：
```text
py title="bubble_sort.py
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

``` py title="bubble_sort.py"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```


插入图片测试：
![插入图片测试](my-wiki\docs\microsatsFigures\wallhaven-jxw8vy.jpg)


## END

参考文档：

- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)

- [mkdocs部署教程（图文）](https://blog.csdn.net/qq_41245706/article/details/127740880)
- [mkdocs部署教程（视频）](https://www.bilibili.com/video/BV1FB4y1n7Gf/?spm_id_from=333.337.search-card.all.click&vd_source=c8c8e120161f762ff543dc30b5b87ff2)
- [mkdocs美化](https://juejin.cn/post/7066641709198737416#heading-5)