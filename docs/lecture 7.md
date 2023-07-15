---
layout: default
title: lecture 7
nav_order: 7
---

# lecture 7

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

- \<cstring>
- \<string>

## 本周内容

### 函数

```cpp
#include <iostream>
#include <vector>

int add(int a, int b) {
  return a + b;
}

float average(const std::vector<int>& numbers) {
  float sum = 0;
  for (int i : numbers) {
    sum += i;
  }
  return sum / numbers.size();
}

int main() {
  int result1 = add(40, 2);
  std::cout << result << "\n";
  
  std::vector numbers{70, 80, 90, 100};
  float avg = average(numbers);
  std::cout << avg << "\n";

  return 0;
}
```

#### swap

```cpp
#include <iostream>
using namespace std;

// pass by value
void swap_incorrect(int a, int b) {
    int temp = a;
 a = b;
 b = temp;
}

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

 // swap_incorrect
 swap_incorrect(a, b);
 cout << a << " " << b << endl; // 1 2
 
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

### 递归

#### factorial

```cpp
#include <iostream>

// Calculate the factorial of N, or N!
// The factorial of N is N * N-1 * N-2 ... * 1
// 7! = 7 * 6 * 5 * 4 * 3 * 2 * 1
// 0! = 1
// 1! = 1
uint64_t factorial(uint64_t n) {
  if (n == 0 || n == 1) {
    return 1;
  }
  return n * factorial(n - 1); 
}

int main() {
  std::cout << factorial(7) << "\n";
  
  // calculate factorial with for loop
  int sum = 1;
  for (int i = n; i >= 0; i--) {
   sum *= n;
  }
}
```

#### Fibonacci

```cpp
#include <iostream>

// Calculate the Nth fibonacci number where 0 is the 0th number
// The Fibonacci rule is the Nth number is equal to the sum of the
// previous two numbers, so N = (N-1) + (N-2)
// The first two numbers should be 0 and 1
// The first 8 Fibonacci numbers are 0, 1, 1, 2, 3, 5, 8, 13
uint64_t fibonacci(uint64_t n) {
  if (n == 0) {
    return 0; 
  } else if (n == 1) {
    return 1;
  }
  return fibonacci(n - 1) + fibonacci(n - 2);
}

int main() {
  std::cout << fibonacci(7) << "\n";
}
```

#### 如何创建cpp文档

1. 打开记事本
2. 输入内容
3. save as .cpp

#### 配置本地环境

- vscode
  - <https://code.visualstudio.com/docs/cpp/config-mingw#_prerequisites>
  - <https://www.youtube.com/watch?v=9VE7p-he4fA>
