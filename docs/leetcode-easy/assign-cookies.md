# Assign Cookies

Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie.

Each child i has a greed factor g[i], which is the minimum size of a cookie that the child will be content with; and each cookie j has a size s[j]. If s[j] >= g[i], we can assign
the cookie j to the child i, and the child i will be content. Your goal is to maximize the number of your content children and output the maximum number.

### Link - [https://leetcode.com/problems/assign-cookies/description/](https://leetcode.com/problems/assign-cookies/description/){target="_blank"}

```java
class Solution {
  public int findContentChildren(int[] g, int[] s) {
    // Sort the arrays of greed factors and cookie sizes
    Arrays.sort(g);
    Arrays.sort(s);

    // Initialize variables for counting content children and tracking array indices
    int count = 0;
    int i = 0; // Index for greed factors array
    int j = 0; // Index for cookie sizes array

    // Iterate through both arrays simultaneously
    while (i < g.length && j < s.length) {
      // If the current cookie size is sufficient for the current child's greed factor,
      // assign the cookie to the child and increment both child and cookie indices
      if (s[j] >= g[i]) {
        count++;
        i++;
        j++;
      } else {
        // If the current cookie size is not sufficient for the current child's greed factor,
        // move to the next cookie size while keeping the current child
        j++;
      }
    }

    // Return the count of content children
    return count;
  }
}
```

### Explanation

* **Array Sorting**: The method starts by sorting the arrays of greed factors (`g`) and cookie sizes (`s`). Sorting allows for efficient comparison of greed factors and cookie
  sizes later in the algorithm.

* **Variable Initialization**: It initializes variables `count`, `i`, and `j`. `count` stores the count of content children, while `i` and `j` are indices for iterating through the
  greed factors and cookie sizes arrays, respectively.

* **Iteration through Arrays**: The method iterates through both arrays simultaneously using the `while` loop. It continues iterating until either the end of the greed factors
  array (`g`) or the end of the cookie sizes array (`s`) is reached.

* **Comparison and Assignment**: For each iteration, it compares the current greed factor (`g[i]`) with the current cookie size (`s[j]`). If the cookie size is sufficient for the
  greed factor, it increments the `count` variable to indicate a content child and moves to the next greed factor and cookie size. If the cookie size is insufficient, it moves to
  the next cookie size while keeping the current greed factor.

* **Returning Result**: After iterating through both arrays, it returns the count of content children.


!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(nlog(n))
    - **Space Complexity:** O(1)
