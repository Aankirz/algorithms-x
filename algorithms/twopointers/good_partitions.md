```C++
class Solution {
public:
    int numberOfGoodPartitions(vector<int>& nums) {
        unordered_map<int,int>freq;

        int lastDuplicate=0;

        for(int i=0;i<nums.size();++i){
            freq[nums[i]]++;
            if(freq[nums[i]]>1){
                lastDuplicate=i;
            }
        }
            
        return (int)pow(2,nums.size()-(lastDuplicate+1)-1)+1;
    }
};

```

### using pow
- Line 15: Char 21: runtime error: inf is outside the range of representable values of type 'int' (solution.cpp)
SUMMARY: UndefinedBehaviorSanitizer: undefined-behavior prog_joined.cpp:24:21
- The pow function returns a value of type `double`, which is used for floating-point calculations. When the result of `pow` is very large, attempting to cast it to int causes undefined behavior because the value exceeds the range of integers.

### using bitwise leftshifts

