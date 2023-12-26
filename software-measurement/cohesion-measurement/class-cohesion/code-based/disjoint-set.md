# Cohesion Metrics Disjoint Sets of Elements

## How

- Counting the number of pairs of methods that do not share their class attribute 

## Lack of Cohesion of Methods (LCOM1)

Let M be the set of methods and A be the set of attributes. 

Let the number of attributes of each M element be `AMi` and the number of methods accessing each A attribute be `MAj`

Then `LCOM1=[A(M) - (sum(MAj, j from 1 to A(A))/A(A))]/A(M)-1`

## LCOM2 (a Pairwise Connection-Based metric)

Calculating the difference between the number of method pairs that do or do not share their class attributes.

## LCOM3 (a Class Cohesion metric)

Measuring the number of connected components in the graph.

## LCOM4