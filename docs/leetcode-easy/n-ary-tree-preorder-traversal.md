# N-ary Tree Preorder Traversal

### Link - [https://leetcode.com/problems/n-ary-tree-preorder-traversal/description/](https://leetcode.com/problems/n-ary-tree-preorder-traversal/description/){target="_blank"}

```java
/*
// Definition for a Node.
class Node {
    public int val;
    public List<Node> children;

    public Node() {}

    public Node(int _val) {
        val = _val;
    }

    public Node(int _val, List<Node> _children) {
        val = _val;
        children = _children;
    }
};
*/

class Solution {
  public List<Integer> preorder(Node root) {
    List<Integer> answer = new ArrayList<>();
    preorder(root, answer);
    return answer;
  }

  private void preorder(Node root, List<Integer> answer) {
    if (root == null) {
      return;
    }
    answer.add(root.val);
    for (Node child : root.children) {
      preorder(child, answer);
    }
  }
}
```

### Explanation

*   **Preorder Traversal**: The `preorder` method is the entry point of the algorithm. It initializes a list to store the preorder traversal result and calls a recursive method to perform the traversal.
*   **Recursive Traversal**: The `preorder` method recursively traverses the N-ary tree in preorder fashion, which means visiting the root node, then recursively traversing each child node in preorder.
*   **Base Case**: If the current node is null, it means the traversal has reached the end, so the method returns.
*   **Adding Nodes to Result**: It adds the value of the current node to the result list before traversing its children.
*   **Iterating Through Children**: It iterates through each child of the current node and recursively performs the preorder traversal on each child.

This solution efficiently performs the preorder traversal of an N-ary tree using recursion, adding nodes to the result list as they are visited.


!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(n) [due to call stack]
