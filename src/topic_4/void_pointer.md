# 泛型指针

本课程第四个话题是讨论泛型编程相关的技术。理解这个问题可以帮助我们更好地理解以下几个问题：

- 编写可以处理任意类型的代码并了解其中的陷阱
- 学习如何将函数作为参数进行传递

泛型编程是一种编程范式，在很多语言中都有具体的应用。编写泛型代码可以降低代码重复，减少代码错误。

在泛型编程方面，C 没有提供很多现成的满足类型安全的泛型函数。C 能提供的比较好的泛型函数也就是 `bsearch`，`qsort`，`memcpy` 这些。

如果从元素大小而不是元素类型的角度看，C 为构建泛型函数仍然提供了可能。C 可以根据元素的大小进行存储并操作。但是由于类型信息缺失，我们需要非常熟悉其内部机制才能够编写出功能完善且健壮的代码。

## 泛型指针

C 的泛型编程极大程度依赖 `void*` 泛型指针，不关联任何数据类型。

- 任何数据类型的地址或指针都可以赋值给 `void*`；`void*` 也可以赋值给任何数据类型的指针。

    ```c
    int arr[] = {2, 4, 6, 8, 10};
    void* arr_p1 = arr;      //  int* ->   void*  
    double* arr_p2 = arr_p1; // void* -> double*
    ```

- `void*` 不可以直接解引用，必须搭配类型转换。

    ```c
    // Buggy #1: void pointers cannot be dereferenced
    int a = 10;
    void* a_ptr = &a;
    // printf("%d", *a_ptr);        // error
    printf("%d\n", * (int*) a_ptr);
    ```

- `void*` 不可以直接进行指针算术运算，必须转换为 `char*` 等具体类型才可以进行算术运算。

    ```c
    // Buggy #2: void pointers doesn’t allow pointer arithmetic
    double b[2] = {1.0, 2.0};
    void* b_ptr = &b;
    // b_ptr = b_ptr + sizeof(double);     // error
    b_ptr = (char*)b_ptr + sizeof(double);
    // or
    b_ptr = (double*)b_ptr + 1;
    ```

由于内存分配函数 `malloc/calloc` 等返回的是 `void*` 类型，所以可以用于分配任何数据类型的内存。除此之外，`void*` 还可以用于实现泛型函数。

## 泛型选择表达式

C11 标准引入了一个**泛型选择**（generic selection）特性，通过宏语句提供泛型支持。其语法类似 `switch-case` 语句，但区别是宏替换是发生在编译期的，类似 C++ 的模板技术。

```c
#include <stdio.h>
#include <math.h>
 
// 实现泛型 cbrt 函数
#define cbrt(X) _Generic((X), \
              long double: cbrtl, \
                  default: cbrt,  \
                    float: cbrtf  \
              )(X)
 
int main(void) {
    double x = 8.0;
    const float y = 3.375;
    printf("cbrt(8.0) = %f\n", cbrt(x));    // 类型为 double，选择默认的 cbrt 函数
    printf("cbrtf(3.375) = %f\n", cbrt(y)); // 类型为 float，自动选择 cbrtf 函数
}
```

感兴趣的同学可以参考在文档和示例程序：[Generic selection (since C11)](https://en.cppreference.com/w/c/language/generic)。关于该技术，本课程不作更多叙述。
