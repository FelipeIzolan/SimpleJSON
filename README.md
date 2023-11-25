# SimpleJSON
Simple C++ JSON library

## License
Do what the fuck you want public license

## About
SimpleJSON is a lightweight JSON library for exporting data in JSON format from C++. By taking advantage of templates and operator overloading on the backend, you're able to create and work with JSON objects right away, just as you would expect from a language such as JavaScript. SimpleJSON is a single C++ Header file, "json.hpp". Feel free to download this file on its own, and include it in your project. No other requirements!

#### Platforms
SimpleJSON should work on any platform; it's only requirement is a C++11 compatible compiler, as it make heavy use of the C++11 move semantics, and variadic templates. The tests are tailored for linux, but could be ported to any platform with python support and a C++11 compiler.

## API
You can find the API [over here](API.md). For now it's just a Markdown file with C++ syntax highlighting, but it's better than nothing!

## Fork

First Thanks To The Creator [nbsdx](https://github.com/nbsdx)!

- Fix - Convert numbers to stoll() & stold(), because JavaScript use 64-bit Floating Point.
- Update - Undefined, now stringify ignore The "undefined" value.

## Example
More examples can be found in the 'examples' directory. Check out [the API](API.md) for a full list of functions.

```cpp
#include "json.hpp"

int main() {
  json::JSON obj;
  // Create a new Array as a field of an Object.
  obj["array"] = json::Array( true, "Two", 3, 4.0 );
  // Create a new Object as a field of another Object.
  obj["obj"] = json::Object();
  // Assign to one of the inner object's fields
  obj["obj"]["inner"] = "Inside";
  
  // We don't need to specify the type of the JSON object:
  obj["new"]["some"]["deep"]["key"] = "Value";
  obj["array2"].append( false, "three" );
  
  // We can also parse a string into a JSON object:
  obj["parsed"] = JSON::Load( "[ { \"Key\" : \"Value\" }, false ]" );
  
  std::cout << obj << std::endl;
}
```
Output:
``` 
{
  "array" : [true, "Two", 3, 4.000000],
  "array2" : [false, "three"],
  "new" : {
    "some" : {
      "deep" : {
        "key" : "Value"
      }
    }
  },
  "obj" : {
    "inner" : "Inside"
  },
  "parsed" : [{
      "Key" : "Value"
    }, false]
}
```

This example can also be written another way:
```cpp
#include "json.hpp"
#include <iostream>

using json::JSON;

int main() {
    JSON obj = {
        "array", json::Array( true, "Two", 3, 4.0 ),
        "obj", {
            "inner", "Inside"
        },
        "new", { 
            "some", { 
                "deep", { 
                    "key", "Value" 
                } 
            } 
        },
        "array2", json::Array( false, "three" )
    };

    std::cout << obj << std::endl;
```
Sadly, we don't have access to the : character in C++, so we can't use that to seperate key-value pairs, but by using commas, we can achieve a very similar effect. The other point you might notice, is that we have to explictly create arrays. This is a limitation of C++'s operator overloading rules, so we can't use the [] operator to define the array :( I'm looking into ways to make this smoother.
