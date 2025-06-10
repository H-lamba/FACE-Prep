# Reverse Words in a String - Stack Approach

## Overview
This C++ solution reverses the order of words in a given string using a stack data structure. The approach efficiently handles the word reversal while maintaining proper spacing between words.

## Approach
1. **Initialization**: 
   - Create an empty string `p` to build words character by character.
   - Initialize a stack `st` to store words in reverse order.

2. **Processing the Input String**:
   - Iterate through each character in the input string:
     - When a space is encountered, the current word in `p` is pushed onto the stack (if `p` is not empty), and `p` is reset.
     - For non-space characters, append them to `p` to build the current word.
   - After the loop, push any remaining word in `p` onto the stack (handles the last word in the string).

3. **Constructing the Reversed String**:
   - Pop words from the stack and append them to the result string `z`.
   - Add a space between words, except after the last word.

## Key Features
- **Efficient Word Handling**: Uses a stack to naturally reverse word order.
- **Space Management**: Properly handles multiple spaces by checking if `p` is non-empty before pushing.
- **Edge Cases**: Correctly processes strings with leading/trailing spaces and multiple spaces between words.

## Complexity Analysis
- **Time Complexity**: O(n), where n is the length of the input string. Each character is processed exactly twice (once when building words and once when constructing the result).
- **Space Complexity**: O(n), due to stack storage and the result string.

## Usage
```cpp
Solution sol;
string reversed = sol.reverseWords("the sky is blue");
// reversed will be "blue is sky the"
```

## Code
```cpp
#include <stack>
#include <string>
using namespace std;

class Solution {
public:
    string reverseWords(string s) {
        string p = "";
        stack<string> st;
        
        for(char i : s) {
            if(i == ' ') {
                if (!p.empty()) {  // Ensure we don't push empty strings
                    st.push(p);
                    p = "";
                }
            } else {
                p = p + i;
            }
        }
        
        // Push the last word if it exists
        if (!p.empty()) {
            st.push(p);
        }
        
        string z = "";
        while(!st.empty()) {
            z = z + st.top();
            st.pop();
            if(!st.empty()) {
                z = z + " ";
            }
        }
        
        return z;
    }
};
'''

