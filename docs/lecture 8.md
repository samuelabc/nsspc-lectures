---
layout: default
title: lecture 8
nav_order: 8
---

# lecture 8
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

- 函数
- 递归

## 本周内容

### struct

- 作用：把多个数据集合在一起
- struct vs class
  - <https://stackoverflow.com/a/54596/10640344>
  - class能实现的功能struct也都能实现
  - struct 里的元素默认是public的
  - class 里的元素默认是private的
  - 选择建议
    - 仅仅要存取一些public数据时，用struct
    - 使用到private，protected数据和oop（面向对象编程）特性时，用class
- 宣告
- 初始化

```cpp
#include <string>
#include <iostream>

struct Point {
  float x, y, z;
};

struct Person {
  std::string name;
  int age;
  bool married;
};

int main() {
  Point origin{0, 0, 0};
  Point origin1;
  
  std::cout << origin.x << ", " << 
               origin.y << ", " << 
               origin.z << "\n";

  Point elsewhere{3.0f, 4.0f, 5.0f};
  std::cout << elsewhere.x << ", " << 
               elsewhere.y << ", " << 
               elsewhere.z << "\n";

  Person maria{"Maria", 42, true};
  std::cout << maria.name << ": " << maria.age << "\n";
  Person nushi{"Nushi", 12, false};
  std::cout << nushi.name << ": " << nushi.age << "\n";
}

```

- struct指针
- 存取
  - `(*ptr).feet`
  - `ptr->feet`

```cpp
#include <iostream>
using namespace std;

struct Distance {
    int feet;
    float inch;
};

int main() {
    Distance *ptr, d;

    ptr = &d;
    
    cout << "Enter feet: ";
    cin >> (*ptr).feet;
    cout << "Enter inch: ";
    cin >> (*ptr).inch;
 
    cout << "Displaying information." << endl;
    cout << "Distance = " << (*ptr).feet << " feet " << (*ptr).inch << " inches";

    return 0;
}

```

```cpp
#include <iostream>
using namespace std;

struct Distance {
    int feet;
    float inch;
};

Distance *my_sum(Distance *d)
{
 int f = d->feet;
 float i = d->inch;
 d->sum = f + i;
 return d;
}

int main() {
    Distance *ptr, d;

    ptr = &d;
    
    cout << "Enter feet: ";
    cin >> ptr->feet;
    cout << "Enter inch: ";
    cin >> ptr->inch;
 
    cout << "Displaying information." << endl;
    cout << "Distance = " << ptr->feet << " feet " << ptr->inch << " inches";

    return 0;
}

```

### define, const

- define
  - 全局
  - 没有数据类型
  - 在竞赛中常见，但是是不好的代码风格，写工程项目通常不会这样写
- const
  - 全局或局部
  - 有数据类型

```cpp
#define N 10
const int MAX 1000000
const double EPS 1e-8

// loops
#define FOR(i, a, b) for (int i = (a); i < (b); ++i)
#define F0R(i, a) FOR(i, 0, a)
#define ROF(i, a, b) for (int i = (b)-1; i >= (a); --i)
#define R0F(i, a) ROF(i, 0, a)
#define rep(a) F0R(_, a)
#define each(a, x) for (auto &a : x)
```

### 标准模板库 Standard Template Library(STL)

```cpp
#include <iostream>
#include <iomanip>

#include <cmath>

#include <cstring>
#include <string>

#include <algorithm>
#include <functional>

#include <utility>   // pair, make_pair
#include <vector>
#include <set>
#include <map>

using namespace std;


```

```cpp
#include <bits/stdc++.h>
```

### containers

- <https://cplusplus.com/reference/stl/>
- <https://hackingcpp.com/cpp/std/sequence_containers.html>
- <https://hackingcpp.com/cpp/std/associative_containers.html>
- <https://learn.microsoft.com/en-us/cpp/standard-library/stl-containers?view=msvc-170>

### pair

- <https://cplusplus.com/reference/utility/pair/>
- <https://cplusplus.com/reference/utility/pair/pair/>

```cpp
#include <utility>      // std::pair, std::make_pair
#include <string>       // std::string
#include <iostream>     // std::cout

int main () {
  std::pair <std::string,double> product1;                     // default constructor
  std::pair <std::string,double> product2 ("tomatoes",2.30);   // value init
  std::pair <std::string,double> product3 (product2);          // copy constructor

  product1 = std::make_pair(std::string("lightbulbs"),0.99);   // using make_pair (move)

  product2.first = "shoes";                  // the type of first is string
  product2.second = 39.90;                   // the type of second is double

  std::cout << "The price of " << product1.first << " is $" << product1.second << '\n';
  std::cout << "The price of " << product2.first << " is $" << product2.second << '\n';
  std::cout << "The price of " << product3.first << " is $" << product3.second << '\n';
  return 0;
}
```

### vector

- <https://cplusplus.com/reference/vector/vector/>
- <https://cplusplus.com/reference/vector/vector/vector/>

```cpp
#include <vector>
#include <iostream>

int main() {
  std::vector<int> vec{1, 2, 3};
  vec.push_back(4);

  std::cout << "vec.size(): " << vec.size() << "\n";
  std::cout << "vec[1]: " << vec[1] << "\n";

  vec.pop_back();
  for (auto n : vec) {
    std::cout << n << "\n";  
  }
}
```

### set

- <https://cplusplus.com/reference/set/set>
- <https://cplusplus.com/reference/set/set/set/>

```cpp
#include <set>
#include <string>
#include <iostream>

using std::string;

struct ShorterString {
  bool operator()(const string& a, const string& b) const {
    return a.size() <= b.size();
  }
};

int main() {
  std::set<string, ShorterString> tags{
    {"wild"},
    {"funny"},
    {"outgoing"},
    {"bashful"},
  };

  for (const auto& tag : tags) {
    std::cout << tag << "\n";
  }
}
```

### map

- <https://cplusplus.com/reference/map/map/>
- <https://cplusplus.com/reference/map/map/map/>

```cpp
#include <map>
#include <string>
#include <iostream>

using std::string;

struct ShorterString {
  bool operator()(const string& a, const string& b) const {
    return a.size() <= b.size();
  }
};

int main() {
  std::map<string, int, ShorterString> persons{
    {"Maria", 42},
    {"Nushi", 12},
    {"Mohammed", 25},
    {"Jose", 64}
  };

  for (const auto& [name, age] : persons) {
    std::cout << name << " is " << age << " years old.\n";
  }
}
```

### 小数位

- fixed
- setprecision
  - 不保证四舍五入

```cpp
// setprecision example
#include <iostream>     // std::cout, std::fixed
#include <iomanip>      // std::setprecision

int main () {
  double f =3.14159;
  std::cout << std::setprecision(5) << f << '\n'; //3.1416
  std::cout << std::setprecision(9) << f << '\n'; //3.14159
  std::cout << std::fixed;
  std::cout << std::setprecision(5) << f << '\n'; //3.14159
  std::cout << std::setprecision(9) << f << '\n'; //3.141590000

 
  return 0;
}
```

### 四舍五入

- round
- 手写round函数

```cpp
#include <iostream>
using namespace std;
float round(float var)
{
    // 37.66666 * 100 =3766.66
    // 3766.66 + .5 =3767.16    for rounding off value
    // then type cast to int so value is 3767
    // then divided by 100 so the value converted into 37.67
    float value = (int)(var * 100 + .5);
    return (float)value / 100;
}
 
int main()
{
    float var = 37.66666;
    cout << round(var);
    return 0;
}

```

- std的round

```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main()
{
    float var = 37.66666;
    cout << round(var * 100) / 100;
    return 0;
}
```

- setprecision vs round

```cpp
#include <iostream>
#include <cmath>
#include <iomanip>
#include <string>
#include <set>
#include <vector>
#include <algorithm>
#include <map>
using namespace std;

int main()
{
 float a = 123.34519;
 float b = 0.298475;

 cout << fixed << setprecision(5) << b << endl; // 0.2984749999999999903 => 0.29847
 cout << round(b * 100000) / 100000 << endl; // 0.2984749999999999903 => 0.29848
 return 0;
}
```
