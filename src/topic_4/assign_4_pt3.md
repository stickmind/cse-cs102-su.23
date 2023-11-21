# 探究 bsearch

接下来，你将学习以下代码，以便实现一个通用的二分插入函数，即使用二分搜索高效地将元素插入到一个有序数组中。在稍后的作业中，你将使用它作为 `sort` 命令实现的一部分。编写一个正确的二分搜索函数本身就相当困难，而实现一个通用的 `void*` 函数只会增加挑战。如果需要复习二分搜索算法，可以查看 CS101 配套课本。

我们提供了一份来自 [bsearch.c (apple.com)](https://opensource.apple.com/source/gcc/gcc-5659/libiberty/bsearch.c.auto.html) 的通用二分搜索 `bsearch` 的代码。稍后你将修改此实现，作为你自己的 `binsert` 函数的一部分，因此了解它的工作原理非常重要。请仔细研究！如果你还没有完成实验 4 中有关 `void*` 的练习，那么现在可以继续巩固这些知识。

```c
void *apple_bsearch(const void *key, const void *base, 
                    size_t nmemb, size_t width, 
                    int (*compar)(const void *, const void *)) {
    for (size_t nremain = nmemb; nremain != 0; nremain >>= 1) {
        void *p = (char *)base + (nremain >> 1) * width;
        int sign = compar(key, p);
        if (sign == 0) {
            return p;
        }
        if (sign > 0) {  /* key > p: move right */
            base = (char *)p + width;
            nremain--;
        }       /* else move left */
    }
    return NULL;
}
```

- 在实验 1 中，我们阅读了 Joshua Bloch 的文章 [Nearly All Binary Searches and Mergesorts are Broken](https://research.googleblog.com/2006/06/extra-extra-read-all-about-it-nearly.html)，讨论了实现中点计算的问题。 Apple 的 `bsearch` 实现是否存在文章中指出的错误？解释下原因。
- 注释 `/* else move left */` 似乎注释了一个空的 `else` 语句块。当符号为负时，搜索如何向左移动呢？
- 对 `void*` 执行指针算术运算是非法的，因此强制转换为 `char*`。在实验 4 中，我们研究过 `musl_memmove`，它将其 `void*` 参数复制到函数开头的 `char*` 类型的局部变量中，从而避免了转换的必要。相比之下，Apple 的 `bsearch` 将其参数保留为 `void*` 并在每个指针算术运算之前显式强制转换。这种处理背后的依据是 `void*` 类型传达了该指针的特殊性质，不会误导用户认为该参数是一个普通的 C 字符串。保持它的 `void*` 属性还意味着，如果你不小心对其执行解引用或指针算术运算，编译器会报警。每次对 `void*` 的操作都需要显式强制转换，这种故意的类型转换强调了程序员的设计意图。
- 假设变量 `void *arr` 是数组的基地址，`void *found` 是搜索到的元素的地址，`size_t width` 是每个元素的大小（以字节为单位），那么将 `found` 转换为其相应的数组索引的 C 表达式是什么？

完成这一步是一项巨大的成就。这段代码中发生了很多事情，你应该感到自豪，因为你可以理解这样的库代码了，还能利用它来实现一个通用的二分搜索！有了这些知识储备，你就可以开始编写 `binsert`，这是 Apple `bsearch` 的一个变体。
