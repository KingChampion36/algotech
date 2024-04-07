# Leaf Similar Trees

### Link - [https://leetcode.com/problems/leaf-similar-trees/description/](https://leetcode.com/problems/leaf-similar-trees/description/){target="_blank"}

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
  public boolean leafSimilar(TreeNode root1, TreeNode root2) {
    List<Integer> leafSeq1 = new ArrayList<>();
    leafSequence(root1, leafSeq1);
    List<Integer> leafSeq2 = new ArrayList<>();
    leafSequence(root2, leafSeq2);

    return isSimilar(leafSeq1, leafSeq2);
  }

  private void leafSequence(TreeNode root, List<Integer> leafSeq) {
    if (root == null) {
      return;
    }
    if (root.left == null && root.right == null) {
      leafSeq.add(root.val);
      return;
    }
    leafSequence(root.left, leafSeq);
    leafSequence(root.right, leafSeq);
  }

  private boolean isSimilar(List<Integer> leafSeq1, List<Integer> leafSeq2) {
    if (leafSeq1.size() != leafSeq2.size()) {
      return false;
    }
    for (int i = 0; i < leafSeq1.size(); i++) {
      if (leafSeq1.get(i).intValue() != leafSeq2.get(i).intValue()) {
        return false;
      }
    }
    return true;
  }
}
```

### Explanation:

* **Leaf Value Sequence Construction**:

    * The `leafSimilar` method initializes two lists (`leafSeq1` and `leafSeq2`) to store the leaf value sequences of `root1` and `root2`, respectively.
    * It then invokes the `leafSequence` method for each tree to construct the leaf value sequences in a depth-first manner.

* **Leaf Sequence Construction (`leafSequence` method)**:

    * This method recursively traverses each tree (`root`) in a depth-first manner.
    * If the current node (`root`) is a leaf node (i.e., it has no left or right child), its value is added to the corresponding `leafSeq` list.
    * The traversal continues recursively for both the left and right children of the current node.

* **Leaf Sequence Comparison (`isSimilar` method)**:

    * After constructing the leaf value sequences for both trees (`root1` and `root2`), the `isSimilar` method is invoked to compare these sequences.
    * It first checks if the sizes of `leafSeq1` and `leafSeq2` are different. If so, the trees cannot be leaf-similar, and the method returns `false`.
    * If the sizes are the same, the method iterates through the leaf value sequences (`leafSeq1` and `leafSeq2`) element by element.
    * If there is any mismatch between corresponding leaf values in the sequences, the method returns `false`, indicating that the trees are not leaf-similar.
    * If the sequences match completely, the method returns `true`, indicating that the trees are leaf-similar.

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(n)
