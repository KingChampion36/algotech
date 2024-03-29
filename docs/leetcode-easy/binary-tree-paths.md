# Binary Tree Paths

Link - [https://leetcode.com/problems/binary-tree-paths/description/](https://leetcode.com/problems/binary-tree-paths/description/)

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

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(n) [due to call stack]
