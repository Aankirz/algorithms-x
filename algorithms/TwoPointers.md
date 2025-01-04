## Two Pointers

- There's two pointers on two desired location
- Moving ahead when a desired condition meets
- Stops when the start > end

### **Understanding Two Pointers: The Crux of the Technique**

The **two pointers technique** is one of the most versatile tools in problem-solving. It is particularly useful for problems involving arrays, strings, or other sequential data structures. Let's dive deep into the **intuition, use cases, and implementation** of this approach.

---

### **1. What is the Two Pointers Technique?**

The **two pointers technique** involves using two indices (pointers) to traverse a data structure in a systematic and efficient way. The two pointers can either:

1. **Start at different positions**:
   - One pointer starts at the beginning, and the other at the end.
   - Common for problems involving sorting or searching, e.g., finding pairs that satisfy a condition.

2. **Move at different speeds**:
   - One pointer advances faster (e.g., skips elements) while the other moves slower.
   - Common for problems involving cycles, intervals, or comparisons.

---

### **2. Crux of the Technique**

#### Key Ideas:
1. **Efficient Traversal:**
   - Instead of brute-forcing all possible combinations, two pointers allow you to traverse the data in linear or near-linear time.
   - Example: Instead of \(O(n^2)\), many problems reduce to \(O(n)\) or \(O(n \log n)\).

2. **Dynamic Movement:**
   - The pointers move **dynamically** based on conditions, allowing you to discard irrelevant parts of the input.

3. **Divide and Conquer:**
   - The two pointers effectively divide the input into **smaller problems** to solve them in manageable steps.

---

### **3. Types of Two Pointers Problems**

#### **Type 1: Opposite Direction (Left and Right)**

**When to Use:**
- The data is sorted, or you want to leverage order for efficient traversal.
- Problems like finding pairs, palindromes, or satisfying constraints.

**Example: Two-Sum Problem in a Sorted Array**
- Input: `nums = [1, 2, 3, 4, 6], target = 6`
- Goal: Find two numbers that sum to `target`.

**Steps:**
1. Start two pointers:
   - Left pointer at the beginning.
   - Right pointer at the end.
2. Check the sum of the two pointers:
   - If the sum is smaller than the target, move the left pointer to the right.
   - If the sum is larger, move the right pointer to the left.
   - If the sum equals the target, return the pair.

---

#### **Type 2: Same Direction (Fast and Slow Pointers)**

**When to Use:**
- Problems involving cycles, intervals, or contiguous subarrays.
- Sliding window problems, finding duplicates, or removing elements.

**Example: Detecting a Cycle in a Linked List**
- Input: A linked list.
- Goal: Check if the list contains a cycle.

**Steps:**
1. Use two pointers:
   - **Slow pointer:** Moves one step at a time.
   - **Fast pointer:** Moves two steps at a time.
2. If there’s a cycle, the fast pointer will eventually meet the slow pointer.
3. If the fast pointer reaches the end, there’s no cycle.

---

#### **Type 3: Sliding Window**

**When to Use:**
- Problems requiring contiguous subarrays or substrings.
- Optimize the size, length, or sum of subarrays.

**Example: Longest Substring Without Repeating Characters**
- Input: `s = "abcabcbb"`
- Goal: Find the length of the longest substring without repeating characters.

**Steps:**
1. Use two pointers:
   - **Left pointer:** Marks the start of the sliding window.
   - **Right pointer:** Expands the window.
2. Use a hash set to track characters in the current window.
3. If a character is repeated, move the left pointer until the character is removed from the window.

---

### **4. Key Insights for Using Two Pointers**

#### **a) When to Move Which Pointer?**
- Left pointer moves when the current state becomes **invalid**.
- Right pointer moves to explore new possibilities or expand the range.

#### **b) Conditions for Movement**
- Use conditions to dynamically adjust the pointers:
  - **Sum-based problems:** Adjust pointers based on the target value.
  - **Substring problems:** Adjust pointers when constraints are violated.

#### **c) Avoid Overlapping**
- Ensure the pointers do not overlap unnecessarily unless the problem specifically allows it (e.g., palindromes).

---

### **5. Example Problem Walkthrough**

#### **Problem: Find All Pairs with a Target Sum**

**Input:**  
`nums = [1, 2, 3, 4, 6], target = 6`  
**Output:**  
Pairs: `(2, 4)`

**Approach:**
1. **Sort the array** (if unsorted).
2. Initialize two pointers:
   - Left pointer: `l = 0`.
   - Right pointer: `r = nums.size() - 1`.
3. Check the sum:
   - If `nums[l] + nums[r] == target`, record the pair.
   - If the sum is smaller, increment `l`.
   - If the sum is larger, decrement `r`.

**Complexity:**
- Time: \(O(n \log n)\) (sorting) + \(O(n)\) (two-pointer traversal).

---

#### **Problem: Longest Subarray with Sum ≤ k**

**Input:**  
`nums = [1, 2, 1, 0, 1, 1, 0], k = 4`  
**Output:**  
Length = 5

**Approach:**
1. Use two pointers:
   - Left pointer: Shrinks the window.
   - Right pointer: Expands the window.
2. Use a variable `currentSum` to track the sum of the window.
3. If `currentSum > k`, move the left pointer until the sum becomes valid.
4. Keep track of the maximum window size.

**Complexity:**
- Time: \(O(n)\).

---

### **6. Advantages of Two Pointers**

1. **Efficiency:**
   - Reduces brute force \(O(n^2)\) solutions to \(O(n)\) or \(O(n \log n)\).

2. **Space Optimization:**
   - No extra data structures are needed in many cases.

3. **Versatility:**
   - Works for a variety of problems (strings, arrays, linked lists).

---

### **7. Typical Patterns**

1. **Finding Pairs:**
   - Sum, difference, or product conditions.

2. **Substring Problems:**
   - Longest/shortest substring with constraints.

3. **Cycle Detection:**
   - Linked lists or graphs.

4. **Partitioning Problems:**
   - Splitting arrays into parts with specific properties.

---

### **8. Common Pitfalls**

1. **Infinite Loops:**
   - Ensure both pointers move under valid conditions.

2. **Edge Cases:**
   - Single-element arrays, duplicates, or empty inputs.

3. **Boundary Conditions:**
   - Ensure pointers do not go out of bounds.

---