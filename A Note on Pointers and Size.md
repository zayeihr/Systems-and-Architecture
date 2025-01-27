# Why `.size` Doesn't Work for Arrays in C

In C, **arrays do not store their size as part of their structure**. Unlike higher-level languages (e.g., Python, Java, or C++), where objects like arrays or vectors have built-in properties like `.size`, C arrays are just **blocks of contiguous memory** without metadata.

## Key Reasons Why `.size` Doesn't Work
1. **No Metadata**:
   - When an array is declared in C, only the memory for its elements is allocated. The size of the array is not stored anywhere in memory.
   - Example:
     ```c
     int myArray[5] = {1, 2, 3, 4, 5};
     ```
     Here, `myArray` is just a pointer to the first element of the array in memory. The compiler does not attach size information to `myArray`.

2. **Arrays Decay into Pointers**:
   - When you pass an array to a function, it "decays" into a pointer to its first element. The size information is lost entirely during the function call.
   - Example:
     ```c
     void printArray(int arr[]) {
         // Can't determine the size of the array here
     }
     ```

---

## Why Use Zero-Delimiters?

The **zero-delimiter technique** is a way to determine the "end" of an array when the size isn't explicitly known. It's commonly used in C for character strings (`char` arrays) and other dynamically sized arrays.

1. **Fixed End Marker**:
   - A zero-delimited array has a special value (e.g., `0`) as the last element to indicate the end of the array.
   - This is similar to how C strings are terminated with a `'\0'`.

2. **Efficient Traversal**:
   - By checking for the zero-delimiter, you can iterate through the array without needing its size.
   - Example:
     ```c
     int arrayForFinding[] = {7, 8, 13, 19, 3, 0}; // Zero-terminated
     for (int i = 0; arrayForFinding[i] != 0; i++) {
         printf("%d\n", arrayForFinding[i]);
     }
     ```

3. **Dynamic Arrays**:
   - The zero-delimiter method is especially useful for arrays where the size can vary or isn't known at compile time.

---

## How to Handle Array Sizes in C

If you know the size of the array at compile time, you can:

### 1. Use `sizeof` to Calculate Size
   ```c
   int myArray[] = {7, 8, 13, 19, 3};
   int arraySize = sizeof(myArray) / sizeof(myArray[0]);
