# Add Number Strings

### Link - [https://leetcode.com/problems/add-strings/description/](https://leetcode.com/problems/add-strings/description/){target="_blank"}

```java
class Solution {
  public String addStrings(String num1, String num2) {
    StringBuilder result = new StringBuilder();
    int carry = 0;
    int i = num1.length() - 1, j = num2.length() - 1;

    while (i >= 0 || j >= 0 || carry > 0) {
      int digit1 = (i >= 0) ? num1.charAt(i--) - '0' : 0;
      int digit2 = (j >= 0) ? num2.charAt(j--) - '0' : 0;
      int sum = digit1 + digit2 + carry;
      result.append(sum % 10);
      carry = sum / 10;
    }

    return result.reverse().toString();
  }
}
```

### Explanation

* **StringBuilder Initialization**: The method initializes a `StringBuilder` named `result` to store the result of addition.

* **Carry Initialization**: It initializes an integer variable `carry` to store the carry generated during addition.

* **Pointer Initialization**: It initializes two pointers `i` and `j` to the last digits of `num1` and `num2`, respectively.

* **Addition Loop**: The method iterates through both numbers from their last digits to their first digits, or until there's no carry left. It handles addition of corresponding
  digits along with the carry.

* **Digit Retrieval**: Inside the loop, it retrieves the current digits from `num1` and `num2`, or 0 if either of the numbers is exhausted.

* **Sum Calculation**: It calculates the sum of current digits along with the carry and appends the last digit of the sum to the `result` StringBuilder.

* **Carry Update**: It updates the carry for the next iteration based on the sum.

* **Final Result**: After the loop, it reverses the `result` StringBuilder to obtain the final result and returns it as a string.

This implementation efficiently adds two number strings by iterating through them once and handling addition along with carry. It utilizes a `StringBuilder` for efficient string
manipulation and reverses the result at the end to obtain the correct order of digits.

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(n)
    - **Space Complexity:** O(1)
