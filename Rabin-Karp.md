A [[Pattern Matching Algorithm]] that focuses on improving the brute force algorithm by adding a "screening" step to decide if we should do a brute force comparison or not between the pattern and text window. This is accomplished by comparing hashes of the pattern and the text mask. In particular, the algorithm uses a very robust hash function known as the **Rabin Fingerprint rolling hash**, which can efficiently update the hash along the text as the window moves along. It is similar to [[LSD Radix Sort]] because it takes a unique math-based approach.
* Always shifts by one, but beats [[Brute Force Pattern Matching]] by knowing how to check if a certain text mask matches the pattern in a more efficient way---through hashing.
### Ideal Use Case
* Best Space usage
	* One major advantage of Rabin-Karp is that it uses O(1) auxiliary storage space, which is great if the pattern string you're looking for is very large.
* Finding multiple pattern matches in a large text, i.e. plagiarism detector

### Analysis
n = len(text)
m = len(pattern)
Best Case: fail as much as possible -> Hash of pattern never mayches hash of text
hash of pattern -> O(m), intitial hash -> O(m), roll hash -> O(n) * O(1) = O(n)
Worst Case: never fail -> all hashes match pattern, e.g. bad hash like $h = 42$ or text = "aaaaaa...", pattern = "aaa"

|                  | Best Case  | Worst Case |
| ---------------- | ---------- | ---------- |
| No occurrences   | $O(m + n)$ | $O(mn)$    |
| Single occurence | $O(m)$     | $O(mn)$    |
| All Occurences   | $O(m + n)$ | $O(mn)$    |
### Auxiliary Space Complexity
Constant -> store pattern hash 
(vs O(m) for [[Knuth-Morris-Pratt]], [[Boyer-Moore]])
### Rabin Fingerprint Rolling hash
Rolling the hash makes this algorithm viable, as we dont have to calculate the hash for each mask from scratch, but instead just calculate the next hashcode from the previous one in constant time.
* Calculate first hash normally
* Calculate all subsequent hashes from previous hashes; **Rolling Hash**
	* In a simple example $h(\text{args}) = \sum \text{args}$, so for $h(a, b, c) \rightarrow h(b, c, d)$,  $h(b, c, d) = h(a, b, c) - a + d$
		* This is a obviously a bad hash function though
##### Initial Hash
* Select base $B$, which is a large prime number
* Convert hash 1 by converting the first mask in the text into base $B$
	* e.g. $h(\text{"dog"}) = \text{d} \cdot B^2 + \text{o} \cdot B^1 + \text{g} \cdot B^0$
	* each letter has a function to convert it into a integer, e.g. ascii value
##### Rolling Hash
$$
\text{newHash} = (\text{oldHash} - \text{oldFirstLetter} \cdot B^{m - 1}) \cdot B + \text{newLastLetter}
$$
* $O(1)$ to update hash!
* Implicit limit to size due to nature of 2's complement integers, i.e. overflow is a feature
### Pseudocode
```
rk(pattern, text) -> list {
	n = text.len, m = pattern.len
	match = []
	
	phash = hash(pattern)
	thashes = new int[n - m + 1], thashes[0] = hash( text[0:m) )
	for si in [1, n - m] thashes[si] = {
		rollinghash(text[si-1], text[si+m-1], thashes[si-1])
	}

	for enum (i,hash) in thashes {
		if phash == hash {
			check if theyre actually the same -> matching
			if (matching) match.add(i)
		}
	}
	return match
}

hash(str) {
	result = 0, slen = str.len
	for i in [0, slen) { result += str[slen - 1 - i] * B**i }
	return result
}

int rollinghash(char oldFstLet, char newLstLet, int oldHash) {
	return (oldHash - oldFirstLetter * B**(m - 1)) * BASE + newLastLetter;
}

```