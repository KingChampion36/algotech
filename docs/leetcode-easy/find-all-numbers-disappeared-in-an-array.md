# Find All Numbers Disappeared in an Array

Link - [https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/description/](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/description/)

## Method 1 (Using visited array)

```java
class Solution {
  public List<Integer> findDisappearedNumbers(int[] nums) {
    boolean[] visited = visitedArray(nums);

    List<Integer> answer = new ArrayList<>();
    for (int i = 1; i < visited.length; i++) {
      if (visited[i] == false) {
        answer.add(i);
      }
    }

    return answer;
  }

  private static boolean[] visitedArray(int[] nums) {
    boolean[] visited = new boolean[nums.length + 1];
    for (int i = 0; i < nums.length; i++) {
      visited[nums[i]] = true;
    }
    return visited;
  }
}
```

## Method 2 (Negating the existing numbers)

```java
class Solution {
  public List<Integer> findDisappearedNumbers(int[] nums) {
    // Negate the numbers which are present
    for (int i = 0; i < nums.length; i++) {
      int index = Math.abs(nums[i]) - 1;
      if (nums[index] > 0) {
        nums[index] *= -1;
      }
    }

    List<Integer> answer = new ArrayList<>();
    for (int i = 0; i < nums.length; i++) {
      if (nums[i] > 0) {
        answer.add(i + 1);
      }
    }

    return answer;
  }
}
```

