# Design Philosophy & Motivation

## Motivation

F-Lang addresses the complexity and fragmentation often found in modern functional programming languages. By strictly adhering to mathematical first principles, it aims to eliminate syntactic noise and semantic ambiguity. The goal is a language where the "Soul" of the program—its mathematical invariants—is indistinguishable from its implementation.

## Disambiguation of Terminology

Precise terminology is essential for rigorous design. Common logical connectives are often overloaded in natural language; F-Lang distinguishes them explicitly:

*   **Logical AND**:
    *   **Contextual (`andAlso`)**: Present in the same locality.
    *   **Sequential (`andThen`)**: Ordered nesting of events.
    *   **Formal (`AND`)**: Boolean conjunction.
    *   **Structural (`,`)**: The Product type (join).
*   **Logical OR**:
    *   **Choice (`orElse`)**: Short-circuiting alternative.
    *   **Formal (`OR`)**: Boolean disjunction.
    *   **Structural (`|`)**: The Sum type (fork).
*   **Refinement**:
    *   **`suchThat`**: Denotes predicate logic constraints (equations of truth).
    *   **`where`**: Denotes nested bindings (definitions in scope).
    *   **`with`**: Denotes set-union at the abstract interface level.

## Unified Abstractions

F-Lang unifies concepts that are often treated separately:

1.  **Functions as Clauses**: A function is defined as a set (disjoint union) of individual clauses. Each clause represents a partial function that partitions the domain.
2.  **`let` as Lambda**: A `let` binding is structurally isomorphic to a `lambda` with in-place application. Nested `let`s correspond to nested closures.
3.  **Pattern Matching**: Conditional expressions (`case`, `match`) are the inverse of function definition. Both rely on the same clausal structure to handle disjoint unions.

## Algebraic Structure

The type system is built on the rigorous nesting of Algebraic Data Types (ADTs):

*   **Sums (`|`)**: Represent choice, branching, or disjoint unions.
*   **Products (`,`)**: Represent grouping, parallelism, or conjunction.

These structures are duals and can be nested arbitrarily. A "single" product is a sum of one item, and a single-clause sum is a product of one. This symmetry is enforced throughout the language.

## Core Primitives

The syntax is reducible to three universal structural elements found in algorithm charting and circuit design:

1.  **Fork (`|`)**: Divergence or choice.
2.  **Join (`,`)**: Convergence or pairing.
3.  **Step (`->`)**: Transformation or implication.

## Computational Model

At its core, an F-Lang program represents a Directed Acyclic Graph (DAG). This structure underpins formal logic, algorithms, and the Curry-Howard isomorphism. Recursion replaces imperative looping to maintain the DAG property.

The "direction" of the graph (`->`) is fundamental and strictly enforced, reflecting the flow of implication. F-Lang formalizes these "intuitive" mathematical truths into a concrete, executable syntax.