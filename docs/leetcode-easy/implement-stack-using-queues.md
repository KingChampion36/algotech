# Implement Stack using Queues

### Link - [https://leetcode.com/problems/implement-stack-using-queues/](https://leetcode.com/problems/implement-stack-using-queues/){target="_blank"}

```java
class MyStack {

  private final Queue<Integer> Q1;
  private final Queue<Integer> Q2;

  public MyStack() {
    Q1 = new LinkedList<>();
    Q2 = new LinkedList<>();
  }

  public void push(int x) {
    Q1.offer(x);
  }

  public int pop() {
    if (Q1.isEmpty()) {
      throw new IllegalArgumentException("Stack is empty");
    }
    while (Q1.size() > 1) {
      Q2.offer(Q1.poll());
    }
    int answer = Q1.poll();
    while (!Q2.isEmpty()) {
      Q1.offer(Q2.poll());
    }
    return answer;
  }

  public int top() {
    if (Q1.isEmpty()) {
      throw new IllegalArgumentException("Stack is empty");
    }
    while (Q1.size() > 1) {
      Q2.offer(Q1.poll());
    }
    int answer = Q1.poll();
    Q2.offer(answer);
    while (!Q2.isEmpty()) {
      Q1.offer(Q2.poll());
    }
    return answer;
  }

  public boolean empty() {
    return Q1.isEmpty();
  }
}
```

### Explanation

* **Queue Initialization**: The constructor initializes two queues, `Q1` and `Q2`, using the `LinkedList` implementation.

* **Push Operation**: The `push` method adds elements to `Q1`, effectively pushing elements onto the stack.

* **Pop Operation**: The `pop` method removes and returns the top element from the stack. It moves all elements except the last one from `Q1` to `Q2`, retrieves the last element
  from `Q1`, and then moves all elements back to `Q1`.

* **Top Operation**: The `top` method returns the top element from the stack without removing it. Similar to the `pop` operation, it moves all elements except the last one
  from `Q1` to `Q2`, retrieves the last element from `Q1`, moves it to `Q2` and then back to `Q1`, and finally returns the element.

* **Empty Check**: The `empty` method checks if the stack is empty by checking if `Q1` is empty.
