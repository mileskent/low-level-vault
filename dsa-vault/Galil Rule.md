* Just like [[Knuth-Morris-Pratt]], after finding a match, shift by $m - \text{failTable}(m - 1)$
* An optimization for [[Boyer-Moore]] that doesn't appear in the simplified version of the algorithm explained in [[Boyer-Moore|the simplified entry]]
* Pretty much steals the idea not rechecking characters that we've already checked against the text from [[Knuth-Morris-Pratt]], due to a cyclical pattern

The Galil rule applies only right after finding the pattern
* Old plan after match: shift 1
* New plan with Galil Rule After match:
	* Shift equal to *period* of pattern
### How to Algorithmically Find the Period
Steal FailureTable from [[Knuth-Morris-Pratt]], but only save its last entry.
*The period is the length of the pattern minus the last entry of the failure table*