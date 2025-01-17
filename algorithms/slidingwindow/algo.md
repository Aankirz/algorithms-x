# sliding window
## intuition
- reusing partial results
- contiguity
- dynamic adjustment

## tips
- while loop increment
- 

## examples
### Ex1: Find the maximum sum of any subarray of size k.
```C++
int maxSubarraySum(vector<int>& nums, int k) {
    int n=nums.size();
    int maxSum=0,windowSum=0;

    for(int i=0;i<k;i++)
        windowSum+=nums[i];
    
    maxSum=windowSum;
    for(int i=k;i<nums.size();i++){
        windowSum+=nums[i]-nums[i-k];
        maxSum=max(windowSum,maxSum);
    }

    return maxSum;
}
```
### Ex2: Find the smallest subarray with a sum greater than or equal to target.
```C++
int minSubarrayLen(int target, vector<int>& nums) {
        int n=nums.size();
        int windowSum=0,start=0,minLength=INT_MAX;

        for(int end=0;end<nums.size();end++){
            windowSum+=nums[end];
            while(windowSum>=target){
                minLength=min(minLength,end-start+1);
                windowSum-=nums[start];
                start++;
            }
        }

        if(minLength==INT_MAX)
        return 0;

        return minLength;
}
```
### Ex3 Length Of Longest Substring
```C++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
       if(s.length()==1)
       return 1;

       unordered_map<char,int>freq;
       int start=0,window=0,len=0;

       for(int end=0;end<s.size();end++){
         freq[s[end]-'a']++;
         while(freq[s[end]-'a']>1){
            len=max(len,window);
            window--;
            freq[s[start]-'a']--;
            start++;
         }
         window++;
       }

       len=max(len,window);

       return len;
    }
};
```

