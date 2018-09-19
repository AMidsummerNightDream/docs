---
sidebar: auto
prev: ./some-other-page
next: false
---
# npm

### cnpm

``` bash
$ npm install -g cnpm --registry=https://registry.npm.taobao.org
```

## git
`git add` - Add file contents to the index

`git add -u [<path>]`: 把`<path>`中所有跟踪文件中被修改过或已删除文件的信息添加到索引库。它不会处理那些不被跟踪的文件。省略`<path>`表示 . ,即当前目录。

`git add -A`: []表示把中所有跟踪文件中被修改过或已删除文件和所有未跟踪的文件信息添加到索引库。省略`<path>`表示 . ,即当前目录。

`git add -i`: 我们可以通过`git add -i [<path>]`命令查看中被所有修改过或已删除文件但没有提交的文件，并通过其revert子命令可以查看`<path>`中所有未跟踪的文件，同时进入一个子命令系统。


``` bash
$ git init
$ git clone
$ git add
```