[[C++]] has a system of smart [[Pointer]]s in its `<memory>` header, which allows for management of [[Heap Allocation|Dynamically allocated]] objects automatically, helping avoid [[Memory Leak]]s and [[Dangling Pointer]]s

# Comparison

| Smart Pointer | [[Ownership]]   | Copies Allowed | Overhead | Best For                                                         |
| ------------- | --------------- | -------------- | -------- | ---------------------------------------------------------------- |
| `unique_ptr`  | Exclusive       | No             | Low      | Sole ownership ([[Resource Aquisition is Initialization\|RAII]]) |
| `shared_ptr`  | Shared          | Yes            | Moderate | Shared ownership                                                 |
| `weak_ptr`    | None (observer) | Yes            | Low      | Breaking cycles / observing shared objects                       |

# unique_ptr
You want a resource that has exactly one owner, and you want it automatically deleted when that owner goes out of scope. 
It cannot be copied.
It can be moved.
```
std::unique_ptr<int> ptr = std::make_unique<int>(42);
// Transfer ownership
std::unique_ptr<int> ptr2 = std::move(ptr);
```
# shared_ptr
You need multiple parts of your program to share ownership of the same resource, and the resource should be freed when the **last owner** goes away.
It can be copied (because it can have multiple owners).
It can be moved.
Uses reference counting to decide when to free its memory.
# weak_ptr
You want to observe an object A managed by a `shared_ptr` without affecting object A's lifetime by observing it.
It can be copied.
It can be moved.
It prevents circular references in [[Graph]]s