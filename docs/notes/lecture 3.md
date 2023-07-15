---
layout: default
title: lecture 3
nav_order: 3
---

# lecture 3
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

- 条件判断：if else结构， switch结构
- 循环：for结构，while结构
- 三角交换
- bubble sort
  - 上周说的是顺序排序
  - 逆序排序？

- ch3 question 7
  - Logical Operators
    - (boolean expression) `&&` (boolean expression
    - `||`
    - `!`
  - Bitwise Operators
    - <https://www.programiz.com/cpp-programming/bitwise-operators>
    - 操作二进制数
    - `&` 0 & 1 ==> 0
    - `|`
    - `^` 0 ^ 1 ==> 1
    - `~` ~0 ==> 1, ~1 ==> 0
    - `<<`  0001(1) << 1  ==> 0010(2) << 1 ==> 0100 (4) << 1 ==> 1000(8)
    - `>>` 00001000 >> 2 => 00000010
- {1,3,4,5,7}
- 10111010 (1byte)
- int exist[8] ={0, 1, 0, 1, 1, 1, 0, 1} (4byte\*8==>32byte)

``` cpp
and
a && b
a & b

or
a || b
a | b

xor
(a && !b) || (!a && b)
a ^ b
```

## 本周内容

### 数组

- 如何定义数组
- 如何初始化数组
- 如何写入数组
- 如何从数组读出数据

``` cpp
#include <iostream>
using namespace std;

int main()
{
 int int_write_arr_a[3];
 int_write_arr_a[0] = 100;
 int_write_arr_a[1] = 200;
 int_write_arr_a[2] = 300;
 
 // write to array
 for (int i = 0; i < 3; i++)
 {
  cin >> int_write_arr_a[i];
 }

 // read from array
 for (int i = 0; i < 3; i++)
 {
  cout << "int_write_arr_a[" << i << "] = " << int_write_arr_a[i] << endl;
 }

 int int_arr_a[] = {1, 2, 3};
 int int_arr_b[3] = {1, 2, 3};
 int int_arr_c[]{1, 2, 3};
 int int_arr_d[3]{1, 2, 3};

 float float_arr_a[] = {1.0, 2.0, 3.0};
 float float_arr_b[3] = {1.0, 2.0, 3.0};
 float float_arr_c[]{1.0, 2.0, 3.0};
 float float_arr_d[3]{1.0, 2.0, 3.0};

 char char_arr_a[] = {'a', 'b', 'c', '\0'};
 char char_arr_b[4] = {'a', 'b', 'c', '\0'};
 char char_arr_c[]{'a', 'b', 'c', '\0'};
 char char_arr_d[4]{'a', 'b', 'c', '\0'};
 char char_arr_e[] = "abc"; // not string
 // char char_arr_f[3] = "abc";
 char char_arr_f[4] = "abc";
 char char_arr_g[]{"abc"};

 for (int i = 0; i < 3; i++)
 {
  cout << "int_arr_a[" << i << "] = " << int_arr_a[i] << endl;
  cout << "int_arr_b[" << i << "] = " << int_arr_b[i] << endl;
  cout << "int_arr_c[" << i << "] = " << int_arr_c[i] << endl;
  cout << "int_arr_d[" << i << "] = " << int_arr_d[i] << endl;
 }

 for (int i = 0; i < 3; i++)
 {
  cout << "float_arr_a[" << i << "] = " << float_arr_a[i] << endl;
  cout << "float_arr_b[" << i << "] = " << float_arr_b[i] << endl;
  cout << "float_arr_c[" << i << "] = " << float_arr_c[i] << endl;
  cout << "float_arr_d[" << i << "] = " << float_arr_d[i] << endl;
 }

 cout << "char_arr_a = " << char_arr_a << endl;
 cout << "char_arr_b = " << char_arr_b << endl;
 cout << "char_arr_c = " << char_arr_c << endl;
 cout << "char_arr_d = " << char_arr_d << endl;
 cout << "char_arr_e = " << char_arr_e << endl;
 cout << "char_arr_f = " << char_arr_f << endl;
 cout << "char_arr_g = " << char_arr_g << endl;

 return 0;
}
```

#### 使用库函数来排序

``` cpp
#include <iostream>
#include <algorithm> // for sort
using namespace std;

int main()
{
 int arr[] = {1, 9, 2, 4, 3, 8, 7, 6, 5, 0};

 // sort in ascending order
 sort(arr, arr + 10);
 
 // print array
 for (int i = 0; i < 10; i++)
 {
  cout << "arr[" << i << "] = " << arr[i] << endl;
 }
 cout << "========================" << endl;

 // sort in descending order
 sort(arr, arr + 10, greater<int>());

 // print array
 for (int i = 0; i < 10; i++)
 {
  cout << "arr[" << i << "] = " << arr[i] << endl;
 }

 return 0;
}
```

### vector

- 类似数组，但是封装了许多可以调用的功能
- 参考资料
  - <https://www.programiz.com/cpp-programming/vectors> (入门)
  - <https://hackingcpp.com/cpp/std/sequence_containers.html#vector> （可视化）
  - <https://cplusplus.com/reference/vector/vector/> （文档）

``` cpp
#include <iostream>
#include <vector> // for vector
#include <algorithm> // for sort

using namespace std;

void print(vector<int> &vec)
{
 for (int i = 0; i < vec.size(); i++)
 {
  cout << "vec[" << i << "] = " << vec[i] << endl;
 }
 cout << "========================" << endl;
}

int main()
{
 vector<int> int_vec_a;

 // demo vector functionality
 int_vec_a.push_back(1);
 int_vec_a.push_back(2);
 int_vec_a.push_back(3);

 // print vector's size
 cout << "int_vec_a.size() = " << int_vec_a.size() << endl;

 // print vector's elements
 print(int_vec_a);

 // remove last element
 int_vec_a.pop_back();

 // print vector's size
 cout << "int_vec_a.size() = " << int_vec_a.size() << endl;

 // print vector's elements
 print(int_vec_a);

 // get first element
 cout << "int_vec_a.front() = " << int_vec_a.front() << endl;

 // get last element
 cout << "int_vec_a.back() = " << int_vec_a.back() << endl;

 // get element at index 1
 cout << "int_vec_a.at(1) = " << int_vec_a.at(1) << endl;

 // sort in ascending order
 sort(int_vec_a.begin(), int_vec_a.end());
 print(int_vec_a);

 // sort in descending order
 sort(int_vec_a.rbegin(), int_vec_a.rend());
 print(int_vec_a);

 return 0;
}
```

### sorting

#### bubble sort

- <https://www.hackerearth.com/practice/algorithms/sorting/bubble-sort/tutorial/> （算法）
- <https://www.hackerearth.com/practice/algorithms/sorting/bubble-sort/visualize/> （可视化）

#### selection sort

- 每一次循环：找最小的数目，并把最小的数目放到正确的位置
- <https://www.hackerearth.com/practice/algorithms/sorting/selection-sort/tutorial/> （算法）
- <https://www.hackerearth.com/practice/algorithms/sorting/selection-sort/visualize/> （可视化）

``` cpp
#include <iostream>
#include <cstdlib>
#include <algorithm>

using namespace std;

int main()
{
 const int N = 7;
 int arr[N] = {4, 1, 9, 2, 5, 7, 3};

 // selection sort
 for (int i = 0; i < N - 1; i++) // O(N)
 {
  int min = i;
  for (int j = i; j < N; j++) // O(N)
  {
   if (arr[j] < arr[min]) // O(1)
   {
    min = j;
   }
  }
  swap(arr[i], arr[min]);
 }

 // Print the array
 for (int i = 0; i < N; i++) // O(N)
 {
  cout << arr[i] << " "; // O(1)
 }
}
```

### search

#### linear search 线性（暴力）搜索

- <https://www.programiz.com/dsa/linear-search>

#### binary search 二分搜索

N = 16
16 elements O(1)
8 O(1)
4 O(1)
2 O(1)
1 O(1)

log2(N) = log2(16) = 4 (divide by 2 for 4 times)
logN

- <https://www.programiz.com/dsa/binary-search>
- <https://stackoverflow.com/questions/8185079/how-to-calculate-binary-search-complexity>
- array has to be sorted

``` cpp
// Binary Search in C++

#include <iostream>
using namespace std;

int binarySearch(int array[], int x, int low, int high)
{
 // Repeat until the pointers low and high meet each other
 while (low <= high) // O(logN)
 {
  // O(1)
  int mid = low + (high - low) / 2;

  if (array[mid] == x)
   return mid;

  if (array[mid] < x)
   low = mid + 1;

  else
   high = mid - 1;
 }

 return -1;
}

int main(void)
{
 int array[] = {3, 4, 5, 6, 7, 8, 9};
 int x = 4;
 int n = sizeof(array) / sizeof(array[0]);
 int result = binarySearch(array, x, 0, n - 1);
 if (result == -1)
  cout << "Not found";
 else
  cout << "Element is found at index " << result;
}
```

### （空间/时间）复杂度

- <https://www.freecodecamp.org/news/big-o-cheat-sheet-time-complexity-chart/>
- 设输入n条数据

#### 空间复杂度

- O(1)：算法所需存储空间和输入数据量不相关（如输入n条数据，但算法只使用了一个int变量，没有使用数组来存储n条数据)
- O(n): 算法把n条输入数据存储在空间为n的数组。
- O(n^2): 算法把n条输入数据存储在空间为n\*n的数组 (比如说这n条数据都是一个graph中的节点，彼此之间的连接关系可以用邻接矩阵来表示，这个矩阵占用n\*n的空间）。
- 以此类推。

#### 时间复杂度

- O(1)：算法并不遍历这n条数据（计算量和输入数据量不相关，比如说直接输出数组的最后一条数据），很少有这种情况。
- O(n)：算法遍历这n条数据1次（一层for/while循环）
- O(n^2): 算法遍历这n条数据n次（两层嵌套的for/while循环）
- 以此类推。
