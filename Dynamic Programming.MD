# Dynamic Programming

### Basic Concept

- Recursive solution: repeated calls for same inputs --> optimize using Dynamic Programming by storing the results of subproblems.

- Fibonacci Example

  - Recursive Solution
  
  ```C++
  int fib(int n) {
    if (n <= 1)
      return 1;
     return fib(n-1) + fib(n-2);
  }
  ```
  
  - Dynamic Programming Solution
  
  ```C++
  int fib(int n) {
    int f[n + 1];
    f[0] = 1;
    f[1] = 1;
    
    for (int i = 0; i <= n; i++) {
      f[i] = f[i-1] + f[i-2];
    }
    
    return f[n];
  }
  ```
