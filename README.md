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
```
### JUnit Test Cases
```java
import org.junit.Test;
import static org.junit.Assert.*;

public class AverageTest {

    @Test
    public void testNormalCase() {
        Average avg = new Average();
        assertEquals(2, avg.average(3, new int[]{1, 2, 3, 4, 5}));
    }

    @Test
    public void testKGreaterThanArrayLength() {
        Average avg = new Average();
        assertEquals(10, avg.average(10, new int[]{5, 10, 15}));
    }

    @Test
    public void testEmptyArray() {
        Average avg = new Average();
        assertEquals(0, avg.average(3, new int[]{}));
    }

    @Test
    public void testNegativeK() {
        Average avg = new Average();
        assertEquals(0, avg.average(-2, new int[]{5, 10, 15}));
    }

    @Test
    public void testKZero() {
        Average avg = new Average();
        assertEquals(0, avg.average(0, new int[]{1, 2, 3}));
    }
}
```

## JUnit Test Cases Failures and Analysis

### Observations

- **testNormalCase**: This test case passes as expected. It tests the function with a normal case where `k` is less than the list length, and the average is computed correctly.
  
- **testKGreaterThanArrayLength**: This test case passes successfully. It checks the behavior when `k` exceeds the array length and verifies the average of the entire array.
  
- **testEmptyArray**: This test case passes successfully. It ensures that when the list is empty, the function correctly returns `0`.
  
- **testNegativeK**: This test case passes. It verifies that when `k` is negative, the function returns `0`, as expected.
  
- **testKZero**: This test case passes. It checks the case when `k` is `0`, ensuring the function returns `0`.

## Code Coverage

### Code Coverage Report

After running the tests with EclEmma in Eclipse, the code coverage was evaluated for the `Average` class. The coverage report shows **100% branch coverage**.

- **Lines Covered**: 100%
- **Branch Coverage**: 100%
- **Code Coverage Tools**: EclEmma

This confirms that all the branches and conditions in the `average` method are covered by the tests.

