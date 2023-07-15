---
layout: default
title: lecture 5
parent: Notes
nav_order: 5
---

# lecture 5
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## 上周回顾

- 多维数组 (multi-dimensional/nested array)
- 巢状循环 (nested loop)
- 函数 (function)
- 指标/指针 (pointer)

## 本周内容

### 参考/引用(reference)

- const pointer(cannot repoint), automatically add '\*' during dereference
- 为一个对象定义别名
- <https://cppbyexample.com/references.html>

- 用处
  - <https://cppbyexample.com/why_references.html>

1. 通过引用传递参数
	- 通过值传递参数 vs 通过引用传递参数 ?
	- 通过**值**传递参数(pass by value)：复制了一个新的变量，新的变量和旧的变量分别存储在不同的内存空间。
		- C++ default 的行为是：通过**值**传递参数。
	- 通过**引用**传递参数(pass by reference)：两个变量存储在同一个内存空间
		- 在函数参数写上`&`
		- 好处：提高处理速度，减少不必要的额外空间
2. 给变量取别名(alias)
	- 好处：提高代码可读性

``` cpp
#include <iostream>

// 通过值传递参数i
void square_copy(int i)
{
 i = i * i;
}

// 通过引用传递参数i
void square_reference(int &i)
{
 i = i * i;
}

void print_int(const int &i)
{
 std::cout << i << "\n";
}

int main()
{
 int aWeirdVariableName = 0; // 0x0b
 // iAlias is another name for the variable "aWeirdVariableName"
 int &iAlias = aWeirdVariableName;

 iAlias = iAlias + 2;
 print_int(aWeirdVariableName); // 2
 print_int(iAlias); // 2

 iAlias = iAlias * 6;
 print_int(aWeirdVariableName); // 12
 print_int(iAlias); // 12

 square_copy(iAlias); 
 print_int(aWeirdVariableName); // 12
 print_int(iAlias); // 12

 square_reference(iAlias);
 print_int(aWeirdVariableName); // 144
 print_int(iAlias); // 144

 iAlias = 42;
 print_int(aWeirdVariableName); // 42
 print_int(iAlias); // 42
}
```

### 参考/引用(reference) vs 指针(pointer)

- <https://cppbyexample.com/pointers_vs_references.html>
- <https://www.geeksforgeeks.org/pointers-vs-references-cpp/>
- 指针灵活性较高，可应用范围较广，很多数据结构都用指针实现
- 参考的可应用范围较小，通常用在函数的`参数传递过程`，用以实现 `pass by reference`

|                | References                                               | Pointers                                                           |
| -------------- | -------------------------------------------------------- | ------------------------------------------------------------------ |
| Repoint   | The variable cannot repoint.          | The variable can repoint.                        |
| Memory Address | It shares the same address as the original variable.     | Pointers have their own memory address.                            |
| Work           | It is referring to another variable.                     | It is storing the address of the variable.                         |
| Null Value     | It does not have null value.                             | It can have value assigned as null.                                |

### 参考和指针的实际应用

```cpp
#include <iostream>
using namespace std;

// using reference
void swap_using_reference(int &a, int &b)
{
 int temp = a;
 a = b;
 b = temp;
}

// using pointer
void swap_using_pointer(int *a, int *b)
{
 int temp = *a;
 *a = *b;
 *b = temp;
}

int main()
{
 int a = 1;
 int b = 2;

 // swap using reference
 swap_using_reference(a, b);
 cout << a << " " << b << endl; // 2 1

 // swap using pointer
 swap_using_pointer(&a, &b);
 cout << a << " " << b << endl; // 1 2

 // swap using std::swap
 swap(a, b);
 cout << a << " " << b << endl; // 2 1
}
```
