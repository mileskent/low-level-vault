A [[Map]] that uses hashes for its functionality.
### Implementations
###### Remove
```
V remove(Key key) {
    int hashIndex = Math.abs(key.hashCode() % table.length);
    for (int i = 0; i < table.length; ++i) {
        int currentIndex = (hashIndex + i) % table.length;
        Entry entry = table[currentIndex];
        if (entry == null) break;
        if (!entry.removed && entry.key == key) {
            entry.removed = true;
            --this.size;
            return entry.value;
        }
    }
    throw exception "Key is not in the map!"
}

```