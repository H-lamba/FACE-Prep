# Excel Sheet Column Title Converter

This project provides a C++ implementation to convert a given positive integer into its corresponding Excel column title.

## 🧩 Problem Description

In Microsoft Excel, columns are labeled alphabetically:
```

A → 1
B → 2
...
Z → 26
AA → 27
AB → 28
...

````

Given a column number, the task is to return its corresponding Excel column title.

### Example
| Input | Output |
|-------|--------|
| 1     | A      |
| 28    | AB     |
| 701   | ZY     |

## 🚀 How It Works

- The logic is similar to converting a number to base-26.
- Since Excel uses 1-indexed letters (A=1, not 0), we decrement the number by 1 before every modulus operation.
- The character is calculated by:  
  `char letter = 'A' + (columnNumber - 1) % 26`

## 🛠️ Code Overview

```cpp
std::string convertToTitle(int columnNumber) {
    std::string result;
    while (columnNumber > 0) {
        columnNumber--;
        int remainder = columnNumber % 26;
        char letter = 'A' + remainder;
        result += letter;
        columnNumber /= 26;
    }
    std::reverse(result.begin(), result.end());
    return result;
}
````

## 🧪 Sample Output

```cpp
Input: 1      → Output: A  
Input: 28     → Output: AB  
Input: 701    → Output: ZY  
Input: 2147483647 → Output: FXSHRXW  
```

