## Q9.Collatz Sequence Analysis

### Problem Statement
Given a positive integer $n$, generate its Collatz trajectory using the following rules:
* If $n$ is even, divide it by 2.
* If $n$ is odd, calculate $3n + 1$.
* Continue until the value becomes 1.

The program should display the complete trajectory, number of steps, and maximum value reached. It should also analyze an interval $[a, b]$ to find the number having the longest sequence and the highest value reached. Overflow during the $3n + 1$ operation must also be detected.

### Algorithm

 A. Collatz Next Value
* Check whether the current number is even. If it is even, calculate:
  $n = n / 2$
* If it is odd, check whether calculating $3n + 1$ will cause an unsigned integer overflow
* If overflow is possible, set the overflow flag. Otherwise, calculate:
  $n = 3n + 1$

B. Single Trajectory Analysis
* Initialize the current value and maximum value with the starting number.
* Dynamically allocate memory for storing the trajectory.
* Continue generating Collatz values until $1$ is reached, expanding capacity using `realloc()` as needed.
* Track the maximum value encountered and safely terminate if overflow occurs.
* Display the starting value, complete trajectory, number of steps, and peak value.

C. Interval Analysis
* Iterate through every starting value from $a$ to $b$.
* For each value, generate its sequence, count steps, and track the highest peak reached.
* Record the values producing the longest sequence and the highest peak, then display the interval summary.
