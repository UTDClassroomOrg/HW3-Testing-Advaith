# HW3-Testing-Advaith

# Average Function Assignment

## Functional Description
The `average` function calculates the average of the first `k` elements in the array `list`. It ensures the number of elements used in the calculation does not exceed the size of the array. If `k` is greater than the array length, it computes the average of the entire array. If `k` is zero or negative, or if the array is empty, the function returns `0`.

---

## Functional Test Cases

| Test Case                         | Input                         | Expected Output |
|-----------------------------------|-------------------------------|-----------------|
| Normal Case                       | `k = 3`, `list = [1, 2, 3, 4, 5]` | `2`             |
| k Larger Than Array Length        | `k = 10`, `list = [5, 10, 15]`   | `10`            |
| Empty Array                       | `k = 3`, `list = []`            | `0`             |
| Negative k                        | `k = -2`, `list = [5, 10, 15]`  | `0`             |
| k = 0                             | `k = 0`, `list = [1, 2, 3]`     | `0`             |

---

## Partitions and Partition Test Cases

### Input Partitions
1. **k <= 0**: `k` is negative or zero.
2. **k > 0 and k <= list.length**: `k` is within the array length.
3. **k > list.length**: `k` exceeds the array length.
4. **Empty Array**: The array is empty (`list.length = 0`).

### Partition Test Cases
| Partition    | Input                         | Expected Output |
|--------------|-------------------------------|-----------------|
| k <= 0       | `k = -2`, `list = [1, 2, 3]`  | `0`             |
| k > 0, k <= length | `k = 3`, `list = [1, 2, 3, 4]` | `2`             |
| k > length   | `k = 5`, `list = [1, 2, 3]`   | `2`             |
| Empty Array  | `k = 3`, `list = []`          | `0`             |

---

## Boundary Value Test Cases

| Boundary Case                 | Input                         | Expected Output |
|-------------------------------|-------------------------------|-----------------|
| k = 1                         | `k = 1`, `list = [10]`        | `10`            |
| k = list.length               | `k = 3`, `list = [10, 20, 30]`| `20`            |
| k = list.length + 1           | `k = 4`, `list = [10, 20, 30]`| `20`            |
| Empty Array                   | `k = 1`, `list = []`          | `0`             |

---

## Java Implementation and JUnit Test Cases

### Java Implementation
```java
public class Average {
    public int average(int k, int[] list) {
        int average = 0;
        int n = Math.min(k, list.length);
        if (n > 0) {
            for (int i = 0; i < n; i++) {
                average += list[i];
            }
            average = average / n;
        }
        return average;
    }
}
