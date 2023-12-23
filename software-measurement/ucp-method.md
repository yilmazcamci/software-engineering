# Use Case Point Method

## Considerations

- Use case actors
- Scenarios
- Non-functional requirements
- Environmental factors

## Formula

`UCP = UUCP * TCF * ECF`

where:
- `UUCP` - Unjustified Use Case Points: the complexity of functional requirements
  - Unadjusted Actor Weight (`UAW`): the total complexity of all actors in all use cases
  - Unadjusted Use Case Weight (`UUCW`): the number of activities (steps) in all use case scenarios
- `TCF` - Technical Complexity Factors: the complexity of non-functional requirements
- `ECF` - Environmental Complexity Factors: assesses the development team's experience and their development environment

## Unadjusted Use Case Point

`UCCP = UAW + UUCW`

### Unadjusted Actor Weight (`UAW`)

#### Actor classifiers and associated weights

| Classifier | Considerations                                                                                                                                                      | Weight |
|:----------:|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------:|
|   Simple   | An other system interacts with our system through a defined API                                                                                                     |   1    |
|  Average   | A person interacts with our system through a text-base UI<br>An other system interacts with our system through a protocol, such as a network communication protocol |   2    |
|  Complex   | A person interacts with out system through a GUI                                                                                                                    |   3    |

`UAW = #simple + #average * 2 + #complex * 3`

### Unadjusted Use Case Weight (`UUCW`)

#### Use case categories and associated weights

| Category | Consideration                                                           | Weight |
|:--------:|-------------------------------------------------------------------------|:------:|
|  Simple  | 1 actor<br>Happy case steps 1-3<br>Concepts of domain model 1-3         |   5    |
| Average  | 2+ participating actors<br>Happy case steps 4-7<br>Domain concepts 5-10 |   10   |
| Complex  | 3+ participating actors<br>Happy case steps 7+<br>Domain concepts 10+   |   15   |

`UUCW = #simple * 5 + #average * 10 + #complex * 15`

## Technical Complexity Factor (TCF)

### Common technical factors and their weights

| Factor | Description                                        | Weight |
|:------:|----------------------------------------------------|:------:|
|   T1   | Distributed system                                 |   2    |
|   T2   | Performance objectives (response time, throughput) |  1-2   |
|   T3   | End-use efficiency                                 |   1    |
|   T4   | Complex internal processing                        |   1    |
|   T5   | Reusable design or code                            |   1    |
|   T6   | Easy to install                                    |  0.5   |
|   T7   | Easy to use                                        |  0.5   |
|   T8   | Portable                                           |   2    |
|   T9   | Easy to change                                     |   1    |
|  T10   | Concurrent use                                     |   1    |
|  T11   | Special security                                   |   1    |
|  T12   | Provides direct access for third parties           |   1    |
|  T13   | Special user training facilities are required      |   1    |

### Perceived Complexity (PC) points

The development team will assess the perceived complexity of each technical factor in the context of the project and assign a point in range 0 to 5 for each.

- `0`: no problem
- `3`: need average effort or in-doubt
- `5`: need major effort

### Constants C1 and C2

TCF also have two constants to limit the its impact whose range is from 0.6 to 1.3. We choose the values for C1 and C2 based on experience and intuition.

### Formula

`TCF = C1 + C2 * sum(Wi * PCi, i from 1 to 13 if any)`

## Environmental Complexity Factor (`ECF`)

### Common ECF and their weights

| Factor | Description                                                | Weight |
|:------:|------------------------------------------------------------|:------:|
|   E1   | Familiar with the development process:<br>- Agile<br>- UML |  1.5   |
|   E2   | Application problem experience                             |  0.5   |
|   E3   | Paradigm experience:<br>- OOP                              |   1    |
|   E4   | Lead analyst capability                                    |  0.5   |
|   E5   | Motivation                                                 |   1    |
|   E6   | Stable requirements                                        |   2    |
|   E7   | Part-time staff                                            |   -1   |
|   E8   | Difficult programming language                             |   -1   |

### Perceived complexity (PC) points

- `0`: no impact at all
- `1`: strong negative impact
- `3`: average negative impact
- `5`: strong positive impact

### Perceived Complexity points and factors associations

- `E1-E4`:
  - `0`: no experience
  - `3`: average
  - `5`: expert
- `E5`:
  - `0`: no motivation
  - `3`: average
  - `5`: high motivation
- `E6`: 
  - `0`: unchanging requirements
  - `3`: average changing requirements
  - `5`: extremely unstable requirements
- `E7`:
  - `0`: no part-time staff
  - `3`: half of team is part-time
  - `5`: all team is part-time
- `E8`:
  - `0`: easy
  - `3`: average
  - `5`: very difficult

ECF also have two constants to limit the its impact whose range is from 0.425 to 1.4. We choose the values for C1 and C2 based on experience and intuition.

### Formula

`ECF = C1 + C2 * sum(Wi * PCi, i from 1 to 8 if any)`
