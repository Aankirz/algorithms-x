## 3Sum Approach

---

### 1. **Understand the Problem**
   - You're looking for **triplets** (three distinct indices) such that the sum of the three numbers is zero.
   - The result must not include **duplicate triplets**.

   **Key Observations:**
   - Sorting the array can help identify duplicates and reduce complexity.
   - The problem can be thought of as finding pairs that sum to a target (-nums[i]) for every element nums[i].

---

### 2. **Break the Problem into Smaller Steps**
   - **Sort the Array**: Sorting simplifies handling duplicates and allows the use of two-pointer techniques.
   - **Fix One Element**: For each number `nums[i]`, fix it as the first element in the triplet.
   - **Find the Remaining Two Elements**: Use the **two-pointer technique** to find two numbers that sum up to `-nums[i]`.

---

### 3. **Key Edge Cases**
   - All elements are zeros, e.g., `[0, 0, 0]`.
   - Arrays with no valid triplets, e.g., `[0, 1, 1]`.
   - Arrays with duplicates, e.g., `[-1, -1, 2, 2, 0]`.

---

### 4. **Efficient Approach**
   - **Step 1**: Sort the array. This allows you to:
     - Efficiently skip duplicate numbers.
     - Use the two-pointer technique.
   - **Step 2**: For each `nums[i]`:
     - If `nums[i]` is the same as the previous number, skip to avoid duplicates.
     - Use two pointers (`left` and `right`) to find pairs that sum up to `-nums[i]`.
   - **Step 3**: Adjust pointers:
     - If the sum is less than `0`, increment `left`.
     - If the sum is greater than `0`, decrement `right`.
   - **Step 4**: Add valid triplets to the result and ensure no duplicates by skipping adjacent duplicate numbers.

---

### 5. **Reasoning Behind Two-Pointer Technique**
   - Sorting helps you reduce the number of checks by working with a predictable sequence.
   - Using two pointers minimizes the complexity of finding pairs, reducing the time from \(O(n^2)\) (brute force for pairs) to \(O(n)\) per iteration of the outer loop.

---

### 6. **Complexity**
   - Sorting: \(O(n \log n)\).
   - Two-pointer search for each fixed element: \(O(n)\).
   - Overall: \(O(n^2)\), which is efficient for constraints.

```C++
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        sort(nums.begin(), nums.end());

        vector<vector<int>> ans;

        // Fix one element and use two-pointer technique
        for (int i = 0; i < nums.size(); ++i) {
            // Skip duplicates for the first element
            if (i > 0 && nums[i] == nums[i - 1])
                continue;

            int s = i + 1; // Start after the fixed element
            int e = nums.size() - 1;

            while (s < e) {
                int sum = nums[i] + nums[s] + nums[e];
                if (sum == 0) {
                    ans.push_back({nums[i], nums[s], nums[e]});
                    
                    // Skip duplicates for the second and third elements
                    while (s < e && nums[s] == nums[s + 1]) s++;
                    while (s < e && nums[e] == nums[e - 1]) e--;

                    s++;
                    e--;
                } else if (sum < 0) {
                    s++;
                } else {
                    e--;
                }
            }
        }

        return ans;
    }
};
```