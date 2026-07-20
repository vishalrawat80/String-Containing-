# String-Containing-
string containing 

# 2.Write a program: Given a string containing just the characters '(' and ')', return the length of the longest valid (well-formed) parentheses substring.
Example 1:Input: s = "(()"Output: 2Explanation: The longest valid parentheses substring is "()".
Example 2:Input: s = ")()())"Output: 4Explanation: The longest valid parentheses substring is "()()".
Example 3:Input: s = ""Output: 0
Constraints:
0 <= s.length <= 3 * 104
s[i] is '(', or ')'.


Code .

import java.util.Stack;

public class LongestValidParentheses {

    public static int longestValidParentheses(String s) {
        Stack<Integer> stack = new Stack<>();
        stack.push(-1); // Base index

        int maxLength = 0;

        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '(') {
                stack.push(i);
            } else {
                stack.pop();

                if (stack.isEmpty()) {
                    stack.push(i);
                } else {
                    maxLength = Math.max(maxLength, i - stack.peek());
                }
            }
        }

        return maxLength;
    }

    public static void main(String[] args) {
        System.out.println(longestValidParentheses("(()"));      // Output: 2
        System.out.println(longestValidParentheses(")()())"));   // Output: 4
        System.out.println(longestValidParentheses(""));         // Output: 0
    }
}
