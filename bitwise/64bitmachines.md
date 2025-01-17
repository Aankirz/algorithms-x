## 32bit vs 64bit
- The "word size" of a computer refers to the size of the data it can process in one go. Most modern systems have a word size of 32 bits or 64 bits.

##### Historical context
- Early C/C++ standards specified that int should be "at least 16 bits" but left the exact size to the implementation. With the widespread adoption of 32-bit processors in the 1980s and 1990s, int became standardized as 32 bits on most systems.

##### Backward compatibility
- Even on modern 64-bit systems, int often remains 32 bits for backward compatibility with older codebases.

##### Variation across systems
- The size of an int isn't always 32 bits—it depends on the system and compiler:
  - On some embedded systems, an int might be 16 bits.
  - On some 64-bit systems, int is still 32 bits, but long might be 64 bits.

#### The int Type Is Not Tied to Machine Word Size
- The size of an int is determined by the compiler and language specification, not strictly by the machine's word size.
- Most 64-bit systems maintain int as 32 bits for compatibility with existing codebases and to align with language standards.

####  How to Use 64-bit Integers
If you need the larger range on a 64-bit system, you can explicitly use types like long long in C/C++ or int64_t from <stdint.h>:

### What About size_t or Pointer Types?
On 64-bit systems, types like size_t or pointers (void*) are typically 64 bits. These are used to take full advantage of the system's 64-bit address space.

```
To check int size: sizeof(int);
```  
