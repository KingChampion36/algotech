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

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(nlog(n))
    - **Space Complexity:** O(1)
