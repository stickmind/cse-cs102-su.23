# Summary

[前言](preface.md)

# 开发环境 Linux & C

- [Linux 介绍](topic_0/linux_intro.md)
  - [Windows 模拟 Linux 环境](topic_0/linux_on_windows.md)
  - [Ubuntu 虚拟机安装及配置](topic_0/linux_virtual_box.md)
- [Linux 命令行](topic_0/linux_command.md)
  - [基本命令](topic_0/linux_command_pt1.md)
  - [文件操作](topic_0/linux_command_pt2.md)
  - [文件搜索](topic_0/linux_command_pt3.md)
- [从 C++ 到 C](topic_0/from_cxx_to_c.md)
  - [simpio.h](topic_0/from_cxx_to_c_simpio.md)
  - [strlib.h](topic_0/from_cxx_to_c_strlib.md)
  - [Pig Latin](topic_0/from_cxx_to_c_pig_latin.md)
- [实验 0：上手 Linux 开发环境](topic_0/lab_0.md)
- [作业 0：使用 Linux 和 C](topic_0/assign_0.md)
  - [入侵者检测](topic_0/assign_0_pt1.md)
  - [谢尔宾斯基分形](topic_0/assign_0_pt2.md)
  - [作业提交](topic_0/assign_0_pt3.md)

# 数据的表示 Data Representation

- [位和字节](topic_1/num_base.md)
  - [二进制](topic_1/num_base_pt1.md)
  - [十六进制](topic_1/num_base_pt2.md)
- [整数的表示](topic_1/int_rep.md)
  - [无符号整型](topic_1/int_rep_pt1.md)
  - [有符号整型](topic_1/int_rep_pt2.md)
  - [整型溢出](topic_1/overflow.md)
  - [整型转换](topic_1/conversion.md)
- [位运算](topic_1/bitwise.md)
  - [应用：位掩码](topic_1/bitmask.md)
- [实验 1：数据的表示](topic_1/lab_1.md)
  - [位运算](topic_1/lab_1_pt1.md)
  - [圆整](topic_1/lab_1_pt2.md)
  - [中点计算](topic_1/lab_1_pt3.md)
  - [工作流练习](topic_1/lab_1_pt4.md)
- [作业 1：有趣的位](topic_1/assign_1.md)
  - [饱和计算](topic_1/assign_1_pt1.md)
  - [细胞自动机](topic_1/assign_1_pt2.md)
  - [UTF-8](topic_1/assign_1_pt3.md)
  - [测试与提交](topic_1/assign_1_pt4.md)
  - [作业解读](topic_1/assign_1_hints.md)

# 数组和指针 Array & Pointer


- [字符串](topic_2/string.md)
  - [字符串作为数组](topic_2/string_pt1.md)
  - [string.h](topic_2/string_pt2.md)
  - [字符串作为指针](topic_2/string_pt3.md)
- [数组和指针](topic_2/array_and_pointer.md)
  - [指针新解：理解 *p 的特殊性](topic_2/array_and_pointer_pt1.md)
  - [数组索引和指针运算](topic_2/array_and_pointer_pt2.md)
  - [多维数组和二级指针](topic_2/array_and_pointer_pt3.md)
- [函数参数](topic_2/function_params.md)
- [实验 2：数组和指针](topic_2/lab_2.md)
  - [GDB 探究指针和数组](topic_2/lab_2_pt1.md)
  - [探究 atoi](topic_2/lab_2_pt2.md)
  - [使用 Valgrind](topic_2/lab_2_pt3.md)
  - [探究 strtok](topic_2/lab_2_pt4.md)
- [作业 2：C 字符串](topic_2/assign_2.md)
  - [背景：文件系统和 Shell](topic_2/assign_2_pt1.md)
  - [实现 get_env_value](topic_2/assign_2_pt2.md)
  - [实现 scan_token](topic_2/assign_2_pt3.md)
  - [实现 mywhich](topic_2/assign_2_pt4.md)
  - [测试与提交](topic_2/assign_2_pt5.md)

# 栈和堆 Stack & Heap

- [内存布局](topic_3/memory_layout.md)
- [内存管理](topic_3/memory_allocation.md)
- [结构体](topic_3/struct.md)
  - [设计栈 ADT](topic_3/stack_adt.md)
- [实验 3：栈和堆](topic_3/lab_3.md)
  - [堆内存的使用](topic_3/lab_3_pt1.md)
  - [Valgrind 检测内存错误](topic_3/lab_3_pt2.md)
  - [Valgrind 检测内存泄漏](topic_3/lab_3_pt3.md)
  - [调试练习](topic_3/lab_3_pt4.md)
- [作业 3：有趣的堆](topic_3/assign_3.md)
  - [背景：过滤命令](topic_3/assign_3_pt1.md)
  - [实现 read_line](topic_3/assign_3_pt2.md)
  - [实现 mytail](topic_3/assign_3_pt3.md)
  - [实现 myuniq](topic_3/assign_3_pt4.md)
  - [测试与提交](topic_3/assign_3_pt5.md)
 
# 泛型编程 Generic C

- [泛型指针](topic_4/void_pointer.md)
- [函数指针](topic_4/function_pointer.md)
- [实验 4：泛型和回调](topic_4/lab_4.md)
  - [回调函数](topic_4/lab_4_pt1.md)
  - [探究 gfind_max](topic_4/lab_4_pt2.md)
  - [探究 bsearch_bug](topic_4/lab_4_pt3.md)
  - [探究 memmove](topic_4/lab_4_pt4.md)
  - [GDB 调试技巧](topic_4/lab_4_pt5.md)
- [作业 4：深入泛型指针](topic_4/assign_4.md)
  - [探究 scandir](topic_4/assign_4_pt1.md)
  - [实现 myls](topic_4/assign_4_pt2.md)
  - [探究 bsearch](topic_4/assign_4_pt3.md)
  - [实现 binsert](topic_4/assign_4_pt4.md)
  - [实现 mysort](topic_4/assign_4_pt5.md)
  - [测试与提交](topic_4/assign_4_pt6.md)

# 汇编语言 x86-64 Assembly

# 堆分配器 Heap Allocator

-----------

[更新记录](misc/contributors.md)
