# LeetCode 20 - Valid Parentheses

## Problem

Given a string `s` containing only the characters:

```text
( ) { } [ ]
```

Determine if the input string is valid.

A string is valid if:

* Every opening bracket has a corresponding closing bracket.
* Brackets are closed in the correct order.
* Every closing bracket matches the most recent unmatched opening bracket.

---

## Example 1

```python
s = "()"
```

Output:

```python
True
```

---

## Example 2

```python
s = "()[]{}"
```

Output:

```python
True
```

---

## Example 3

```python
s = "(]"
```

Output:

```python
False
```

---

## Pattern Used

* Stack
* LIFO (Last In, First Out)

---

## Intuition

A stack follows the **Last In, First Out (LIFO)** principle.

* Push every opening bracket onto the stack.
* When a closing bracket appears, check whether it matches the top element of the stack.
* If it matches, remove the opening bracket from the stack.
* If it doesn't match or the stack is empty, the string is invalid.
* At the end, the stack must be empty for the string to be valid.

---

## Approach

1. Create an empty stack.
2. Create a dictionary to map each closing bracket to its corresponding opening bracket.
3. Traverse the string one character at a time.
4. If the character is an opening bracket, push it onto the stack.
5. If the character is a closing bracket:

   * Return `False` if the stack is empty.
   * Pop the top element from the stack.
   * Compare it with the expected opening bracket.
   * Return `False` if they do not match.
6. After processing all characters, return `True` only if the stack is empty.

---

## Python Solution

```python
class Solution(object):
    def isValid(self, s):
        stack = []

        mapping = {
            ')': '(',
            ']': '[',
            '}': '{'
        }

        for ch in s:

            if ch in "([{":
                stack.append(ch)

            else:
                if not stack:
                    return False

                top = stack.pop()

                if top != mapping[ch]:
                    return False

        return len(stack) == 0
```

---

## Time Complexity

* **O(n)**

Each character is processed only once.

---

## Space Complexity

* **O(n)**

In the worst case, all opening brackets are stored in the stack.

---

## What I Learned

* How the **Stack** data structure follows the **LIFO (Last In, First Out)** principle.
* How to use Python lists as stacks with `append()` and `pop()`.
* How to match opening and closing brackets efficiently.
* Why a dictionary simplifies bracket matching.
* How Stack is used to solve expression and parentheses-related interview problems.
