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

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(n) [due to call stack]
