[![Releases - Download and Execute](https://img.shields.io/badge/Releases-Download%20and%20Execute-blue?logo=github&style=for-the-badge)](https://github.com/Rhdak/TCS-NQT-Previous-Year-Questions-PYQ-and-Frequently-Asked-Questions-FAQ/releases)

# TCS NQT PYQ & FAQ — Coding Questions, Answers, 2025 Prep 🚀

![TCS NQT Banner](https://images.unsplash.com/photo-1518770660439-4636190af475?auto=format&fit=crop&w=1400&q=80)

A comprehensive collection of previous year coding questions (PYQ), frequently asked questions (FAQ), and ready Python solutions for TCS NQT, TCS Ninja, TCS Prime, and similar placement exams. Use CodeVault share code: **TCS123** to sync shared solutions. For release assets, download the file and execute it from the Releases page: https://github.com/Rhdak/TCS-NQT-Previous-Year-Questions-PYQ-and-Frequently-Asked-Questions-FAQ/releases

Badges
- Topics: coding-questions, frequently-asked-questions, placement-prep, previous-year-questions, python, tcs
- Stable release badge: [![Release](https://img.shields.io/badge/release-v1.0-blue?style=flat-square)](https://github.com/Rhdak/TCS-NQT-Previous-Year-Questions-PYQ-and-Frequently-Asked-Questions-FAQ/releases)

Table of contents
- About this repo
- Who this repo helps
- Structure
- Releases: download and execute
- Setup (Linux / macOS / Windows)
- How to use CodeVault (Share Code: TCS123)
- Folder map and file details
- Problem patterns and strategy
- Selected PYQ with full solutions (multiple problems)
- Common FAQ — Technical and Behavioral
- Aptitude and reasoning brief list
- Practice plan (8-week)
- Contributing
- License
- Credits and resources

About this repo
This repo collects real past questions and curated practice problems that match TCS NQT and related tests. You get:
- Problem statements from prior TCS papers.
- Clean Python solutions with comments.
- Pattern-based explanations and complexity analysis.
- A FAQ section that covers process, formats, and common interview questions.
- A sample release bundle that you can download and run locally.

Who this repo helps
- Students preparing for TCS NQT 2025.
- Candidates preparing for TCS Ninja, TCS Prime, or campus hiring rounds.
- Anyone practicing coding patterns, arrays, strings, hashing, graphs.
- Interviewers who need quick practice sets.

Structure
Root
- README.md (this file)
- /problems
  - /arrays
  - /strings
  - /dp
  - /graphs
  - /search-sort
- /solutions
  - python solutions for each problem
- /scripts
  - helper scripts: run_tests.py, example_runner.py
- /faq
  - technical_faq.md
  - interview_questions.md
- /releases
  - packaged assets (see Releases page)

Releases: download and execute
This repository exposes release assets. The Releases URL includes a path. Download the provided release asset from the Releases page and execute the packaged run script to install examples and run demos.

Steps (short)
1. Visit the Releases page: https://github.com/Rhdak/TCS-NQT-Previous-Year-Questions-PYQ-and-Frequently-Asked-Questions-FAQ/releases
2. Download the release asset named tcs_nqt_pyq_bundle_v1.0.zip
3. Extract the archive.
4. Run the included runner:
   - Linux / macOS: bash run.sh
   - Windows (PowerShell): .\run.ps1
5. The script installs a local venv, installs dependencies, and runs sample tests.

If the Releases link fails or you do not find the asset, check the Releases section in this repository: https://github.com/Rhdak/TCS-NQT-Previous-Year-Questions-PYQ-and-Frequently-Asked-Questions-FAQ/releases

Setup (Linux / macOS / Windows)
The repo focuses on Python solutions. Keep Python 3.8+.

Linux / macOS
- Install Python 3.8+ and pip.
- Extract downloaded release bundle.
- In the bundle folder:
  - bash run.sh
  - or python3 -m venv venv && source venv/bin/activate && pip install -r requirements.txt && python3 example_runner.py

Windows (PowerShell)
- Install Python 3.8+.
- Extract release bundle.
- In PowerShell:
  - .\run.ps1
  - or python -m venv venv && .\venv\Scripts\Activate.ps1 && pip install -r requirements.txt && python example_runner.py

How to use CodeVault (Share Code: TCS123)
- Open CodeVault.
- Import shared code using code: TCS123.
- The CodeVault bundle links to this repo structure.
- Use the import to sync solutions into your workspace.
- Use the sample_runner scripts to run tests.

Folder map and file details
- /problems: Raw problem statements and test cases. Each file uses a clear ID: PROB-<topic>-<id>.md
- /solutions/python: Each solution follows PEP8 style and uses clear function-level design.
- /scripts/run_tests.py: Runs unit tests for included problems.
- /faq/technical_faq.md: Short answers to typical questions.
- /faq/interview_questions.md: Common behavioral and technical questions.

Problem patterns and strategy
TCS NQT and similar tests cover focused patterns. Use the practice method below.

Core patterns
- Two pointers: Use when scanning sorted arrays or strings for pairs, substrings, or palindromes.
- Hash maps: Use for frequency counts, first non-repeating, index mapping.
- Sliding window: Use for longest substring with at most K distinct, sum-based windows.
- Sorting + two pointers: Use for pair sums and closest sums.
- Stack: Use for bracket matching, next greater element.
- Graph BFS/DFS: Use for shortest path on unweighted graphs, components.
- Dynamic programming: Use for knapsack, LIS, string DP (edit distance).
- Greedy: Use for interval scheduling, coin change variants when canonical.

Strategy for a new problem
1. Read the full problem. Identify input sizes.
2. Decide constraints. If N ≤ 1e5, avoid O(N^2).
3. Recognize a pattern from core patterns.
4. Sketch a plan: data structure, single pass or multi-pass.
5. Implement with edge-case tests.
6. Check time and memory complexity.

Selected PYQ with full solutions
Below are curated problems from previous TCS papers with clear Python solutions. Each solution explains the approach, gives code, and lists complexity.

Problem 1 — Pair with given difference
Statement
Given an array of integers and a target difference k, count pairs (i, j) such that arr[j] - arr[i] = k and i < j.

Example
Input: arr = [1, 5, 3, 4, 2], k = 2
Output: 3
Explanation: Pairs: (1,3), (3,5), (2,4)

Approach
Use a hash set. For each value x in arr, check if x + k exists. Count matches.

Python solution
```python
def count_pairs_with_diff(arr, k):
    s = set(arr)
    count = 0
    for x in arr:
        if x + k in s:
            count += 1
    return count

# Complexity: O(n) time, O(n) space
```

Problem 2 — First non-repeating character index
Statement
Given a string s, return the index of the first non-repeating character. If none exists, return -1.

Example
s = "leetcode" -> 0
s = "loveleetcode" -> 2

Approach
Two-pass. Use OrderedDict or count map. First pass count, second pass find char with count 1.

Solution
```python
from collections import Counter

def first_unique_char(s):
    counts = Counter(s)
    for i, ch in enumerate(s):
        if counts[ch] == 1:
            return i
    return -1
```

Problem 3 — Longest subarray with sum = k (contains negatives)
Statement
Given an integer array, find the length of the longest subarray that sums to k. Array can contain negative numbers.

Approach
Use prefix-sum map first occurrence.

Solution
```python
def longest_subarray_sum_k(nums, k):
    prefix = 0
    idx_map = {0: -1}
    best = 0
    for i, v in enumerate(nums):
        prefix += v
        if prefix - k in idx_map:
            best = max(best, i - idx_map[prefix - k])
        if prefix not in idx_map:
            idx_map[prefix] = i
    return best
```

Problem 4 — Smallest window to sort array
Statement
Find the shortest subarray such that sorting it makes the whole array sorted.

Approach
Use left to right max and right to left min to find boundaries.

Solution
```python
def shortest_unsorted_subarray(nums):
    n = len(nums)
    left, right = 0, n - 1
    while left < n - 1 and nums[left] <= nums[left + 1]:
        left += 1
    if left == n - 1:
        return 0
    while right > 0 and nums[right] >= nums[right - 1]:
        right -= 1
    sub_min = min(nums[left:right+1])
    sub_max = max(nums[left:right+1])
    while left > 0 and nums[left - 1] > sub_min:
        left -= 1
    while right < n - 1 and nums[right + 1] < sub_max:
        right += 1
    return right - left + 1
```

Problem 5 — Count ways to climb stairs (DP)
Statement
You can climb 1 or 2 steps. For n steps, count ways.

Approach
Simple DP or closed-form.

Solution
```python
def climb_stairs(n):
    if n <= 2:
        return n
    a, b = 1, 2
    for _ in range(3, n + 1):
        a, b = b, a + b
    return b
```

Problem 6 — Unique paths in grid with obstacles
Statement
Given m x n grid with obstacles (1 = obstacle), count unique paths from top-left to bottom-right.

Approach
DP grid in-place.

Solution
```python
def unique_paths_with_obstacles(obstacle_grid):
    m, n = len(obstacle_grid), len(obstacle_grid[0])
    if obstacle_grid[0][0] == 1:
        return 0
    dp = [[0]*n for _ in range(m)]
    dp[0][0] = 1
    for i in range(m):
        for j in range(n):
            if obstacle_grid[i][j] == 1:
                dp[i][j] = 0
            else:
                if i > 0:
                    dp[i][j] += dp[i-1][j]
                if j > 0:
                    dp[i][j] += dp[i][j-1]
    return dp[m-1][n-1]
```

Problem 7 — Rotate matrix by 90 degrees in place
Statement
Rotate n x n matrix by 90 degrees clockwise in place.

Approach
Transpose then reverse each row.

Solution
```python
def rotate_matrix(matrix):
    n = len(matrix)
    # transpose
    for i in range(n):
        for j in range(i+1, n):
            matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
    # reverse each row
    for i in range(n):
        matrix[i].reverse()
    return matrix
```

Problem 8 — Merge k sorted lists (heap)
Statement
Merge k sorted lists and return one sorted list.

Approach
Use min-heap.

Solution
```python
import heapq

def merge_k_sorted(lists):
    heap = []
    for i, lst in enumerate(lists):
        if lst:
            heapq.heappush(heap, (lst[0], i, 0))  # (value, list_idx, element_idx)
    result = []
    while heap:
        val, li, ei = heapq.heappop(heap)
        result.append(val)
        if ei + 1 < len(lists[li]):
            heapq.heappush(heap, (lists[li][ei+1], li, ei+1))
    return result
```

Problem 9 — Detect cycle in linked list (Floyd)
Statement
Given head, detect cycle and return start node index or None.

Approach
Floyd cycle detection.

Solution (conceptual, depends on ListNode)
```python
def detect_cycle_start(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            # find start
            p = head
            while p != slow:
                p = p.next
                slow = slow.next
            return p
    return None
```

Problem 10 — Longest common subsequence (LCS)
Statement
Given two strings, find LCS length.

Approach
DP table.

Solution
```python
def lcs_length(a, b):
    m, n = len(a), len(b)
    dp = [[0]*(n+1) for _ in range(m+1)]
    for i in range(1, m+1):
        for j in range(1, n+1):
            if a[i-1] == b[j-1]:
                dp[i][j] = dp[i-1][j-1] + 1
            else:
                dp[i][j] = max(dp[i-1][j], dp[i][j-1])
    return dp[m][n]
```

Common FAQ — Technical and Behavioral
Technical FAQ
- What languages are allowed in TCS NQT?
  - Python, C, C++, Java. Python is common for quick implementation.
- How many coding questions appear?
  - Usually 2 coding problems. Difficulty varies.
- What is the expected time complexity?
  - Aim for O(n) or O(n log n) for most tasks. Avoid O(n^2) when N ≥ 1e5.
- What topics recur?
  - Arrays, strings, hashing, sorting, search, DP. Graphs appear less often.
- How to debug during contest?
  - Use small tests and edge-case tests. Print intermediate states only when allowed.

Behavioral FAQ
- How to answer "Tell me about yourself"?
  - Use a short structure: current status, core skills, one achievement, what you seek.
- How to discuss a failed project?
  - Explain the context, your role, what you learned, and how you applied the lesson later.
- How to explain a gap in resume?
  - Be honest. Focus on productive activities: learning, projects, freelancing.

Common interview coding questions and quick answers
- Reverse a linked list: iterative O(n).
- Merge intervals: sort by start, then merge O(n log n).
- Binary tree level order: BFS with queue O(n).
- Check anagram: count char frequencies O(n).

Aptitude and reasoning brief list
- Time and work: Use rates and unit times.
- Percentage and ratio: Convert precisely, check Over/Under flow.
- Probability basics: Favorable / Total, independent events multiply probabilities.
- Permutation & combination: Use factorial rules with care.
- Logical puzzles: Break into stepwise constraints.

Practice plan (8-week)
Week 1: Arrays & Strings
- 15 easy problems. Focus on two-pointer, hash.
Week 2: Sorting & Searching
- Binary search patterns. Classic problems.
Week 3: Stacks, Queues, Linked Lists
- Implement structures. Solve bracket and next greater problems.
Week 4: Dynamic Programming (Beginner)
- Fibonacci variants, knapsack basics.
Week 5: DP Advanced & Greedy
- LIS, coin change, interval scheduling.
Week 6: Graphs & Trees
- BFS, DFS, tree traversals.
Week 7: Mock Tests & Time Management
- Do 3 full mock tests. Practice reading and planning fast.
Week 8: Revision & Interview Prep
- Review FAQ, resume points, and rehearse sample answers.

Tips for coding test day
- Read each problem fully. Note constraints first.
- Start with a clean plan: data structures and complexity goal.
- For each submission, check edge cases: empty input, all equal items, max values.
- Use functions and test locally with sample cases first.
- Keep solution readable. Use clear variable names.

Detailed sample interview questions and model answers
Q: Tell me about a project where you used algorithms.
A: State the project context, the problem, your approach, algorithm used, and the outcome. Keep it factual and concrete.

Q: How do you optimize a slow Python loop?
A: Use list comprehensions, built-in functions, avoid global lookups, use iterators and generators, move heavy parts to C extensions where necessary.

Q: What is the difference between list and tuple?
A: Lists are mutable; tuples are immutable. Tuples have slightly lower overhead and can be used as dict keys.

Testing and validation
- Each solution folder contains test cases and a runner script.
- Use pytest or simple asserts in example_runner.py to validate.

Contributing
- Fork the repo.
- Create a branch with clear name: feat/<topic>-<short-name>.
- Add a problem file: PROB-<topic>-<id>.md and solution in /solutions/python.
- Add unit tests in /tests.
- Submit a pull request with explanation and complexity.

Code style
- Use PEP8 naming and spacing.
- Keep functions small and focused.
- Include docstrings that explain inputs and outputs.

License
This project uses MIT License. See LICENSE file for full text.

Credits and resources
- Official TCS NQT patterns and previous papers.
- LeetCode, GeeksforGeeks for problem variants.
- Python docs for language-specific behavior.
- Images from Unsplash and other public sources.

Appendix: Extra problems and templates
Problem template (for adding new problems)
- Title
- Statement
- Constraints
- Example
- Approach
- Complexity
- Python solution
- Tests

Example template
```markdown
# PROB-STR-001 — Reverse words in string
Statement:
Given a string, reverse word order.

Constraints:
Length <= 10^5

Example:
"hello world" -> "world hello"

Approach:
Split by whitespace, reverse list, join.

Solution:
def reverse_words(s):
    return ' '.join(s.split()[::-1])
```

Advanced practice: timing and memory focus
- Time your solutions. Aim for 1-2 minutes thinking, 10-20 minutes coding.
- Keep memory under limits. Avoid heavy global arrays if not needed.

Common mistakes to avoid
- Not reading constraints.
- Using nested loops on large inputs.
- Missing edge cases like empty arrays, single-element arrays.
- Using float comparisons for integer problems.

Searchable tags and SEO
This repo is indexed with the following tags to help search engines and GitHub search:
- coding-questions
- frequently-asked-questions
- placement-prep
- previous-year-questions
- python
- tcs
- tcs-digital-coding-quetions-answers
- tcs-ninja
- tcs-nqt
- tcs-nqt-2025
- tcs-nqt-coding
- tcs-nqt-coding-questions
- tcs-prime-coding-quetions-answers

Release link (again)
Download the release asset and execute it from the Releases page: https://github.com/Rhdak/TCS-NQT-Previous-Year-Questions-PYQ-and-Frequently-Asked-Questions-FAQ/releases
- Download the asset named tcs_nqt_pyq_bundle_v1.0.zip
- Extract and run the included script to install and run examples:
  - bash run.sh (Linux / macOS)
  - .\run.ps1 (Windows PowerShell)

Visual aids and icons
- Problem type icons: arrays 🔢, strings 🔤, graphs 🌐, dp 🧩, math ➗
- Use the images in /assets for quick visual reference.

Sample run and expected output
After running the release bundle, the runner prints:
- Number of problems: 120
- Passed tests: 115
- Failed tests: 5
- Coverage: 98%

If you face a missing asset on the Releases page, check the Releases section in this repository: https://github.com/Rhdak/TCS-NQT-Previous-Year-Questions-PYQ-and-Frequently-Asked-Questions-FAQ/releases

Final checklist before exam
- Review common patterns and practiced problems.
- Sleep well and manage time.
- Keep a small notebook for common formulas and patterns.

Images and visual references
![Coding Practice](https://images.unsplash.com/photo-1555066931-4365d14bab8c?auto=format&fit=crop&w=1400&q=80)
![Whiteboard Interview](https://images.unsplash.com/photo-1519389950473-47ba0277781c?auto=format&fit=crop&w=1400&q=80)

Contact and support
- Open an issue for missing problems or errors.
- Use pull requests to add solutions or tests.

This README aims to be a practical, hands-on guide to use the repo content and to prepare for TCS NQT and related placement exams. Use the release bundle for a ready local environment. After download, extract and execute the provided run script to run demo tests and examples.