# Lab 2 - Francesco Sorrentino

You can find my solution into the file lab2_notebook.

## **Problem**

Same as lab1, we have to solve the set-covering problem, but this time with a Genetic Algorithm.

## **Method**

For this genetic algorithm i used a population of individual with a genome made of subset of lists from the main problem (possible solution), and a fitness made of a tuple with `covering` and `w` as the weight of the solution.

Now talking about the genetic operators, i used a custom crossover that take the intersection of the two lists (keeping the best parts that made them the winners of the tournament) and shuffling the "unique" part.

The mutation simply add a random list from the general problem to the genome if isn't already in the list: in that case the list is removed from the genome.

## **Results**

> Note: Population size, generations and offsprings size are selected depending on the problem size, that's because this algorithm doesn't scale so well, later i'll talk about the problems and how a second version would scale better and would produce better solutions.

| N | covering | w | pop | generations | offsprings |
|---|---|---|---|---|---|
| 5 | 5 | 5 | 10 | 10 | 5 |
| 10 | 10 | 10 | 40 | 20 | 20 |
| 20 | 20 | 24 | 500 | 100 | 300 |
| 500 | 500 | 1743 | 1000 | 100 | 600 |
| 1000 | 1000 | 4213 | 2000 | 100 | 1100 |

## **Problems and possible second version**

### **Problems**

As i said above this version of the algorithm has a lot of flaws, making genomes out of subset of lists, for large `N` use a lot of memory, just think about N = 1000 or larger. 

A second problem with the genome is that the size is variable and that makes it more difficult to apply genetic operators, in fact a fixed size genome (i'll talk about it later) would've been more effective.

Another problem is the mutation: it doesn't work very well and that's the reason of that low probability, but low probability of mutation it's equal to more probability to being stuck on a local minima, a really bad one, so that' why from `N=20` the algorithm begin to perform not so well.

### **Future possible second version**

A different version of this algorithm would be using as genome a list of integer `[0,1]` with the lenght of the problem, the meaning of that would be:

`if 0 = list not taken, if 1 = list taken`.

That will reduce the rappresentation as a list of bits, easy to manage with simple genetic operator, and the size of each genome would be fixed! two problem solved with a simple change.
Even if `N` would be much larger than 1000, the lists would be N integers.

## **Conclusions**

There could be a lot of improvements, maybe using migrations or other sort of implementation and different genetic operators, but at least it's slightly better than a greedy algorithm.
