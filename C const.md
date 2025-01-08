
| Declaration       | What is mutable?             | Use Case                         |
| ----------------- | ---------------------------- | -------------------------------- |
| `char* const ptr` | The data pointed to (`*ptr`) | Fixed pointer to modifiable data |
| `const char* ptr` | The pointer (`ptr`)          | Pointer to read-only data        |
From [[C Variable Management]]  "from inside, go right if you can, left if you must". This will tell you that the first statement has a constant pointer and mutable data, while the second statement has a mutable pointer with constant data.