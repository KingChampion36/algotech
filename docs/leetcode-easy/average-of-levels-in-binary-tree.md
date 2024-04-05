# Average of levels in Binary Tree

### Link - [https://leetcode.com/problems/average-of-levels-in-binary-tree/](https://leetcode.com/problems/average-of-levels-in-binary-tree/){target="_blank"}

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
  public List<Double> averageOfLevels(TreeNode root) {
    List<Double> answer = new ArrayList<>();
    if (root == null) {
      return answer;
    }

    Queue<TreeNode> Q = new LinkedList<>();
    Q.offer(root);

    while (!Q.isEmpty()) {
      int nodesInCurrentLevel = Q.size();
      Double sum = 0.0;
      int n = nodesInCurrentLevel;
      while (n-- > 0) {
        TreeNode node = Q.poll();
        sum += node.val;
        if (node.left != null) {
          Q.offer(node.left);
        }
        if (node.right != null) {
          Q.offer(node.right);
        }
      }
      Double average = sum / nodesInCurrentLevel;
      answer.add(average);
    }
    return answer;
  }
}
```

### Explanation:

* **Node Definition**: The code begins with the definition of the binary tree node class `TreeNode`, which includes a value (`val`), and references to the left and right child
  nodes (`left` and `right`).

* **Method Explanation**: The `averageOfLevels` method calculates the average value of nodes at each level of the binary tree.

* **Base Case**: It starts with a base case where it checks if the root is null. If the root is null, it returns an empty list, indicating that there are no levels to compute
  averages for.

* **Level Order Traversal**: It performs level order traversal of the binary tree using a queue (`Q`). It starts by adding the root node to the queue.

* **Processing Each Level**: While the queue is not empty, it processes each level:

  * It gets the number of nodes in the current level (`nodesInCurrentLevel`) and initializes a sum to store the sum of values of nodes in the current level.
  * It iterates through the nodes in the current level, calculates the sum of their values, and adds their children to the queue for the next level.
  * After processing all nodes in the current level, it calculates the average value of nodes in that level and adds it to the list of averages.

* **Return Value**: Finally, it returns the list of averages of levels.

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(n)
