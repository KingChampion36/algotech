# Root Equals Sum of Children

You are given the root of a binary tree that consists of exactly 3 nodes: the root, its left child, and its right child.

### Link - [https://leetcode.com/problems/root-equals-sum-of-children/](https://leetcode.com/problems/root-equals-sum-of-children/){target="_blank"}

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
  public boolean checkTree(TreeNode root) {
    if (root == null) {
      return true;
    }

    if (root.left == null && root.right == null) {
      return true;
    }

    int left = root.left != null ? root.left.val : 0;
    int right = root.right != null ? root.right.val : 0;

    return root.val == left + right && checkTree(root.left) && checkTree(root.right);
  }
}
```

### Explanation:

* **Objective**: The purpose of the `checkTree` method is to validate a specific binary tree structure, which in this case consists of exactly three nodes: a root node (`root`), a
  left child node (`root.left`), and a right child node (`root.right`).

* **Base Cases**:

  1. **Empty Tree (`root == null`)**:

      *   If the `root` node is `null`, indicating an empty tree, the method returns `true` because there is no tree structure to violate the condition.

  2. **Leaf Node (`root.left == null && root.right == null`)**:

      *   If the `root` node has no children (`left` and `right` are both `null`), it is considered a valid tree with exactly one node (the root itself), so the method returns `true`.

* **Value Calculation**:

  * For non-empty trees (where `root` is not `null`), the method calculates the values of the left and right children (`left` and `right`) or assumes their value as `0` if they
    are `null`.

* **Validation**:

  * The method checks if the sum of the values of the left and right children (`left + right`) equals the value of the `root` node (`root.val`). This check ensures that the tree
    structure at the current node satisfies a specific condition.
* **Recursion**:

  * The method recursively calls `checkTree` on the left subtree (`root.left`) and right subtree (`root.right`). This ensures that the entire tree structure starting from the current
    node (`root`) and extending to its children is validated according to the specified condition.
* **Return Value**:

  * The method returns `true` if the tree rooted at `root` satisfies the condition (valid structure) based on the value checks and recursive validation of its subtrees. If any part
    of the tree structure violates the condition, the method returns `false`.

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(n)
