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

当前 `Python` 版本主要存在 2 和 3 两个版本，就目前来看 2 已经逐步淡出历史舞台。学习时也应该从 3 开始，除非你还在看着老古董级别的教科书。
<!-- more -->

## `Python` 最新消息来源

`Python` 官方消息来源为 PEP，[PEP](https://www.python.org/dev/peps/) 的全称为 `Python` 改进提案（Python Enhancement Proposal,PEP）。它是 Python 变化的书面文档。
PEP 0 则告诉你最新的 `Python` 消息。

## `Python 2` 和 `Python 3` 的差异

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

3 中所有的字符串都是 `Unicode` ，字节（`bytes`）需要加一个 `b` 或 `B` 的前缀。~~不支持使用 `u` 前缀，使用会引发语法错误。~~(3.0和3.1不支持，3.3已恢复该前缀)
## 用于跨版本兼容性的常用工具和技术

#### 定义版本号

格式为：主版本号.次版本号.修订号[.先行版本号、编译信息]
- 主版本号（`MAJOR`）：当你做了不兼容的API修改
- 次版本号（`MINOR`）：当你做了向后兼容的功能性新增
- 修订号（`PATCH`）：当你做了向后兼容的问题修正
  
#### `__future__` 模块

`__future__` 模块主要功能是将新版本中的一些功能反向迁移至就版本中，采用的是导入语句的形式。
```
from __future__ import <feature>
```
可用语句：
- `division` ：`python 3` 新增的除法运算符（PEP238）。
- `absolute_import` ：将所有不以点字符开头的 `import` 语句格式解释为绝对导入（PEP 328）。
- `print_function` ： 将 `print` 语句变为函数使用。（PEP 3112）。
- `unicode_literals` ：将每个字符串解释为 `Unicode` （PEP 3112）。

#### Six 模块

提供了常用的兼容性的整个样板。使用时依然采用导入形式。
```
import six.moves.urllib as urllib
```
## 其他 `Python` 实现

一般讨论的 `Python` 指的是 `CPython`，此外还有 `Stacklless Python`，`Jpython`，`Iron Python`，`PyPy`。

## 环境隔离

环境隔离用于解决各种库版本的相互依赖，避免依赖相互冲突。

### 好处

- 解决了这样的难题：”X项目依赖1.x版本，而Y项目依赖4.x版本“。
- 项目不再受限于系统发行版仓库中包的版本。
- 不会破坏依赖特定包版本的其他系统服务。
- 项目依赖的包列表可以轻松”锁定（frozen）“，复制起来也很容易。

#### 解决方案

#### 应用层

1. virtualenv
2. venv
3. buildout

#### 系统级
1. Vagrant
2. Docker


## 其他资源
- Python 文档
- PyPI-Python 包索引
- PEP 0-Python 改进提案索引
   