# First Bad Version

Link - [https://leetcode.com/problems/first-bad-version/description/](https://leetcode.com/problems/first-bad-version/description/)

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

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(log(n))
    - **Space Complexity:** O(log(n)) [due to call stack]
