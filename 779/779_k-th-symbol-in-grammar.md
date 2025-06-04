```C++
class Solution {
public:
    int kthGrammar(int n, int k) {
        if (n == 1 || n == 2) return k - 1; 
        // int d = 1;
        // for (int i = 0; i < n - 2; i++) d *= 2;
        int d = 1 << (n - 2);
        // if (k > d) return kthGrammar(n - 1, (k - 1) % d + 1) ^ 1; // 1-indexに注意して1~dに調整
        if (k > d) return kthGrammar(n - 1, k - d) ^ 1; 
        else return kthGrammar(n - 1, k);
    }
};
```
