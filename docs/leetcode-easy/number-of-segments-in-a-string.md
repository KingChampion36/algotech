# Number of Segments in a String

### Link - [https://leetcode.com/problems/number-of-segments-in-a-string/description/](https://leetcode.com/problems/number-of-segments-in-a-string/description/){target="_blank}

```java
class Solution {
  public int countSegments(String s) {
    if (s == null || s.length() == 0) {
      return 0;
    }

    int firstNonSpaceIndex = findFirstNonSpaceIndex(s);

    int count = 0;
    for (int i = firstNonSpaceIndex; i < s.length(); i++) {
      if (s.charAt(i) == ' ' && s.charAt(i - 1) != ' ') {
        count++;
      }
    }

    // Count Last word
    if (s.charAt(s.length() - 1) != ' ') {
      count++;
    }

    return count;
  }

  private int findFirstNonSpaceIndex(String s) {
    for (int i = 0; i < s.length(); i++) {
      if (s.charAt(i) != ' ') {
        return i;
      }
    }
    return s.length();
  }
}
```

### Explanation

* **Null or Empty Check**: The method first checks if the input string `s` is null or empty. If so, it returns 0, indicating that there are no segments in the string.

* **Finding First Non-Space Index**: It then finds the index of the first non-space character in the string using the `findFirstNonSpaceIndex` method.

* **Segment Counting**: It initializes a count variable to store the count of segments. It iterates through the string starting from the index of the first non-space character. For
  each character, it checks if it is a space and if the previous character is not a space. If so, it increments the count to indicate a new segment.

* **Handling Last Word**: After the loop, it checks if the last word in the string is not followed by a space. If so, it increments the count to include the last word as a segment.

* **Returning Count**: Finally, it returns the count of segments in the string.

This implementation accurately counts the number of segments in a string by iterating through it once and detecting segment boundaries based on space characters. It correctly
handles cases where segments may be separated by multiple consecutive spaces and accounts for the last word even if it's not followed by a space.

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(1)
