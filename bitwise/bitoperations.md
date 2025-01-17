# Bit Operations

## **AND Operation**
The **AND** operation `x & y` produces a number that has one bits in positions where both `x` and `y` have one bits. 

For example:
```
22 & 26 = 18
10110 (22)
& 11010 (26)
= 10010 (18)
```

Using the **AND** operation:
- We can check if a number `x` is even because `x & 1 = 0` if `x` is even, and `x & 1 = 1` if `x` is odd.
- More generally, `x` is divisible by `2^k` exactly when `x & (2^k - 1) = 0`.

---

## **OR Operation**
The **OR** operation `x | y` produces a number that has one bits in positions where at least one of `x` or `y` have one bits.

For example:
```
22 | 26 = 30
10110 (22)
| 11010 (26)
= 11110 (30)
```

---

## **XOR Operation**
The **XOR** operation `x ^ y` produces a number that has one bits in positions where exactly one of `x` or `y` have one bits.
(Same Bits op: 0)

For example:
```
22 ^ 26 = 12
10110 (22)
^ 11010 (26)
= 01100 (12)
```

---

## **NOT Operation**
The **NOT** operation `~x` produces a number where all the bits of `x` have been inverted.

- Formula: `~x = -x - 1`.
- For example: `~29 = -30`.

### Example:
If the numbers are 32-bit `int`, the result is as follows:
```
x =  29  => 00000000000000000000000000011101
~x = -30 => 11111111111111111111111111100010
```

---

## **Bit Shifts**

### Left Shift
The left shift `x << k` appends `k` zero bits to the number. It corresponds to multiplying `x` by `2^k`.

Example:
```
14 << 2 = 56
14 (1110) becomes 111000 (56)
```

### Right Shift
The right shift `x >> k` removes the last `k` bits of the number. It corresponds to dividing `x` by `2^k` rounded down to an integer.

Example:
```
49 >> 3 = 6
49 (110001) becomes 110 (6)
```

---

## **Applications**

- A number of the form `1 << k` has a one bit in position `k` and all other bits are zero. We can use such numbers to access single bits of other numbers.
- To check if the `k-th` bit of a number `x` is one:
  ```cpp
  if (x & (1 << k)) {
      // k-th bit is one
  }
  ```

### Example: Print the Binary Representation of an Integer
```cpp
for (int i = 31; i >= 0; i--) {
    if (x & (1 << i)) 
        cout << "1";
    else 
        cout << "0";
}
```

---

### Modifying Single Bits
- **Set the k-th bit to 1**:
  ```cpp
  x = x | (1 << k);
  ```
- **Set the k-th bit to 0**:
  ```cpp
  x = x & ~(1 << k);
  ```
- **Toggle the k-th bit**:
  ```cpp
  x = x ^ (1 << k);
  ```

---

### Special Bit Tricks
- **Clear the Last One Bit**: 
  ```cpp
  x = x & (x - 1);
  ```
  This sets the last one bit of `x` to zero.
  
- **Check if `x` is a Power of 2**:
  A positive number `x` is a power of 2 exactly when:
  ```cpp
  x & (x - 1) == 0
  ```