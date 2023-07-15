---
layout: default
title: lecture 4
nav_order: 4
---

# lecture 4

## 上周回顾
- 数据结构
	- 数组
	- vector
- 排序
	- selection sort
- 搜索
	- linear search
	- binary search
- 空间/时间复杂度

作业：
- bubble sort 逆序排序
``` cpp
int arr[] = {1,3,2,4,6,2,4};
for (int i = 0; i < n - 1; i++)
  {
    for (int j = 0; j < n - i - 1; j++)
    {
      if (arr[j] < arr[j + 1])
      {
        swap(arr[j], arr[j + 1]);
      }
    }
  }
```

## 本周内容
### 多维数组
- 术语：
	- 行（row）
	- 列（column）
``` cpp
int array[3][5]
{
	{ 1, 2, 3, 4, 5 }, // row 0
	{ 6, 7, 8, 9, 10 }, // row 1
	{ 11, 12, 13, 14, 15 } // row 2
};
```
**问题**：
1. 第1行第3列是？9
2. 如何存取第2行第1列的元素？`array[2][1] = 100;  cout << array[2][1] << endl;`

### 巢状循环 (nested loop)
- 例子：sorting
``` cpp
int N = 10;
for(int i=1; i<N; i++){  //i (N-1) ==> O(N)
	for(int j=1; j<N; j++){ // i*1  ~  i*9 (N-1) ==> O(N)
		cout << i*j << " "; // C ==> O(1)
	}
}
```
**问题**：
1. 上述代码的时间复杂度是？O(N^2)

### 函数 （function）
- 让代码更简洁
- 例子：main函数
- https://cppbyexample.com/functions.html
``` cpp
#include <iostream>
using namespace std;

int multiply(int a, int b)
{
	return a * b;
}

void print_int(int a)
{
	std::cout << a << "\n";
}

void add_type_1(int a)
{
	a++;
}

int add_type_2(int a)
{
	return a + 1;
}

void add_type_3(int &a)
{
	a++;
}

int main()
{
	int a = 10;
	add_type_1(a); //10
	print_int(a); //10

	int b = 10;
	b = add_type_2(b);
	print_int(b);

	int c = 10;
	add_type_3(c);
	print_int(c);

	print_int(42);

	print_int(multiply(7, 3));

	return 0;
}
```
**问题**：
1. `print_int(a)` 会输出什么？10
2. `print_int(b)` 会输出什么？11
3. `print_int(c)` 会输出什么？11

### 指标/指针 (pointer)
- 储存内存地址的变量
- https://cppbyexample.com/pointer.html
- 为什么使用指标
	- https://cppbyexample.com/why_pointer.html
	- 把变量存储在heap
		- 好处：每个函数都有一个stack空间，用以存储变量，当函数执行结束时，该stack内存空间就被解散，stack内的变量也不再存在；相反地，当函数执行结束时，heap内存空间不受影响，heap内的变量仍存在，直到程序执行结束。
		- 坏处：memory leaked （忘记delete)
		- `new` :给变量分配heap内存空间 `int *p = new int;`
		- `delete` :移除分配给变量的heap空间 
		- stack vs heap
			- https://stackoverflow.com/questions/5836309/stack-memory-vs-heap-memory
			- https://www.geeksforgeeks.org/new-and-delete-operators-in-cpp-for-dynamic-memory/
	- 动态分配内存空间
		- 动态数组
		- linked list 

- We use the ampersand (**`&`**) to say “the address of this variable”.
- The asterisk (**`*`**) has two meanings, depending on the _context_ of its use:
    - 宣告指标变量：When placed _after_ a `type` an asterisk (`*`) means “this type is a pointer”. The `type*` syntax means _one thing_, it means “a pointer to a value of `type`“.
    - 存取指标地址所存储的值：When placed _before_ a variable that is a pointer it means “the value at the given address”. In this form it’s known as the “dereference operator”.

``` cpp
#include <iostream>

using std::cout;

int main() {
  int answer = 42;
  int* theAddressOfAnswer = &answer; // 0xffb61098

  cout << "The answer is: " << answer << "\n";

  cout << "The address of answer is: " 
       << theAddressOfAnswer << "\n";
  
  cout << "The answer (through a pointer) is: " 
       << *theAddressOfAnswer << "\n";
       
  return 0;
}
```

- 判断指针是否指向某个地址
	- nullptr
	- if 逻辑判断
		- 空指针会被转型成false
		- 有地址的指针会被转型成true
``` cpp
#include <iostream>

using std::cout;

int main()
{
	int answer = 42;
	int *pointer = nullptr;

	if(pointer != nullptr) {
		cout << *pointer << endl;
		// do something
	}	

	if (pointer)
	{
		cout << "Pointer points to value: " << *pointer << "\n";
	}
	else
	{
		cout << "Pointer points to nothing\n";
	}

	pointer = &answer;

	if (pointer)
	{
		cout << "Pointer points to value: " << *pointer << "\n";
	}
	else
	{
		cout << "Pointer points to nothing\n";
	}

	cout << "We're going to crash now." << std::endl;
	pointer = nullptr;
	cout << *pointer << "\n"; // BOOM!
}
```

- **问题**：
1. 指标是变量吗？是
2. 可以改变指标指向的空间吗？（原来指向一个空间，改成指向另一个空间）可以

### 参考vs指针
- https://cppbyexample.com/pointers_vs_references.html