# Lab 1 - Francesco Sorrentino

You can find my solution into the file lab1_notebook.

Here some considerations:

| N | nodes processed | state visited | n of elements (w) | 
|---|---|---|---|
| 5 | 5 | 18 | 5 |
| 10 | 8 | 335 | 10 |
| 20 | 1110 | 37.700 | 23 |
| 100 | - | - | - | - |
| 500 | - | - | - | - |
| 100 | - | - | - | - |

For N highers than 20 the process time is so higher that i couldn't find a solution. I used an A* algorithm with the combination of the heuristic function:

```
def h(state):
    return len(range(N)) - len(number_set(state))
```


and the unit_cost function:

```
 unit_cost=lambda a: len(a),
```

The idea behind this combination it's to prioritize the process of the nodes that are closer to the goal (the heuristic function calculate how many elements are left to reach the goal) and to set a cost equal to the list lenght. 

Using an unit_cost of 1 speed up the process, and it works for N higher than 20 too but the solution it's not optimal so i didn't report it in the file.

## Source code
Note that the state function, search function and the A*-algorithm are a modified version of the Professor Squillero's one.

You can find the original one here:
[8-puzzle](https://github.com/squillero/computational-intelligence/blob/master/2022-23/8-puzzle.ipynb)



