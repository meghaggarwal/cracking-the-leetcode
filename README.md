# Quick Guide

This book contains solutions and guide to solve leetcode problems.

Github Repository - [https://github.com/meghaggarwal/cracking-the-leetcode](https://github.com/meghaggarwal/cracking-the-leetcode)

Gitbook - [https://megha-aggarwal.gitbook.io/cracking-the-leetcode](https://megha-aggarwal.gitbook.io/cracking-the-leetcode)

### Why this book❓

I know many people have already posted repositories for leetcode solutions online. 

But few of my intentions behind this book were:

* Keep track of work and be consistent.
* Structured content, concise explanation and multiple approaches to the problem, wherever required.
* Easier documentation of thoughts in form of a multiple pages book.
* Keep it as a public work.
* Reference solutions for later.

### How is this different than others repositories❓

Rather than simply posting solutions, I have written brief thoughts and intutions behind to approach the problem. It makes easier to understand next time we revisit the problem.

Ease of navigation and more structured content in form of book. This will speed up learning and could be useful for spaced repetition, where anyone can revisit the topic they want and brush up. 

### How can I find a particular leetcode question ❓

Since, the solutions are not in order, the reader has to search for particular problem. Luckily, Gitbook have a nice search functionality. You can either look with leetcode question number or problem name.

### Why Python❓

```python
if  __name__ == "__main__":
    print("Data Structure and problem solving is language agnostic")
```

I know majority of repositories are either in C++ or Java, but given the simplicity of Python, it would still be easier to understand if you are from different coding background.  Our first major goal is to learn, and I believe language should be no barrier for it.

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

For ease of calculating time complexity, **we will look for the number of traversals/iterations made**. <mark style="color:purple;">Always try to calculate complexity based on approach.</mark> 

### Test Cases & Online Editor
 I have made submissions on leetcode before posting solutions here.

### Pace of Completion

This is a WIP pretty much. I will keep posting solutions as I move forward. ⻌

_This is an open-source work. Please feel free to correct and make any contributions._ 🙈 🙂

_Disclamier: The intent of this repository is not to provide the most optimised code. I'm afraid I'll be able to do so, since there is always scope of improvement. My motivation is to learn along the way, have fun and not grind problems._ 😉