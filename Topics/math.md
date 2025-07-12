# Topic Name: ➗ Math

### Important Terminologies:
- GCD/LCM: Greatest Common Divisor / Least Common Multiple.
- Modulo Arithmetic: Useful for large number operations.
- Prime Number: Number divisible only by 1 and itself.

### Time Complexity:
- Varies. Euclidean GCD is O(log min(a, b)).
- Sieve of Eratosthenes is O(n log log n).

### Less Known but Important Points:
- (a * b) % c = ((a % c) * (b % c)) % c
- Use fast exponentiation for power mod.
- Overflow risk with large factorials.

### Edge Cases to Consider:
- Zero and one.
- Negative numbers.
- Precision for floats.

### Common Coding Interview Patterns:
- Sieve for prime generation.
- GCD for array operations.
- Power mod / inverse mod.

### Relevant LeetCode Problems:
- [Greatest Common Divisor of Strings](https://leetcode.com/problems/greatest-common-divisor-of-strings/) (LC #1071)
- [Count Primes](https://leetcode.com/problems/count-primes/) (LC #204)
- [Pow(x, n)](https://leetcode.com/problems/powx-n/) (LC #50)

### Links to Important Resources:
- [GCD and LCM](https://www.geeksforgeeks.org/gcd-in-python/)
- [Sieve of Eratosthenes](https://www.geeksforgeeks.org/sieve-of-eratosthenes/)
- [Modular Arithmetic](https://cp-algorithms.com/algebra/module-inverse.html)