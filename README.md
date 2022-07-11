# Quick Guide

This book contains solutions to the leetcode problems.\
\
<mark style="color:blue;">**Why this book?**</mark>\
****\
****I know many people have already posted repositories for leetcode solutions online.

But few of my intentions behind this book were:

* Keep track of work and be consistent.
* Structured content, concise explanation and multiple approaches to the problem, wherever required.
* Easier documentation of thoughts in form of a multiple pages book.
* Keep it as a public work.
* Reference solutions for later.

<mark style="color:blue;">**How is this book different than others?**</mark>\
****\
****I have tried to structure the content based on certain criteria like patterns, data structures, algorithms and level. This will speed up learning and could be useful for spaced repetition, where anyone can revisit the topic they want and brush up. _Since a problem can belong to muti categories, I have given priority to patterns and algorithms over chosen data structures._\
\
<mark style="color:blue;">**How can I find a particular LC question?**</mark>

Since, the solutions are not posted in order, the reader has to search for particular problem. Luckily, Gitbook have a nice search functionality. You can either look with leetcode question number or problem name.

### Language

```python
if  __name__ == "__main__":
    print("Data Structure and problem solving is language agnostic")
```

**So, solutions will be posted in Python3**. I know majority of repositories are either in C++ or Java,\
but given the simplicity of Python, it would still be easier to understand if you are from different coding background. ;)

### Time and Space Complexity

_This is a sample code:_

```python
// TC - O(n)
// SC - O(1)
def test_code(arr):
    n = len(arr)
    for _ in range(n):
        print("sample code")
```

**I would only estimate extra space initialised by us to calculate space complexity**. This is because each program needs some space to run, but for better comparison of algorithm's overhead, we consider extra space initiated by us during runtime of program.\
\
Here in the given example, arr takes n space. But this is not considered here to calculate space complexity. _Look at line no, 4-6 in the code block above to calculate extra space complexity_. We have not initiated any new data structure (array, stack) in the memory to solve this problem. So, space complexity remains O(1)

For ease of calculating time complexity, **we will look for the number of traversals/iterations made**. <mark style="color:orange;">Always try to calculate complexity based on approach.</mark>

### Test Cases & Online Editor

I have used leetcode compiler to test the code. I have made submissions on leetcode before posting solutions here.

### Pace of Completion

This is a WIP pretty much. I will keep posting solutions as I move forward.  \


_This is an open-source work. Please feel free to correct and make any contributions._
