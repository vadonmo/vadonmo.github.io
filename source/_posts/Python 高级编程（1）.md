---
title: Python 高级编程（1）
date: 2019-10-23 09:06:24
toc: true
category: Python
tags: 
 - Python
 - 学习
---
## 前言
当前 Python 版本主要存在 2 和 3 两个版本，就目前来看 2 已经逐步淡出历史舞台。学习时也应该从 3 开始，除非你还在看着老古董级别的教科书。
<!-- more -->
## Python 最新消息来源
Python 官方消息来源为 PEP，[PEP](https://www.python.org/dev/peps/) 的全称为 Python 改进提案（Python Enhancement Proposal,PEP）。它是 Python 变化的书面文档。
PEP 0 则告诉你最新的 Python 消息。
## Python 2 和 Python 3 的差异
  ### 语法变化
  1. `ptint` 不再是一条语句而是一个函数，必须加上括号。
  2. 捕获异常的语法由 `except exc, var` 改成 `except exc as var` 。
  3. 弃用比较运算符 `<>` ，改用 `!=` 
  4. `from module import * ` 只能用于模块，不能用在函数中。
  5. 现在 `from .[model] import name` 是相对导入唯一正确的语法。所有不以点字符开头的导入都被当做绝对导入。
  6. `sorted` 函数与列表的 `sort` 方法不再接受 `cmp` 参数，应该用 `key` 参数来代替。
  7. 整数除法表达式返回的是浮点数。取整运算可以用 `//` 运算符，如 `1//2`。
   
### 标准库中的变化
   部分模块进行了添加、弃用、改进或完全删除，一般来说这种变化在导入时就会抛出异常，从而发现问题所在。
### 数据类型与集合的变化
3 中所有的字符串都是 `Unicode` ，字节（`bytes`）需要加一个 `b` 或 `B` 的前缀。不支持使用 `u` 前缀，使用会引发语法错误。