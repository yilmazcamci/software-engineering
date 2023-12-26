# An Ordinal Scale of Cohesion Measurement

*Relied purely on human assessment*

| Rank | Type          | Quality |
|:----:|---------------|:-------:|
|  6   | Functional    |  Good   |
|  5   | Sequential    |    .    |
|  4   | Communication |    .    |
|  3   | Procedural    |    .    |
|  2   | Temporal      |    .    |
|  1   | Logical       |    .    |
|  0   | Coincidental  |   Bad   |

## Functional cohesion

*Highest cohesion*

Each module performs a single well-defined function or achieves a single goal.

## Sequential cohesion

There are modules performing more than one function, but they occur in an order prescribed by the specification, i.e., they are strongly related.

## Communication cohesion

There are modules performing multiple functions on the same data or sets of data. The data, however, is not a single type or structure.

## Procedural cohesion

There are modules performing multiple functions that are procedurally related.

## Temporal cohesion

There are modules performing more than one function, and they are related only by the fact that they must occur within the same time span.

## Logical cohesion

There are modules performing a series of similar functions with weak relationship. For example, utility classes.