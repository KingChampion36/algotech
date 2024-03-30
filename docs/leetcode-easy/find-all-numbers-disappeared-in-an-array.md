# Find All Numbers Disappeared in an Array

### Link - [https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/description/](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/description/){target="_blank"}

## Method 1 (Using visited array)

This solution first creates a boolean array to track visited numbers, then loops through the array to find the missing numbers, and returns a list containing those missing numbers.

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

This code:

- Creates a boolean array to mark which numbers are visited.
- Iterates through the boolean array to find missing numbers.
- Utilizes a separate method to create the boolean array, keeping the main method clean and focused.
- The boolean array is used to mark visited numbers, enabling easy identification of missing numbers.

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(n)

## Method 2 (Negating the existing numbers)

This solution utilizes the property of the input array to mark visited numbers without using additional space.

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

#### Explanation

- **Marking Present Numbers:** It negates each number's index if it's positive to mark it as visited.
- **Finding Missing Numbers:** It iterates through the array to find positive numbers, indicating missing numbers, and adds them to the answer list.
- **Final Steps:** It returns the list containing all the disappeared numbers.

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(1) [Excluding the returned array]

