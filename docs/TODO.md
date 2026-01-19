# Implementation Tasks & Notes

## Core Semantics
*   **Inverse Relation**: Ensure the `match` expression is the strict inverse of type definition by clauses.
*   **Disjoint Unions**: Functions are defined as disjoint unions of clauses.
*   **Pattern Binding**: Every left-hand side binding site is a pattern (Erlang-style).
*   **Single-Clause Functions**: A function defined by a single clause is equivalent to a single-branch `match`.

## Syntax Goals
*   **Minimal Uniformity**: Eliminate special cases; treat functions, `case`, and `let` as unified pattern-matching constructs.