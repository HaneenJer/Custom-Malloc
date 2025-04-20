# Custom-Malloc
Building malloc from the ground up — a hands-on dive into memory management in C++.

## 📦 Implementations

1. **Naïve Malloc (malloc_1.cpp)**

   The first implementation (`smalloc`) is a minimal version of malloc that directly requests memory from the operating system using `sbrk`.

   ### Features:
   - Allocates memory blocks of arbitrary size (up to 108 MB).
   - Performs basic validation checks:
     - Returns `nullptr` if size is 0 or exceeds the maximum threshold.
     - Returns `nullptr` if `sbrk` fails.
   - Does not reuse memory or manage fragmentation.
   - Does not support freeing or coalescing blocks.

   ### Limitations:
   - No metadata is stored with the allocation.
   - Allocations cannot be freed or reused, causing memory fragmentation.
   - Each allocation simply extends the heap by the requested size, potentially leading to inefficient memory usage.

   ### Usage Example:
   ```cpp
   void* ptr = smalloc(1024); // Allocate 1KB
   if (!ptr) {
       std::cerr << "Allocation failed" << std::endl;
   }
