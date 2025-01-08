A method for representing [[Fractional Binary]] values.

The problem with generic [[Fractional Binary]] values: NASA wants to measure planetary distances, GTRI wants to measure atomic collisions. Where does fraction component start?
Hence [[IEEE 754]], [[IEEE 754 Double]]

[[Floating Point]] breaks the associative property sometimes, when mixing very large and very small numbers.
Also, casting integers to a float doesn't always preserve value, due to differences in precision. Using [[IEEE 754 Double]], usually prevents this.