# LC304 - Range Sum Query 2D Immutable

## Pattern

Prefix Sum → 2D Prefix Sum

Difficulty: Medium

---

# Why Does This Pattern Exist?

In 1D Prefix Sum, we answer:

```text
Sum from index L to R
```

efficiently.

Example:

```text
[1,2,3,4,5]
```

Query:

```text
Sum(1,3)
```

can be answered in O(1).

But what if data is stored as:

```text
Rows
+
Columns
```

like a matrix?

```text
1 2 3
4 5 6
7 8 9
```

Now interviewer asks:

```text
Find sum of rectangle

(1,1)

to

(2,2)
```

Brute force works.

But multiple queries become expensive.

We need:

```text
O(1) Query Time
```

This is exactly why 2D Prefix Sum exists.

---

# Core Intuition

## 1D Prefix Sum

We store:

```text
Prefix[i]

=

Sum from start

to i
```

Example:

```text
Array

[1,2,3,4]

Prefix

[1,3,6,10]
```

---

## 2D Prefix Sum

We store:

```text
Prefix[r][c]

=

Sum of rectangle

(0,0)

to

(r,c)
```

Think:

```text
Every cell remembers
everything above it
and everything left of it.
```

---

# Recognition Signals

Think 2D Prefix Sum when you see:

* Matrix Range Query
* Rectangle Sum
* Multiple Queries
* Immutable Matrix
* Sum of Submatrix
* Rectangular Region

Keywords:

```text
matrix

submatrix

rectangle

range sum

query
```

---

# Mental Model

When you see:

```text
Matrix
+
Rectangle Query
```

Immediately think:

```text
Can I precompute
rectangle sums?
```

If yes:

```text
2D Prefix Sum
```

---

# Building The Prefix Matrix

Suppose:

```text
1 2 3

4 5 6

7 8 9
```

---

## What does Prefix[1][1] mean?

Rectangle:

```text
1 2

4 5
```

Sum:

```text
1+2+4+5

=

12
```

Therefore:

```text
Prefix[1][1]

=

12
```

---

## Meaning

```text
Prefix[r][c]

=

Sum of entire rectangle

from

(0,0)

to

(r,c)
```

---

# Building Formula

For every cell:

```text
Prefix[r][c]

=

Matrix[r][c]

+

Prefix[r-1][c]

+

Prefix[r][c-1]

-

Prefix[r-1][c-1]
```

---

# Why Subtract?

This is the most important concept.

Visual:

```text
+-------+
|   A   |
+---+---+
| B | C |
+---+---+
```

When we add:

```text
Top Rectangle

+

Left Rectangle
```

Region A gets counted twice.

Therefore:

```text
Top

+

Left

-

Overlap

+

Current Cell
```

---

# Visual Dry Run

Matrix:

```text
1 2 3

4 5 6

7 8 9
```

---

## Cell (0,0)

```text
Prefix

=

1
```

Current Prefix Matrix:

```text
1
```

---

## Cell (0,1)

```text
1+2

=

3
```

Current:

```text
1 3
```

---

## Cell (0,2)

```text
1+2+3

=

6
```

Current:

```text
1 3 6
```

---

## Cell (1,0)

```text
1+4

=

5
```

Current:

```text
1
5
```

---

## Cell (1,1)

Formula:

```text
Current

+

Top

+

Left

-

Overlap
```

Values:

```text
5

+

3

+

5

-

1
```

Result:

```text
12
```

---

## Cell (1,2)

Values:

```text
6

+

6

+

12

-

3
```

Result:

```text
21
```

---

## Cell (2,0)

```text
7+5

=

12
```

---

## Cell (2,1)

```text
8+12+12-5

=

27
```

---

## Cell (2,2)

```text
9+21+27-12

=

45
```

---

# Final Prefix Matrix

```text
1   3   6

5  12  21

12 27  45
```

---

# The Real Power

Suppose interviewer asks:

```text
Find sum of rectangle

(1,1)

to

(2,2)
```

Highlighted:

```text
1 2 3

4 [5 6]

7 [8 9]
```

Expected:

```text
5+6+8+9

=

28
```

---

# Rectangle Query Formula

```text
Answer

=

Prefix[row2][col2]

-

Prefix[row1-1][col2]

-

Prefix[row2][col1-1]

+

Prefix[row1-1][col1-1]
```

---

# Why This Formula Works

Take:

```text
Entire Rectangle
```

Remove:

```text
Top Area
```

Remove:

```text
Left Area
```

Oops.

Overlap removed twice.

Add overlap back.

Visual:

```text
Big

-

Top

-

Left

+

Overlap
```

This is called:

```text
Inclusion-Exclusion Principle
```

---

# Query Dry Run

Need:

```text
(1,1)

to

(2,2)
```

Formula:

```text
Prefix[2][2]

-

Prefix[0][2]

-

Prefix[2][0]

+

Prefix[0][0]
```

Values:

```text
45

-

6

-

12

+

1
```

Result:

```text
28
```

Correct.

---

# Code

```java
class NumMatrix {

    int pre[][];

    public NumMatrix(int[][] matrix) {

        int row=matrix.length;
        int col=matrix[0].length;

        pre=new int[row][col];

        for(int r=0;r<row;r++){
            for(int c=0;c<col;c++){

                int top=(r>0)?pre[r-1][c]:0;
                int left=(c>0)?pre[r][c-1]:0;
                int overlap=(r>0 && c>0)?pre[r-1][c-1]:0;

                pre[r][c]=matrix[r][c]+top+left-overlap;
            }
        }
    }
    
    public int sumRegion(int row1, int col1, int row2, int col2) {
        int big=pre[row2][col2];

        int top=(row1>0)?pre[row1-1][col2]:0;
        int left=(col1>0)?pre[row2][col1-1]:0;
        int overlap=(row1>0 && col1>0)?pre[row1-1][col1-1]:0;

        return big-top-left+overlap;
    }
}

```

---

# Complexity Analysis

## Building Prefix Matrix

```text
O(R × C)
```

where:

```text
R = Rows
C = Columns
```

---

## Query Time

```text
O(1)
```

Only four lookups.

---

## Space Complexity

```text
O(R × C)
```

For storing prefix matrix.

---

# Common Mistakes

## Mistake 1

Forgetting:

```text
- overlap
```

while building prefix.

---

## Mistake 2

Forgetting:

```text
+ overlap
```

during query.

---

## Mistake 3

Memorizing formula without understanding.

Remember:

```text
Big

-

Top

-

Left

+

Overlap
```

Everything comes from this.

---

# Interview Explanation

"I precompute a 2D Prefix Sum matrix where each cell stores the sum of the rectangle from the top-left corner to that cell. Then for any rectangle query, I use inclusion-exclusion to remove extra regions and add back the overlap. This allows O(1) query time after O(rows × cols) preprocessing."

---

# Pattern Tracker

```text
Pattern:
2D Prefix Sum

Problem:
LC304

Recognition Signal:
Matrix Range Query

Core Observation:
Store rectangle sums.

Building Formula:
Current + Top + Left - Overlap

Query Formula:
Big - Top - Left + Overlap

Time:
Build → O(R×C)

Query → O(1)

Space:
O(R×C)

Key Insight:
Use Inclusion-Exclusion.
```

---

# Revision Sheet

```text
Recognition Signal

Matrix
+
Rectangle Query
+
Multiple Queries

↓

Use 2D Prefix Sum


Build Formula

Current
+
Top
+
Left
-
Overlap


Query Formula

Big
-
Top
-
Left
+
Overlap


Time

Build → O(R×C)

Query → O(1)


Golden Idea

Store rectangle information
once and reuse forever.
```
