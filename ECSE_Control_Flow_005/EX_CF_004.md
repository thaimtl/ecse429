# EX_CF_004 - Bubble Sort

## Control flow diagram

[EX_CF_004_Diagram.pdf](EX_CF_004_Diagram.pdf)

| Node | Code |
|---|---|
| 1 | `int n = arr.length; int i = 0` |
| 2 | `i < n-1` |
| 3 | `int j = 0` |
| 4 | `j < n-i-1` |
| 5 | `arr[j] > arr[j+1]` |
| 6 | swap |
| 7 | `j++` |
| 8 | `i++` |
| 9 | end |

## Number of basis paths

N = 9, E = 11

V(G) = E - N + 2 = 11 - 9 + 2 = **4**

## Basis paths

1. 1 → 2 → 9
2. 1 → 2 → 3 → 4 → 5 → 7 → 4 → 8 → 2 → 9
3. 1 → 2 → 3 → 4 → 5 → 6 → 7 → 4 → 8 → 2 → 9
4. 1 → 2 → 3 → 4 → 5 → 7 → 4 → 5 → 7 → 4 → 8 → 2 → 3 → 4 → 5 → 7 → 4 → 8 → 2 → 9

Path 4 is used instead of 1 → 2 → 3 → 4 → 8 → 2 → 9, which is infeasible: when i < n-1, the inner test j < n-i-1 always passes at least once.
