# Ransom Note

### Link - [https://leetcode.com/problems/ransom-note/](https://leetcode.com/problems/ransom-note/){target="_blank"}

## Method 1 (Using 2 maps)

```java
class Solution {
  public boolean canConstruct(String ransomNote, String magazine) {
    Map<Character, Integer> ransomNoteMap = constructCountMap(ransomNote);
    Map<Character, Integer> magazineMap = constructCountMap(magazine);

    for (Map.Entry<Character, Integer> e : ransomNoteMap.entrySet()) {
      Character key = e.getKey();
      Integer value = e.getValue();

      if (magazineMap.get(key) == null || magazineMap.get(key) < value) {
        return false;
      }
    }

    return true;
  }

  private Map<Character, Integer> constructCountMap(String s) {
    Map<Character, Integer> map = new HashMap<>();
    for (char ch : s.toCharArray()) {
      map.put(ch, map.getOrDefault(ch, 0) + 1);
    }
    return map;
  }
}
```

### Explanation:

*   **Count Maps Construction**: The `canConstruct` method constructs count maps for both the `ransomNote` and `magazine` strings using the `constructCountMap` method. These count maps store the frequency of each character in the respective strings.

*   **Checking Constructibility**: It iterates through the count map of `ransomNote`. For each character and its frequency in `ransomNote`, it checks if the count in the count map of `magazine` is at least equal to the required count. If not, it means the `ransomNote` cannot be constructed using the letters from `magazine`, so it returns `false`.

*   **Returning Result**: If all characters in `ransomNote` can be constructed using the letters from `magazine`, it returns `true`.


This solution efficiently determines whether `ransomNote` can be constructed using the letters from `magazine` by counting characters and checking their frequencies.

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(n)

### Method 2 (Using a single map)

```java
class Solution {
  public boolean canConstruct(String ransomNote, String magazine) {
    Map<Character, Integer> magazineMap = constructCountMap(magazine);

    for (char ch : ransomNote.toCharArray()) {
      magazineMap.put(ch, magazineMap.getOrDefault(ch, 0) - 1);
      if (magazineMap.get(ch) < 0) {
        return false;
      }
    }

    return true;
  }

  private Map<Character, Integer> constructCountMap(String s) {
    Map<Character, Integer> map = new HashMap<>();
    for (char ch : s.toCharArray()) {
      map.put(ch, map.getOrDefault(ch, 0) + 1);
    }
    return map;
  }
}
```

### Explanation

*   **Constructing Character Count Map**: The `canConstruct` method starts by constructing a map called `magazineMap`, which stores the count of each character in the `magazine` string. This is done using the `constructCountMap` method.

*   **Iterating Through Ransom Note**: It then iterates through each character in the `ransomNote` string.

*   **Decrementing Counts**: For each character in `ransomNote`, it decrements the count of that character in the `magazineMap`.

*   **Checking Availability**: If at any point the count of a character becomes negative in `magazineMap`, it means that character is not available in the `magazine` string, so it returns `false`.

*   **Returning Result**: If the loop completes without encountering any negative counts, it means all characters in `ransomNote` can be constructed using the characters from `magazine`, so it returns `true`.


This solution improves upon the previous one by combining the construction of the count map and the checking of character availability in a single loop. It achieves the same result but with better efficiency.

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(n)
