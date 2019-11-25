---
title: "关于 gitignore 文件"
authors: [kiki]
tags: [git]
categories: [blog]
draft: false
---

- [格式规范](#%e6%a0%bc%e5%bc%8f%e8%a7%84%e8%8c%83)
  - [通配符](#%e9%80%9a%e9%85%8d%e7%ac%a6)
  - [斜线](#%e6%96%9c%e7%ba%bf)
  - [两个星号](#%e4%b8%a4%e4%b8%aa%e6%98%9f%e5%8f%b7)
  - ["!" 取消忽视](#%22%22-%e5%8f%96%e6%b6%88%e5%bf%bd%e8%a7%86)
- [忽略文件示例](#%e5%bf%bd%e7%95%a5%e6%96%87%e4%bb%b6%e7%a4%ba%e4%be%8b)
- [参考](#%e5%8f%82%e8%80%83)

## 格式规范

- 所有空行或者以 ＃ 开头的行都会被 git 忽略
- 可以使用标准的 glob 模式匹配
  - glob 模式指 shell 所使用的简化了的正则表达式，包括`*`、`?`、`[]`、`**`
- 匹配模式可以以(/)开头防止递归
- 匹配模式可以以(/)结尾指定目录
- 要忽略指定模式以外的文件或目录, 可以在模式前加上惊叹号(!)取反

### 通配符

- `*` 匹配除了 `/` 的所有字符，匹配零个或多个任意字符
- `?` 匹配除了 `/` 的所有单字符
- `[]` 匹配任何一个列在方括号中的字符：如果在方括号中使用短划线分隔两个字符, 表示所有在这两个字符范围内的都可以匹配
  - 比如 `[0-9]` 表示匹配所有 0 到 9 的数字

### 斜线

- 行首第一个 `/` 匹配路径的开始, 以 `.gitignore` 当前所在路径计算相对路径
- 如 `/*.txt` 匹配与 `.gitignore` 同一路径下的 txt 文件, 不包含 `.gitignore` 当前路径下子文件内的 txt 文件
  - `test/*.txt` 路径的开始是 `t` 而不是 `/`

### 两个星号

- `**/` 匹配任意中间目录
- `/**` 匹配包含的所有内容, 包括文件和文件夹, 以及子文件和子文件下的文件
- `/**/` 匹配 0 个或多个目录

### "!" 取消忽视

- `!pattern` 否认 pattern, 即前一个 pattern 匹配的文件会再被包含
- 注意: 如果一个文件的父文件夹被忽略, 那么 git 不能再包含该文件
- 忽视除了 /build/debug 下 除了 snap 的文件和文件夹

```gitignore
## 前两句可互换顺序
build/debug/*
!build/debug
!build/debug/snap
## 如果包含下面的语句则不能再包含 snap 文件和文件夹
# build
# build/
# build/**
```

## 忽略文件示例

- `# 注释行`
- `*.[oa]`        # 忽略所有以 .a 或 .o 为扩展名的文件
- `!lib.a`        # 但是 lib.a 文件或者目录不要忽略
- `/TODO`         # 只忽略根目录下的 TODO, 子目录的 TODO 不忽略
- `build/`        # 忽略所有 build/ 目录下的文件
- `doc/*.txt`     # 忽略 doc/*.txt, 但 doc/server/*.txt 不忽略
- `doc/**/*.pdf`  # 忽略 doc文件夹下所有的*.pdf

## 参考

- [教程](https://git-scm.com/docs/gitignore)
- [ignore 模板](https://github.com/github/gitignore)