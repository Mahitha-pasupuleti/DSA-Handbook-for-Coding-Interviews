# Mathematical Algorithms and Concepts ➗

## Introduction
Mathematical algorithms form the foundation of many computer science problems. Understanding these concepts is crucial for solving problems efficiently and handling numerical computations correctly.

## Core Concepts

### Important Terminologies
- **GCD**: Greatest Common Divisor
- **LCM**: Least Common Multiple
- **Prime Number**: Number divisible only by 1 and itself
- **Modulo**: Remainder after division
- **Factorial**: Product of all positive integers ≤ n
- **Fibonacci**: Sequence where each number is sum of previous two
- **Permutation**: Arrangement of items
- **Combination**: Selection of items
- **Exponentiation**: Power operation
- **Divisor**: Number that divides another number exactly

### Mathematical Properties
1. **Number Theory**:
   - Divisibility rules
   - Prime factorization
   - Modular arithmetic
2. **Combinatorics**:
   - Permutations
   - Combinations
   - Pascal's triangle
3. **Series and Sequences**:
   - Arithmetic
   - Geometric
   - Fibonacci

### Time Complexity Analysis
| Operation               | Time Complexity    | Space Complexity |
|------------------------|-------------------|------------------|
| GCD (Euclidean)        | O(log min(a,b))   | O(1)            |
| Prime Check            | O(√n)             | O(1)            |
| Sieve of Eratosthenes | O(n log log n)    | O(n)            |
| Fast Exponentiation   | O(log n)          | O(1)            |
| Prime Factorization   | O(√n)             | O(log n)        |
| Factorial             | O(n)              | O(1)            |
| Fibonacci (Matrix)    | O(log n)          | O(1)            |

## Implementation Patterns

### 1. GCD and LCM
```python
def gcd(a: int, b: int) -> int:
    while b:
        a, b = b, a % b
    return a

def lcm(a: int, b: int) -> int:
    return abs(a * b) // gcd(a, b)

def extended_gcd(a: int, b: int) -> tuple:
    """Returns (gcd, x, y) where ax + by = gcd"""
    if a == 0:
        return b, 0, 1
    
    gcd, x1, y1 = extended_gcd(b % a, a)
    x = y1 - (b // a) * x1
    y = x1
    
    return gcd, x, y
```

### 2. Prime Numbers
```python
def is_prime(n: int) -> bool:
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True

def sieve_of_eratosthenes(n: int) -> List[int]:
    """Generate all primes up to n"""
    sieve = [True] * (n + 1)
    sieve[0] = sieve[1] = False
    
    for i in range(2, int(n ** 0.5) + 1):
        if sieve[i]:
            for j in range(i * i, n + 1, i):
                sieve[j] = False
    
    return [i for i in range(n + 1) if sieve[i]]

def prime_factors(n: int) -> List[int]:
    factors = []
    d = 2
    while n > 1:
        while n % d == 0:
            factors.append(d)
            n //= d
        d += 1
        if d * d > n:
            if n > 1:
                factors.append(n)
            break
    return factors
```

### 3. Fast Exponentiation
```python
def power_mod(base: int, exponent: int, modulus: int) -> int:
    """Calculate (base ^ exponent) % modulus efficiently"""
    if modulus == 1:
        return 0
    
    result = 1
    base = base % modulus
    
    while exponent > 0:
        if exponent & 1:
            result = (result * base) % modulus
        base = (base * base) % modulus
        exponent >>= 1
    
    return result

def matrix_power(matrix: List[List[int]], n: int) -> List[List[int]]:
    """Calculate matrix ^ n efficiently"""
    def matrix_multiply(A, B):
        n = len(A)
        result = [[0] * n for _ in range(n)]
        for i in range(n):
            for j in range(n):
                for k in range(n):
                    result[i][j] += A[i][k] * B[k][j]
        return result
    
    if n == 0:
        return [[1 if i == j else 0 for j in range(len(matrix))] 
                for i in range(len(matrix))]
    
    if n == 1:
        return matrix
    
    half = matrix_power(matrix, n // 2)
    if n % 2 == 0:
        return matrix_multiply(half, half)
    else:
        return matrix_multiply(matrix_multiply(half, half), matrix)
```

### 4. Combinatorics
```python
def factorial(n: int) -> int:
    result = 1
    for i in range(2, n + 1):
        result *= i
    return result

def permutations(n: int, r: int) -> int:
    return factorial(n) // factorial(n - r)

def combinations(n: int, r: int) -> int:
    r = min(r, n - r)  # Optimization
    num = den = 1
    for i in range(r):
        num *= (n - i)
        den *= (i + 1)
    return num // den

def pascal_triangle(n: int) -> List[List[int]]:
    triangle = [[1]]
    for i in range(1, n):
        row = [1]
        for j in range(1, i):
            row.append(triangle[i-1][j-1] + triangle[i-1][j])
        row.append(1)
        triangle.append(row)
    return triangle
```

### 5. Number Theory Utilities
```python
def euler_totient(n: int) -> int:
    """Count numbers coprime to n"""
    result = n
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            while n % i == 0:
                n //= i
            result -= result // i
    if n > 1:
        result -= result // n
    return result

def modular_inverse(a: int, m: int) -> int:
    """Find multiplicative modular inverse of a under modulo m"""
    def extended_gcd(a, b):
        if a == 0:
            return b, 0, 1
        gcd, x1, y1 = extended_gcd(b % a, a)
        x = y1 - (b // a) * x1
        y = x1
        return gcd, x, y
    
    gcd, x, _ = extended_gcd(a, m)
    if gcd != 1:
        raise Exception('Modular inverse does not exist')
    return (x % m + m) % m
```

## Common Techniques

### 1. Modular Arithmetic Properties
```python
def modular_operations():
    # Addition
    (a + b) % m = ((a % m) + (b % m)) % m
    
    # Subtraction
    (a - b) % m = ((a % m) - (b % m) + m) % m
    
    # Multiplication
    (a * b) % m = ((a % m) * (b % m)) % m
    
    # Power
    (a ^ b) % m = ((a % m) ^ b) % m
```

### 2. Chinese Remainder Theorem
```python
def chinese_remainder(remainders: List[int], moduli: List[int]) -> int:
    """Solve system of linear congruences"""
    total = 0
    product = 1
    for modulus in moduli:
        product *= modulus
    
    for remainder, modulus in zip(remainders, moduli):
        p = product // modulus
        total += remainder * modular_inverse(p, modulus) * p
    
    return total % product
```

## Edge Cases to Consider
1. Zero input
2. Negative numbers
3. Large numbers (overflow)
4. Prime numbers
5. Perfect squares
6. Power of two
7. Integer limits
8. Floating point precision
9. Division by zero
10. Modulo with negative numbers

## Common Pitfalls
1. Integer overflow
2. Division by zero
3. Floating point precision
4. Negative number handling
5. Modulo sign issues
6. Large number computation
7. Recursive depth
8. Memory constraints

## Practice Problems by Difficulty

### Easy
1. [Count Primes](https://leetcode.com/problems/count-primes/) (LC #204)
2. [Power of Three](https://leetcode.com/problems/power-of-three/) (LC #326)
3. [Fibonacci Number](https://leetcode.com/problems/fibonacci-number/) (LC #509)

### Medium
1. [Pow(x, n)](https://leetcode.com/problems/powx-n/) (LC #50)
2. [Unique Paths](https://leetcode.com/problems/unique-paths/) (LC #62)
3. [Fraction to Recurring Decimal](https://leetcode.com/problems/fraction-to-recurring-decimal/) (LC #166)
4. [Basic Calculator II](https://leetcode.com/problems/basic-calculator-ii/) (LC #227)

### Hard
1. [Basic Calculator](https://leetcode.com/problems/basic-calculator/) (LC #224)
2. [Max Points on a Line](https://leetcode.com/problems/max-points-on-a-line/) (LC #149)
3. [Number of Digit One](https://leetcode.com/problems/number-of-digit-one/) (LC #233)

## Real-World Applications
1. **Cryptography**:
   - RSA algorithm
   - Prime factorization
2. **Financial Systems**:
   - Interest calculations
   - Currency conversion
3. **Graphics**:
   - Geometric computations
   - Transformations
4. **Scientific Computing**:
   - Numerical methods
   - Statistical analysis
5. **Game Development**:
   - Physics calculations
   - Probability systems
6. **Data Analysis**:
   - Statistical computations
   - Trend analysis

## Advanced Topics
1. **Number Theory**:
   - Euler's totient
   - Quadratic residues
2. **Combinatorics**:
   - Burnside's lemma
   - Inclusion-exclusion
3. **Linear Algebra**:
   - Matrix operations
   - Eigenvalues
4. **Probability**:
   - Expected value
   - Variance
5. **Numerical Methods**:
   - Newton's method
   - Numerical integration

## Important Resources
1. [Number Theory Concepts](https://www.geeksforgeeks.org/number-theory-competitive-programming/)
2. [Modular Arithmetic](https://www.hackerearth.com/practice/math/number-theory/basic-number-theory-1/tutorial/)
3. [Prime Numbers and Factorization](https://cp-algorithms.com/algebra/factorization.html)
4. [Combinatorics Tutorial](https://www.topcoder.com/thrive/articles/Basics%20of%20Combinatorics)
5. [Mathematical Algorithms](https://www.geeksforgeeks.org/mathematical-algorithms/)

## Interview Tips
1. Verify input constraints
2. Consider edge cases
3. Handle overflow
4. Use built-in functions wisely
5. Consider optimization
6. Test with examples
7. Explain mathematical intuition
8. Consider space-time trade-offs
9. Handle precision issues
10. Think about scalability