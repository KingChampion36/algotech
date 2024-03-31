# Merge two binary Trees

### Link - [https://leetcode.com/problems/merge-two-binary-trees/](https://leetcode.com/problems/merge-two-binary-trees/){target="_blank"}

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
  public TreeNode mergeTrees(TreeNode root1, TreeNode root2) {
    // Check if both roots are null, indicating no trees to merge
    if (root1 == null && root2 == null) {
      return null;
    }
    // If root1 is null, return root2 (the other tree)
    if (root1 == null) {
      return root2;
    }
    // If root2 is null, return root1 (the other tree)
    if (root2 == null) {
      return root1;
    }

    // Add the values of both roots and update the value of root1
    root1.val = root1.val + root2.val;

    // Recursively merge the left subtrees and update root1's left child
    root1.left = mergeTrees(root1.left, root2.left);
    // Recursively merge the right subtrees and update root1's right child
    root1.right = mergeTrees(root1.right, root2.right);

    // Return the merged tree rooted at root1
    return root1;
  }
}
```

### Explanation

* **Base Case**: The method starts by checking if both `root1` and `root2` are null. If so, it returns null, indicating that there are no trees to merge.

* **Null Handling**: If either `root1` or `root2` is null, it returns the other root, as there's no need to merge with a null tree.

* **Value Addition**: If both `root1` and `root2` are not null, it adds the values of `root1` and `root2`, updating the value of `root1` to reflect the sum of the two roots.

* **Recursive Merging**: It then recursively merges the left subtrees of `root1` and `root2` and updates the left child of `root1`. Similarly, it merges the right subtrees and
  updates the right child of `root1`.

* **Return Merged Tree**: Finally, it returns the merged tree rooted at `root1`.

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(n) [due to call stack]
