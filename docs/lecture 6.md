## 上周回顾
- 指针
- 参考/引用

## 本周内容
### \<cstring>
- C-style字符串库
- https://cplusplus.com/reference/cstring/
- strlen()
- strcpy()

### \<string>
- c++ 字符串库
- https://cplusplus.com/reference/string/string/
- https://stackoverflow.com/questions/12824595/difference-between-cstring-and-string
- getline()
- at()
- str[]
- size() / length()
- assign() / =
- append() / +
- insert()
- erase()
- replace()
- find()
- find_first_of()
- substr()
- compare() / ==

- functions
	- https://cplusplus.com/reference/string/
	- stoi()
	- to_string()

### 三元运算符（ternary operator）
- if else 的精简版
```cpp
#include <iostream>

int32_t max(int32_t a, int32_t b) {
  if (a > b) {
    return a;
  } else {
    return b;
  }
}

int32_t max_ternary(int32_t a, int32_t b) {
	return a > b ? a : b
}

int main() {
  std::cout << max(1, 2) << "\n";
  std::cout << max(42, 7) << "\n";
  
  std::cout << max_ternary(1, 2) << "\n";
  std::cout << max_ternary(42, 7) << "\n";
}
```