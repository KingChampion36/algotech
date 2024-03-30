# First Bad Version

### Link - [https://leetcode.com/problems/first-bad-version/description/](https://leetcode.com/problems/first-bad-version/description/){target="_blank"}

```java
/* The isBadVersion API is defined in the parent class VersionControl.
      boolean isBadVersion(int version); */

public class Solution extends VersionControl {
  public int firstBadVersion(int n) {
    return findFirstBadVersion(1, n);
  }

  // Binary Search
  private int findFirstBadVersion(int start, int end) {
    if (start > end) {
      return -1;
    }
    int mid = start + (end - start) / 2;

    if (isBadVersion(mid) && !isBadVersion(mid - 1)) {
      return mid;
    }

    if (isBadVersion(mid)) {
      return findFirstBadVersion(start, mid - 1);
    }

    return findFirstBadVersion(mid + 1, end);
  }
}
```

### Explanation:

*   **Finding the First Bad Version**: The `firstBadVersion` method is the entry point of the algorithm. It calls the `findFirstBadVersion` method with the range from 1 to `n`.

*   **Binary Search Approach**: The `findFirstBadVersion` method implements a binary search approach to find the first bad version. It recursively divides the range into halves and searches in the appropriate half based on whether the midpoint is a bad version or not.

*   **Base Case**: If the start index exceeds the end index, it means there are no bad versions in the current range, so it returns -1.

*   **Midpoint Calculation**: It calculates the midpoint of the current range.

*   **Checking for Bad Version**: If the midpoint is a bad version and the previous version is not, it means the first bad version is found, so it returns the midpoint.

*   **Recursion**: If the midpoint is a bad version, it recursively searches in the left half; otherwise, it searches in the right half.


This solution efficiently finds the first bad version using a binary search algorithm, reducing the number of API calls to `isBadVersion` and optimizing the search process.

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(log(n))
    - **Space Complexity:** O(log(n)) [due to call stack]
