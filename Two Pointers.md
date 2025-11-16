The idea of this technique, in the example of two sum, for example, on a sorted array, is to start two pointers at the minimum and maximum of the array. When the current sum is too large, we shift the right pointer left, which will increase the sum. When the current sum is too small, we shift the left pointer right, which will increase the sum. 

O(n) time and O(1) space

Initialize: left = 0, right = n - 1  
Run a loop while left < right, do the following inside the loop
- Compute current sum, sum = arr\[left\] + arr\[right\]
- If the sum equals the target, we’ve found the pair.
- If the sum is less than the target, move the left pointer to the right to increase the sum.
- If the sum is greater than the target, move the right pointer to the left to decrease the sum.