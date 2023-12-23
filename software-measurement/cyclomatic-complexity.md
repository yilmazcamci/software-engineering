# Cyclomatic Complexity

## In graph theory

`V(G) = e - n + 2`

where

- `e`: the number of edges
- `n`: the number of nodes

## In a simple program

`V(G) = #BD + 1`

where `#BD` is the total binary decisions of the program.

- `If-else` is a two-way decision and counted as 1 binary decision
- `If-elif-else` is a three-way decision and counted as 2 binary decisions
- `swith-n-case` is an n-way decision and counted as n-1 binary decisions
- Each `condition of a loop` is counted as 1 binary decision

## Conditional code, flow, and graph association

### If

*Binary decision 1*

```js
if (c) {
    s1
}

s2
```

```mermaid
flowchart TD
    subgraph flow
        cf{c}--T-->sf1[s1]-->sf2[s2]
        cf--F-->sf2
    end
    subgraph graph
        cg((c))-->sg1((s1))-->sg2((s2))
        cg-->sg2
    end
```

### If-else

*Binary decision 1*

```js
if (c) {
    s1
} else {
    s2
}

s3
```

```mermaid
flowchart TD
    subgraph flow
        cf{c}--T-->sf1[s1]-->sf3[s3]
        cf--F-->sf2[s2]-->sf3
    end
    subgraph graph
        cg((c))-->sg1((s1))-->sg3((s3))
        cg-->sg2((s2))-->sg3
    end
```

### If-elif-else

*Binary decision 2*

```js
if (c1) {
    s1
} elif (c2)
    s2
} else {
    s3
}

s4
```

```mermaid
flowchart TD
    subgraph flow
        cf1{c1}--T-->sf1[s1]-->sf4[s4]
        cf1--F-->cf2{c2}--T-->sf2[s2]-->sf4
        cf2--F-->sf3[s3]-->sf4
    end
    subgraph graph
        cg1((c1))-->sg1((s1))-->sg4((s4))
        cg1-->cg2((c2))-->sg2((s2))-->sg4
        cg2-->sg3((s3))-->sg4
    end
```

### switch-n-cases

*n-1 binary decisions*

switch-4-cases

```js
switch (n) {
    case c1:
        s1
        break
    case c2:
        s2
        break
    case c3:
        s3
        break
    case c4:
        s4
        break
}

s5
```

```mermaid
flowchart TD
    subgraph flow
        cf1{c1}--T-->sf1[s1]-->sf5[s5]
        cf1--F-->cf2{c2}--T-->sf2[s2]-->sf5
        cf2--F-->cf3{c3}--T-->sf3[s3]-->sf5
        cf3--F-->cf4{c4}--T-->sf4[s4]-->sf5
    end
    subgraph graph
        cg1((c1))-->sg1((s1))-->sg5((s5))
        cg1-->cg2((c2))-->sg2((s2))-->sg5
        cg2-->cg3((c3))-->sg3((s3))-->sg5
        cg3-->cg4((c4))-->sg4((s4))-->sg5
    end
```

Or shorter

```mermaid
flowchart TD
    subgraph flow
        cf{c}--c1-->sf1[s1]-->sf5[s5]
        cf--c2-->sf2[s2]-->sf5
        cf--c3-->sf3[s3]-->sf5
        cf--c4-->sf4[s4]-->sf5
    end
    subgraph graph
        cg((c))-->sg1((s1))-->sg5((s5))
        cg-->sg2((s2))-->sg5
        cg-->sg3((s3))-->sg5
        cg-->sg4((s4))-->sg5
    end
```

### Loops

*n-iterations + 1 binary decisions*

#### while and for

```
while (c) {
    s1
}

s2
```

```
for (;c;) {
    s1
}

s2
```

```mermaid
flowchart TD
    subgraph flow
        cf{c}--Tn-->sf1[s1]-->cf
        cf--F-->sf2[s2]
    end
    subgraph graph
        cg((c))--n-->sg1((s1))-->cg
        cg-->sg2((s2))
    end
```

#### do-while

```
do {
    s1
} while (c)

s2
```

```mermaid
flowchart TD
    subgraph flow
        sf1[s1]-->cf{c}--Tn-->sf1
        cf--F-->sf2[s2]
    end
    subgraph graph
        sg1((s1))-->cg((c))--n-->sg1
        cg-->sg2((s2))
    end
```

## Drawbacks

- Ignoring the complexity of sequential statements
- Do not distinguish different kinds of control flow complexity

## Applications

- Indicating the testability and understandability of a program/module/function
- Refactoring code by reducing the complexity of the conditional logic of a program/module/function