# 2149. Rearrange Array Elements by Sign

## Problem

You are given an integer array `nums` containing an equal number of positive and negative integers.

Rearrange the array such that:

- Every consecutive pair of integers has opposite signs.
- The relative order of positive integers is preserved.
- The relative order of negative integers is preserved.
- The array starts with a positive integer.

Return the modified array.

## Approach

Create a new array of the same size.

- Place positive numbers at even indices: `0, 2, 4, ...`
- Place negative numbers at odd indices: `1, 3, 5, ...`
- Use two pointers:
  - `pos` for positive positions.
  - `neg` for negative positions.

Since the number of positive and negative elements is equal, all positions will be filled correctly.

## Algorithm

1. Create an array `ans` of size `n`.
2. Initialize:
   - `pos = 0`
   - `neg = 1`
3. Traverse the input array.
4. If the current element is positive:
   - Place it at `ans[pos]`
   - Increment `pos` by 2.
5. Otherwise:
   - Place it at `ans[neg]`
   - Increment `neg` by 2.
6. Return `ans`.

## Code

```java
class Solution {
    public int[] rearrangeArray(int[] nums) {
        int[] ans = new int[nums.length];

        int pos = 0;
        int neg = 1;

        for (int num : nums) {
            if (num > 0) {
                ans[pos] = num;
                pos += 2;
            } else {
                ans[neg] = num;
                neg += 2;
            }
        }

        return ans;
    }
}
```

## Dry Run

Input:

```text
nums = [3,1,-2,-5,2,-4]
```

Initial:

```text
ans = [_, _, _, _, _, _]
pos = 0
neg = 1
```

Process elements:

```text
3  -> ans[0] = 3
1  -> ans[2] = 1
-2 -> ans[1] = -2
-5 -> ans[3] = -5
2  -> ans[4] = 2
-4 -> ans[5] = -4
```

Final array:

```text
[3,-2,1,-5,2,-4]
```

## Complexity Analysis

- Time Complexity: O(n)
- Space Complexity: O(n)

## Key Concept

Use separate indices for positive and negative numbers.

```text
Even indices  -> Positive numbers
Odd indices   -> Negative numbers
```

This guarantees alternating signs while preserving the original order of positive and negative elements.
