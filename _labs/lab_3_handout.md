---
type: lab
date: 2023-11-21T7:30:00+00:00
title: '实验 3. Stack and Heap'
tldr: "本次实验进一步练习使用 gdb 和 valgrind、学习 string.h 接口、以及将 C 字符串作为原始数组/指针进行操作。"
pdf: https://cs102doc.stickmind.com/topic_3/lab_3/index.html
hide_from_announcments: true
# attachment: /static_files/starter-proj.zip
---

本次实验进一步练习使用 `gdb` 和 `valgrind`，并提供了大量指针相关的代码供你阅读和练习。数组和指针在 C 语言中无处不在，充分理解它们至关重要。以下一些问题用于检测你的理解，并让你进一步思考这些概念：

- 如果 `ptr` 声明为 `char*`，`ptr++` 的作用是什么？如果 `ptr` 声明为 `int*` 有什么区别？
- 尽管将 `&` 应用于栈上分配的数组名（例如 `&buffer`）是合法的表达式并且具有特定的含义，但实际上这样的用法并不明智。解释为什么这样使用可能会造成错误/误解。
- `malloc` 函数的参数是 `size_t`（无符号整型）。考虑一下错误的调用 `malloc(-1)`，这似乎完全没有意义。但编译器没有任何警告信息——为什么会这样？如果程序中有这样的代码，可能会发生什么？
- `realloc` 函数的目的是什么？如果尝试重新分配非 `malloc` 返回的指针（例如字符串常量）会发生什么情况？
- 内存错误（memory error）和内存泄漏（memory leak）有什么区别？

## 学习目标

- 进一步练习 `gdb` 和 `valgrind`
- 加深对指针和数组的理解
- 尝试编写在堆上动态分配内存的代码

## 初始代码

你的个人用户目录下应该已经有 `cs102` 这个文件夹了，通过下面的命令拷贝初始代码到该目录中：

```bash
cp -r /home/cs102-shared/labs/lab3 ~/cs102
```
