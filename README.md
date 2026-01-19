# F-Lang: The Mathematical Optimum

**Version 1.0**

F-lang is a research-grade functional programming language designed to reconcile structural elegance, pragmatic minimalism, and rigorous logic. It unifies clausal constraints, predicates, and algebraic data types into a minimalist, indentation-aware syntax.

## Core Semantic Pillars

1.  **Product-Sum Duality**:
    *   **Products** are denoted by commas (`,`).
    *   **Sums** are denoted by vertical bars (`|`).
2.  **Clausal Constraints (`where`)**: Traits are applied through pattern-matching clauses, enabling conditional behavioral conformance.
3.  **Refinement Predicates (`suchThat`)**: Types are refined by logical predicates defined via clausal analysis, enforcing invariants at the type level.
4.  **Uniform Binding**: Every binding site (function definition, `let`, `case`) is a pattern match.

## The Refined Prelude

### 1. Core Identities
Basic types use absolute minimum syntax.

```haskell
type Bool | False | True
type Maybe a | Nothing | Just a
type Either a, b | Left a | Right b
type List a | Nil | Cons a, List a
```

### 2. Behavioral Traits
Traits are defined as sets of signatures with optional default implementations.

```haskell
trait Eq a
    (==) : a, a -> Bool
    (!=) : a, a -> Bool
    where
        | _ -> not (x == y)

trait Ord a where Eq a
    (<) : a, a -> Bool
    (>) : a, a -> Bool
    max : a, a -> a
    where
        | x, y suchThat x > y -> x
        | _, y                -> y
```

### 3. Refinement Types
Correctness is enforced at the type level using `suchThat`.

```haskell
-- A divisor that can never be zero
type Divisor = Int
    suchThat
        | n : n != 0 -> True
        | _          -> False

-- A list guaranteed to be non-empty
type NonEmpty a
    | Cons a, List a
    suchThat
        | Nil -> False
        | _   -> True
```

### 4. Functors and Monads
The monadic hierarchy utilizes clausal constraints.

```haskell
trait Functor f
    fmap : (a -> b), f a -> f b

trait Monad m where Functor m
    return : a -> m a
    (>>=)  : m a, (a -> m b) -> m b
```

### 5. Unified Pattern Matching
Function headers are named binding sites. The `|` indicates branching logic.

```haskell
let foldl f, acc
    | Nil        -> acc
    | Cons x, xs -> foldl f, (f acc, x), xs

let filter p
    | Nil -> Nil
    | Cons x, xs
        suchThat p x -> Cons x, filter p, xs
        | _          -> filter p, xs
```

## Formal Grammar Summary

*   **Structure**: Indentation-sensitive (Off-side Rule).
*   **Grouping**: `( )` strictly for precedence.
*   **Application**: Space-separated, left-associative, highest precedence.
*   **Keywords**: `type`, `trait`, `let`, `where`, `suchThat`, `with`.

### Precedence Hierarchy

| Level | Operator | Description |
| :--- | :--- | :--- |
| **1** | `( )` | Grouping |
| **2** | `space` | Application (Left-associative) |
| **3** | `,` | Product (Conjunction/AND) |
| **4** | `->` | Mapping (Transition/Arrow) |
| **5** | `|` | Sum (Disjunction/OR) |
| **6** | `where` / `suchThat` | Context / Refinement |

## Example: Quadratic Solver
Combines trait constraints, product types, and refinements.

```haskell
let solveQuadratic a, b, c
    where 
        | _ -> Floating a, Floating b, Floating c
    suchThat 
        | _ -> (b * b) - (4 * a * c) >= 0
    | a, b, c -> 
        let d = sqrt ((b * b) - (4 * a * c))
        ((-b + d) / (2 * a)), ((-b - d) / (2 * a))
```

## Conclusion

F-lang achieves a "Singularity of Syntax" by mapping Category Theory directly onto text:
*   **Logic**: AND (`,`), OR (`|`), IF (`->`).
*   **Categories**: Product, Coproduct, Exponential.
*   **Computation**: Parallelism, Branching, Flow.

The syntax is complete, consistent, and mathematically sound.