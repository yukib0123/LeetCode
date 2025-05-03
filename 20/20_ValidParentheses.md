```C++
class Solution {
public:
    bool isValid(string s) {
        stack<char> st;
        for (char c : s) {
            if (!st.empty() &&
                ((st.top() == '(' && c == ')') ||
                (st.top() == '[' && c == ']') || 
                (st.top() == '{' && c == '}'))
                ) st.pop();
            else st.push(c);
        }
        return st.empty();
    }
};
```

有効でないと分かった瞬間にreturn falseを返すと実行時間が短くなった
```C++
class Solution {
public:
    bool isValid(string s) {
        stack<char> st;
        for (char c : s) {
            if (!st.empty() &&
                ((st.top() == '(' && c == ')') ||
                (st.top() == '[' && c == ']') || 
                (st.top() == '{' && c == '}'))
                ) st.pop();
            else if (c == '(' || c == '[' || c == '{') st.push(c);
            else return false;
        }
        return st.empty();
    }
};
```
