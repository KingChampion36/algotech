# Array Partition

### Link - [https://leetcode.com/problems/array-partition/description/](https://leetcode.com/problems/array-partition/description/){target="_blank"}

#### Given an integer array nums of 2n integers, group these integers into n pairs (a1, b1), (a2, b2), ..., (an, bn) such that the sum of min(ai, bi) for all i is maximized. Return the maximized sum.

```java
class Solution {
  public int arrayPairSum(int[] nums) {
    Arrays.sort(nums);

    int sum = 0;
    for (int i = 0; i < nums.length; i += 2) {
      sum += Math.min(nums[i], nums[i + 1]);
    }

    return sum;
  }
}
```

### Explanation

*   **Sorting**: The `arrayPairSum` method starts by sorting the given array in ascending order. This is crucial for maximizing the sum of minimum pairs since pairs are formed by adjacent elements after sorting.
*   **Iterating and Summing Pairs**: After sorting, the algorithm iterates through the sorted array by pairs (i.e., increments `i` by 2 in each iteration). For each pair, it adds the minimum of the two elements to the sum.
*   **Maximizing Sum**: By sorting the array and summing the minimum of each pair, the algorithm ensures that it maximizes the sum of min pairs. Sorting allows pairing the smallest numbers together, ensuring that the minimum of each pair contributes to the sum.

This solution efficiently maximizes the sum of min pairs by sorting the array and summing the minimum of each pair.

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(nlog(n))
    - **Space Complexity:** O(1)
