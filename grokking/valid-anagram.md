# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

# Approach
<!-- Describe your approach to solving the problem. -->
Key: Comparing Freq

# Complexity
- Time complexity: O(N)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
constant storage **vector** size is fixed at 26

# Code
## Solution 1
```cpp []
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.length() != t.length())
        return false;

        vector<pair<int,int>> freq(26,{0,0});

        for(int i=0;i<s.length();++i){
            if(isalpha(s[i]))
            freq[s[i]-'a'].first++;
        }

        for(int i=0;i<t.length();++i){
            if(isalpha(t[i]))
            freq[t[i]-'a'].second++;
        }

        for(int i=0;i<freq.size();i++){
            if(freq[i].first!=freq[i].second)
            return false;
        }

        return true;
    }
};
```

## Solution 2
```cpp []
class Solution {
public:
    bool isAnagram(string s, string t) {
        sort(s.begin(), s.end());
        sort(t.begin(), t.end());
        return s == t;
    }
};
```

## Solution 3
```cpp []
class Solution {
public:
    bool isAnagram(string s, string t) {
        unordered_map<char, int> count;
        
        // Count the frequency of characters in string s
        for (auto x : s) {
            count[x]++;
        }
        
        // Decrement the frequency of characters in string t
        for (auto x : t) {
            count[x]--;
        }
        
        // Check if any character has non-zero frequency
        for (auto x : count) {
            if (x.second != 0) {
                return false;
            }
        }
        
        return true;
    }
};
```