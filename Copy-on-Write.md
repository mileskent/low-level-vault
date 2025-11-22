A strategy used to optimize the copying of resources.
Resources are [[Lazy|lazily]] copied. 
Only when a write is attempted is the resource copied. Up to that point, only reads have taken place, which do not effect the state of the resource.