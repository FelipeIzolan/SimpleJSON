# json.hpp
json.hpp | C++ JSON library

```cpp
#include "json.hpp"

int main() {
  json::JSON my = json::JSON::Load("{\"test\": true,\"num\": [443,1,2]}");

  std::cout << my["test"] << std::endl;  
  std::cout << my["num"][0] << std::endl;
  std::cout << my["num"][1] << std::endl;
  std::cout << my["num"][2] << std::endl;
  std::cout << my["noexist"] << std::endl;
  
  return 1;
}
```
[examples](https://github.com/FelipeIzolan/json.hpp/tree/master/examples)

## 🍴 Fork

First thanks to the creator [nbsdx](https://github.com/nbsdx)!

- Fix - Convert numbers to stoll() & stold(), because JavaScript use 64-bit Floating Point.
- Update - Undefined, now stringify ignore The "undefined" value.

## 📜 License

- [json.hpp](./) - The Unlicensed
