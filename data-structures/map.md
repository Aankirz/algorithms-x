### **Map**
- **Purpose**: A `map` is a key-value pair data structure that maps keys to values.
- **Types**:
  - `std::map` (ordered map)
  - `std::unordered_map` (hash-based map)

#### **Key Features of Map**
1. **Key-Value Pair**:
   - Each key in the map is unique.
   - The value associated with the key can be changed, but the key remains unique.
2. **Ordering**:
   - `std::map`: Keys are stored in ascending order.
   - `std::unordered_map`: No specific order; keys are stored in a hash table.
3. **Underlying Structure**:
   - `std::map`: Implemented as a self-balancing binary search tree (usually a Red-Black Tree).
   - `std::unordered_map`: Implemented as a hash table.
4. **Operations**:
   - Insertion, deletion, and search in `std::map` take **O(log n)**.
   - Insertion, deletion, and search in `std::unordered_map` take **O(1)** on average.

#### **When to Use Map**
- When you need to associate values with keys.
- When order of keys matters, use `std::map`.
- When order doesn’t matter, use `std::unordered_map`.

---

### **Comparison: Set vs Map**

| Feature             | **Set**                              | **Map**                               |
|---------------------|--------------------------------------|---------------------------------------|
| **Data Structure**  | Collection of unique elements.       | Collection of key-value pairs.        |
| **Uniqueness**      | Elements must be unique.             | Keys must be unique; values can repeat. |
| **Ordering**        | Ordered (`set`) or unordered (`unordered_set`). | Ordered (`map`) or unordered (`unordered_map`). |
| **Storage**         | Stores only elements.                | Stores keys and associated values.    |
| **Use Case**        | For checking existence of elements or uniqueness. | For associating data with unique keys. |
| **Time Complexity** | O(log n) for `set`, O(1) for `unordered_set`. | O(log n) for `map`, O(1) for `unordered_map`. |

---

### **Example Usage**

#### Using `map`:
```cpp
#include <map>
#include <iostream>
using namespace std;

int main() {
    map<int, string> m;
    m[1] = "Apple";
    m[2] = "Banana";
    m[1] = "Orange"; // Updates value for key 1.

    for (auto &[key, value] : m)
        cout << key << " -> " << value << endl;
    // Output: 1 -> Orange
    //         2 -> Banana
    return 0;
}
```

---

### **Key Points to Remember**
1. Use `set`/`unordered_set` for unique elements.
2. Use `map`/`unordered_map` for key-value relationships.
3. Prefer `unordered_set`/`unordered_map` for better performance when ordering is not required.
4. For large datasets, avoid `std::set`/`std::map` unless ordering is crucial.