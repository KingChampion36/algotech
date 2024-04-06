# Evaluate Boolean Binary Tree

### Link - [https://leetcode.com/problems/evaluate-boolean-binary-tree/](https://leetcode.com/problems/evaluate-boolean-binary-tree/){target="_blank"}

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
  public boolean evaluateTree(TreeNode root) {
    if (root == null) {
      return true;
    }
    if (root.left == null && root.right == null) {
      return root.val == 0 ? false : true;
    }
    if (root.val == 2) {
      return evaluateTree(root.left) || evaluateTree(root.right);
    }
    return evaluateTree(root.left) && evaluateTree(root.right);
  }
}
```

### Explanation:

* **Base Case (`root == null`)**:

  * If the `root` node is `null`, indicating an empty tree, the method returns `true`. An empty tree is considered valid.
* **Leaf Node Evaluation (`root.left == null && root.right == null`)**:
  * If the `root` node has no children (`left` and `right` are both `null`), it is considered a leaf node.
* The leaf node's value (`root.val`) is evaluated:
  * If `root.val` is `0`, return `false` (representing `False`).
  * If `root.val` is `1`, return `true` (representing `True`).
* **Non-leaf Node Evaluation (`root.val == 2` or `root.val == 3`)**:

  * For non-leaf nodes (`root.val` is `2` for OR, `3` for AND), recursively evaluate the left and right subtrees (`root.left` and `root.right`):
    * If `root.val` is `2` (OR), return the logical OR (`||`) of the evaluations of the left and right subtrees.
    * If `root.val` is `3` (AND), return the logical AND (`&&`) of the evaluations of the left and right subtrees.

### Key Points:

* **Base Case Handling**:

  * The method handles the base case where the `root` node is `null`, ensuring that an empty tree is considered valid.
* **Leaf Node Handling**:

  * Leaf nodes are identified based on the absence of children (`left` and `right` are both `null`).
  * The boolean value (`true` or `false`) of a leaf node is determined by its `val` property (`0` for `false`, `1` for `true`).
* **Non-leaf Node Handling**:

  * Non-leaf nodes (`2` for OR, `3` for AND) recursively evaluate their children and apply the corresponding boolean operation (`||` or `&&`) to determine their boolean value.
