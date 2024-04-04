# Word Pattern

### Link - [https://leetcode.com/problems/word-pattern/description/](https://leetcode.com/problems/word-pattern/description/){target="_blank"}

```java
class Solution {
  public boolean wordPattern(String pattern, String s) {
    // Check if either the pattern or the string is null
    if (pattern == null || s == null) {
      return false;
    }
    // Split the string into words using space as delimiter
    String[] words = s.split(" ");
    // Check if the number of words matches the length of the pattern
    if (words.length != pattern.length()) {
      return false;
    }

    // Create two maps to store the mapping between characters and words
    Map<Character, String> patternToWordMap = new HashMap<>();
    Map<String, Character> wordToPatternMap = new HashMap<>();

    // Iterate through the pattern and words
    for (int i = 0; i < pattern.length(); i++) {
      // If both maps don't contain mappings for the current character and word
      if (patternToWordMap.get(pattern.charAt(i)) == null && wordToPatternMap.get(words[i]) == null) {
        // Create mappings between the character and word in both maps
        patternToWordMap.put(pattern.charAt(i), words[i]);
        wordToPatternMap.put(words[i], pattern.charAt(i));
      } else {
        // If mappings exist, check if they are consistent
        if (!words[i].equals(patternToWordMap.get(pattern.charAt(i)))
          || pattern.charAt(i) != wordToPatternMap.get(words[i])
        ) {
          // If mappings are not consistent, return false
          return false;
        }
      }
    }

    // If all mappings are consistent, return true
    return true;
  }
}
```

### Explanation

* **Null Check**: The method starts by checking if either the pattern or the string is null. If either is null, it returns false, as there cannot be a bijection between a null
  pattern or string.

* **String Splitting**: It then splits the input string `s` into words using space as the delimiter.

* **Length Comparison**: It compares the number of words obtained from splitting `s` with the length of the pattern. If they are not equal, it returns false, indicating that there
  cannot be a bijection.

* **Mapping Creation**: It creates two maps: `patternToWordMap` and `wordToPatternMap` to store the mappings between characters and words.

* **Mapping Consistency Check**: It iterates through the pattern and words simultaneously. For each character-word pair, it checks if both maps contain mappings. If not, it creates
  mappings between the character and word in both maps. If mappings exist, it checks if they are consistent. If mappings are not consistent, it returns false.

* **Result Return**: If all mappings are consistent, it returns true, indicating that the input string follows the given pattern.

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(n)
