In [[C++]], Move Semantics are an approach to transmitting data between functions by transferring ownership.

Approaches to transmitting data between functions:
* One approach is to copy. Copying can be slow and may result in [[Heap Allocation]] like with a vector.
* One approach is to use [[C++ Reference|References]], which avoids copying through direct access
* One approach is to Move, which avoids copying by transferring ownership of resources

# Move Constructor
An object that uses move semantics has a constructor that takes in an [[C++ Value Categories#rvalue reference]] as a parameter, and handles moving the resources of the object from the old object to the new one, and also zeroing the members of the old object. Zeroing the old object's members prevents its deconstructor from freeing the resources it used to own.
```
Object (Object && other) { ... }
```

# Move Assignment Operator
The move assignment operator uses `=`
It will only be invoked if the `=` operator is used AND the assigned value is an [[C++ Value Categories#rvalue reference]]
Does nothing if moving an object into itself
Frees memory of old object.
Copies the other members.
Only gets called when we assign a variable into an existing variable
```
Object& operator=(Object && other) { ... }
```
# std::move
The [[#Move Constructor]] takes an [[C++ Value Categories#rvalue reference]], so in order to make sure this constuctor is invoked (as opposed to the copy constructor) we have to cast the value we are assigning that we wish to move to an rvalue reference. `std::move` handles this for us at compile time.
```
Object newObj(std::move(ogObj));
/* OR */
Object newObj = std::move(ogObj);
```
