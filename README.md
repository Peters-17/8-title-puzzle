# 8-title-puzzle
Score 100/100
# Assignment Goals
● Deepen understanding of state space generation.

● Practice implementation of an efficient search algorithm.
# Summary
This assignment is about solving a variant of the 8-tile puzzle that we have discussed in class. The
8-tile puzzle was invented and popularized by Noyes Palmer Chapman in the 1870s. The version we
will consider in this homework is played on a 3x3 grid with 7 tiles labeled 1 through 7 and two empty
grids. The goal is to rearrange the tiles so that they are in order and the empty places are at the
bottom right.
You solve the puzzle by moving the tiles around. For each step, you can only move one (not more!)
of the neighbor tiles (left, right, top, bottom but not diagonally) into an empty grid. And all tiles must
stay in the 3x3 grid (so no wrap around allowed). An example is shown in the picture below. Suppose
we start from the following configuration:
![image](https://user-images.githubusercontent.com/85666623/187548073-eb71b245-7b8f-4423-a69d-d24013e207b8.png)



# Program Specification
The code for this program should be written in Python, in a file called funny_puzzle.py. We will
provide states in a one-dimensional list of integers, with the empty spaces represented as 0. For
example, in the picture above, the initial state is represented by [2,5,1,4,3,6,7,0,0] and its
successors are [2,5,1,4,0,6,7,3,0],[2,5,1,4,3,0,7,0,6],[2,5,1,4,3,6,0,7,0].
In this assignment, you will need a priority queue. We highly recommend using the package heapq
for the implementation. You should refer to heapq if you are not familiar with it.

# Heuristic
Since we are using the A* search algorithm, we need a heuristic function h(s). Recall the Manhattan
distance mentioned in lecture (the l1-norm). We will use the sum of Manhattan distance of each tile to
its goal position as our heuristic function. The Manhattan distance of two tiles in this case is the
absolute difference between their x coordinates plus the absolute distance between their y
coordinates.
In our first example puzzle ([2,5,1,4,3,6,7,0,0]) , the h() is 6. This is computed by calculating
the Manhattan distance of each title and summing them. Specifically, tiles 4/6/7 are already in place,
thus they have 0 distances. Tile 1 has a Manhattan distance of 2 (manhattan([0,2], [0,0]) = abs(0-0) +
abs(2-0) = 2), tiles 2/3/5 have distances of 1/2/1, respectively.
Caution: do not count the distance of tiles '0' since they are actually not tiles but are empty sections.
# Functions
For this program you need to write two (2) Python functions:
1. print_succ(state) — given a state of the puzzle, represented as a single list of integers
with a 0 in the empty spaces, print to the console all of the possible successor states.
2. solve(state) — given a state of the puzzle, perform the A* search algorithm and print the
path from the current state to the goal state.
You may, of course, add any other functions you see fit, but these two functions must be present and
work as described here.
