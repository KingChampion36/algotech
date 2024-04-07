# Find a Corresponding Node of a Binary Tree in a Clone of That Tree

### Link - [https://leetcode.com/problems/find-a-corresponding-node-of-a-binary-tree-in-a-clone-of-that-tree/description/](https://leetcode.com/problems/find-a-corresponding-node-of-a-binary-tree-in-a-clone-of-that-tree/description/){target="_blank"}

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
  private TreeNode answer = null;

  public final TreeNode getTargetCopy(final TreeNode original, final TreeNode cloned, final TreeNode target) {
    // Call helper function to find the target node in the cloned tree
    targetCopy(original, cloned, target);
    return answer;
  }

  private void targetCopy(final TreeNode original, final TreeNode cloned, final TreeNode target) {
    // Base case: If either tree is null, return
    if (cloned == null || original == null) {
      return;
    }

    // If the current node in the cloned tree matches the target node
    if (cloned.val == target.val) {
      answer = cloned; // Update answer to the current cloned node
      return;
    }

    // Recursively search the left subtree
    targetCopy(original.left, cloned.left, target);

    // Recursively search the right subtree
    targetCopy(original.right, cloned.right, target);
  }
}
```

### Explanation

* **Method Signature**:
    * The `getTargetCopy` method initializes `answer` and calls the recursive helper function `targetCopy` to find the corresponding node in the cloned tree.

* **Recursive Helper Function (`targetCopy`)**:
    * This function takes three parameters: `original` (current node in the original tree), `cloned` (current node in the cloned tree), and `target` (target node in the original tree).
    * Base Case:
        * If either `cloned` or `original` is `null`, return without further processing.
    * If the current node in the `cloned` tree matches the target node (`target`), update `answer` to this node.
    * Recursively call `targetCopy` for the left and right children of both `original` and `cloned` trees to continue the search.

* **Returning Result**:
    * After the recursive traversal completes, `answer` holds the reference to the corresponding node in the cloned tree that matches the target node.
    * Return `answer` as the result of the function.

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(n)

### Level order Traversal Solution

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */

class Solution {
  public final TreeNode getTargetCopy(final TreeNode original, final TreeNode cloned, final TreeNode target) {
    Queue<TreeNode> Q = new LinkedList<>();
    Q.offer(cloned);

    while (!Q.isEmpty()) {
      TreeNode node = Q.poll();
      if (node.val == target.val) {
        return node;
      }
      if (node.left != null) {
        Q.offer(node.left);
      }
      if (node.right != null) {
        Q.offer(node.right);
      }
    }

    return null;
  }
}
```

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(n)
