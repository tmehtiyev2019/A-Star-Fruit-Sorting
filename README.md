 # Fruit Sorting- A Star Algorithm

This code implements an A* algorithm to solve a fruit sorting problem. The goal is to sort the fruits in three baskets, each containing ten fruits, in ascending order based on their sizes.

**Problem Description**

The initial state consists of three baskets, each containing a list of fruits along with their corresponding sizes. The sizes are represented as tuples, where the first element is the fruit type (e.g., 'apple', 'banana', or 'orange'), and the second element is the size. The initial state of the baskets is as follows:

```
Initial State:
[[('apple', 3), ('apple', 1), ('apple', 8), ('apple', 4), ('apple', 7), ('banana', 10), ('banana', 5), ('banana', 1), ('banana', 8), ('banana', 3)],
[('banana', 4), ('banana', 7), ('banana', 2), ('banana', 9), ('banana', 6), ('orange', 3), ('orange', 4), ('orange', 7), ('orange', 2), ('orange', 9)],
[('orange', 6), ('orange', 10), ('orange', 5), ('orange', 1), ('orange', 8), ('apple', 2), ('apple', 9), ('apple', 6), ('apple', 10), ('apple', 5)]] 
```


**Approach**

The main trick in this code is to normalize the sizes of the fruits to a **scale of 1 to 30**. Each fruit type ('apple', 'banana', 'orange') is assigned a specific range within this scale. The normalization is done by mapping the original sizes to the desired range based on the fruit type.

To achieve this, the code provides two helper functions: `normalize_and_sort and group_and_normalize`.

` normalize_and_sort`: This function takes a list of fruit sizes, along with the minimum and maximum values for normalization. It normalizes the sizes within the given range and returns a list of normalized sizes. This function is used to normalize the sizes for each fruit type.

`group_and_normalize`: This function takes the initial state of the baskets, along with the order of fruit types, as input. It flattens the initial state, groups the fruits by type, and normalizes their sizes using the normalize_and_sort function. The function replaces the original sizes with the normalized sizes in the original data structure and returns the normalized initial state.

After normalizing the initial state, the A* algorithm is used to find the minimum number of moves required to reach the goal state. The A* algorithm utilizes a heuristic function to estimate the number of moves required. In this case, the **heuristic function calculates the distance between the current state and the sorted list of fruits**.

The code also provides the possible_moves function, which generates all possible next states from a given state. It considers both horizontal and vertical swaps of fruits within the baskets.

**Output**

```
Denormalized Initial State
[('apple', 3), ('apple', 1), ('apple', 8), ('apple', 4), ('apple', 7), ('banana', 10), ('banana', 5), ('banana', 1), ('banana', 8), ('banana', 3)]
[('banana', 4), ('banana', 7), ('banana', 2), ('banana', 9), ('banana', 6), ('orange', 3), ('orange', 4), ('orange', 7), ('orange', 2), ('orange', 9)]
[('orange', 6), ('orange', 10), ('orange', 5), ('orange', 1), ('orange', 8), ('apple', 2), ('apple', 9), ('apple', 6), ('apple', 10), ('apple', 5)]


Normalized Initial State
[13, 11, 18, 14, 17, 10, 5, 1, 8, 3]
[4, 7, 2, 9, 6, 23, 24, 27, 22, 29]
[26, 30, 25, 21, 28, 12, 19, 16, 20, 15]


Normalized end state
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
[11, 12, 13, 14, 15, 16, 17, 18, 19, 20]
[21, 22, 23, 24, 25, 26, 27, 28, 29, 30]


Denormalized end state
[('banana', 1), ('banana', 2), ('banana', 3), ('banana', 4), ('banana', 5), ('banana', 6), ('banana', 7), ('banana', 8), ('banana', 9), ('banana', 10)]
[('apple', 1), ('apple', 2), ('apple', 3), ('apple', 4), ('apple', 5), ('apple', 6), ('apple', 7), ('apple', 8), ('apple', 9), ('apple', 10)]
[('orange', 1), ('orange', 2), ('orange', 3), ('orange', 4), ('orange', 5), ('orange', 6), ('orange', 7), ('orange', 8), ('orange', 9), ('orange', 10)]


Minimum number of moves: 73
```
