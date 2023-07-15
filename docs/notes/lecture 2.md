---
layout: default
title: lecture 2
nav_order: 2
---

# lecture 2
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

``` cpp
#include<iostream>
using namespace std;

int myFunction(int a, int b) {
 int c = a + b;
 return c;
}

int main() {
 char character = 'd'; // ASCII 
 int integer_num_variable = 1;
 float floating_point_variable = 1.012;
 string myString = "hello world!";
 
 // some comment (ctrl + /)
 cin >> integer_num_variable;
 cout << floating_point_variable << endl;

 int c = myFunction(1, 2);
 return 0;
}
```

## 本周内容

### 条件判断式&流程控制

#### 关键字

- if, else
- switch, case, default, break

``` cpp
if (boolean condition) {

} else if (boolean condition) {

} else {

}


switch (variable) {
 case constant_1: {
  statement_1
  break;
 }
 case constant_2: {
  statement_2
  break;
 }
 default: {
  statement_default
  break;
 }
}
```

**问题**：什么时候选择if else结构，什么时候选择switch结构?

### 转型 (Type Casting)

- 自动转型
  - `int a = 3 * 3.141;`
- 强制转型
  - `float a = float(3) / 3.141;`

**问题**：`float a = float(10/3); 和 float a = float(10) / float(3);`的结果一样吗?

### 二进制

- 10进制 => 2进制
- 2进制 => 10进制

**问题**：为什么使用2进制而不是其他进制(如10进制，60进制）?

### 数据类型大小

``` cpp
#include <iostream>
int main()
{
 std::cout << "bool:\t\t" << sizeof(bool) << " bytes\n";
 std::cout << "char:\t\t" << sizeof(char) << " bytes\n";
 std::cout << "wchar_t:\t" << sizeof(wchar_t) << " bytes\n";
 std::cout << "char16_t:\t" << sizeof(char16_t) << " bytes\n";
 std::cout << "char32_t:\t" << sizeof(char32_t) << " bytes\n";
 std::cout << "short:\t\t" << sizeof(short) << " bytes\n";
 std::cout << "int:\t\t" << sizeof(int) << " bytes\n";
 std::cout << "long:\t\t" << sizeof(long) << " bytes\n";
 std::cout << "long long:\t" << sizeof(long long) << " bytes\n";
 std::cout << "float:\t\t" << sizeof(float) << " bytes\n";
 std::cout << "double:\t\t" << sizeof(double) << " bytes\n";
 std::cout << "long double:\t" << sizeof(long double) << " bytes\n";
 return 0;
}
```

**问题**：为什么char类型的变量不能存储中文字?

### 三角交换

``` cpp
#include <iostream>
int main()
{
 int a = 1, b = 2;
 int tmp = a;
 a = b;
 b = tmp;
 std::cout << a << " " << b;
 return 0;
}
```

进阶版

``` cpp
// using reference
void swap(int &a, int &b)
{
 int temp = a;
 a = b;
 b = temp;
}

// using pointer
void swap(int *a, int *b)
{
 int temp = *a;
 *a = *b;
 *b = temp;
}
```

### 循环结构

- for
- while

**问题**：

1. 解释for loop各部分的作用
2. while和do while的区别？
3. 什么时候用for结构，什么时候用while结构？
4. for 和 while结构可以相互转换吗？
5. break的作用
6. continue的作用

### 拓展

- 排序
- bubble sort
	- <https://www.hackerearth.com/practice/algorithms/sorting/bubble-sort/visualize/>
	- <https://visualgo.net/en/sorting>
	- <https://www.cs.usfca.edu/~galles/visualization/ComparisonSort.html>
	- <https://sortvisualizer.com/bubblesort/>

``` cpp
int arr[] = {1,3,2,4,6,2,4};
for (int i = 0; i < n - 1; i++)
{
 for (int j = 0; j < n - i - 1; j++)
 {
  if (arr[j] > arr[j + 1])
  {
  int temp = arr[j];
  arr[j] = arr[j+1];
  arr[j+1] = temp;
  // swap(arr[j], arr[j + 1]);
  }
 }
}
```

给3个变量（a,b,c)，怎么排序？

- bubble sort（原来为for结构，平摊成if结构）+ 三角交换

```cpp
if (a > b) swap(a, b);
if (b > c) swap(b, c);
if (a > b) swap(a, b);
```
