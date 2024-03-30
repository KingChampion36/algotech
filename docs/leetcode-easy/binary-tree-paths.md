# Binary Tree Paths

### Link - [https://leetcode.com/problems/binary-tree-paths/description/](https://leetcode.com/problems/binary-tree-paths/description/){target="_blank"}

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
  public List<String> binaryTreePaths(TreeNode root) {
    List<String> answer = new ArrayList<>();
    binaryTreePaths(root, answer, "");
    return answer;
  }

  private static void binaryTreePaths(TreeNode root, List<String> answer, String currentString) {
    if (root == null) {
      return;
    }

    String path = currentString == "" ? String.valueOf(root.val) : currentString + "->" + String.valueOf(root.val);

    if (root.left == null && root.right == null) {
      answer.add(path);
      return;
    }

    binaryTreePaths(root.left, answer, path);
    binaryTreePaths(root.right, answer, path);
  }
}
```

### Explanation:

*   **Finding All Paths**: The `binaryTreePaths` method is the entry point of the algorithm. It initializes a list to store paths and calls a recursive method to find all paths in the binary tree.

*   **Recursive Path Building**: The `binaryTreePaths` method recursively builds the path string as it traverses the binary tree. It appends each node's value to the current path string and updates it accordingly.

*   **Base Case**: If the current node is null, it means the path has reached its end, so the method returns.

*   **Leaf Node Handling**: If the current node is a leaf node (both left and right children are null), it means a complete path is found, so it adds the path to the answer list.

*   **Recursion**: It recursively traverses the left and right subtrees, passing the updated path string to each recursive call.


This solution efficiently finds all paths in the binary tree by recursively traversing the tree and building paths as it goes.

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(n) [due to call stack]
