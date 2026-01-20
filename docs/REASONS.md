# Reasons & Philosophy ("The Whys")

This document captures the design rationale, philosophical inspirations, and "the whys" behind the principles of F-Lang. It explains the reasoning for specific syntactic and architectural choices, often referencing the historical context of functional programming languages.

## The Goal

The main goal is to arrive at a unified syntax, inspired by both the classic FP languages (SML, Erlang, Haskell, OCaml) as well as the modern languages (F#, Scala 3, Rust). We aim for a "minimal but consistent and complete syntax" that reconciles different choices into generic and uniform ones.

## The Trinity and Mathematical Integrity

At the very fundamental level, we use so-called *Trinity* to denote **both** the proper *Algebraic Data Types* (at the type-level) and the corresponding *"dual" nested structure* at the code level.

*   `|` (**OR**, fork)
*   `,` (**AND**, join)
*   `->` (**IMPLY**, maps to)

These are considered "built-in" to the fabric of reality for this language. We desugar everything to these universal constructs.
*   **No Tuple Type Machinery**: Haskell defines a Tuple type `(,)` and has sophisticated machinery for it. We resist this temptation. We rely on the natural nesting of `,`.
*   **Direction**: A direction of a DAG is not arbitrary. It arises from the flow of implications (connecting steps), which are not reversible. Thus, direction is implicit and necessary in any "fork".

## Syntactic Unification

### The Clause as the Atom
A **Clause** is the ultimate building block. We prefer the uniform and minimalist clausal notation (`| pattern -> body`) over specific `match` or `case` keywords where possible.
*   **Why?** An Universal Implication (Modus Ponens) can be denoted as "If This Then That". A Sum-Type is a set of individual clauses. Thus, a single clause (denoting a single arrow) is the most abstract and general building block.
*   **Inspiration**: Ocaml's specialized `function` expression, which pattern-matches on the implicit last argument, is the inspiration for our Anonymous Clauses.

### Currying and the Arrow
*   **Why `->`?** In mathematics, `->` denotes an anonymous *mapping* (e.g., `x -> x + 1`). It traditionally stands for *maps to*. Its use should be restricted to Curried signatures (Type-level) and mappings (Code-level).
*   **Why Currying?** It clearly captures the notion of a "partially filled enzyme" — "not all necessary and sufficient conditions are met yet." It unifies single-argument lambda expressions with the notion of "arrows going in".

### Homage to Mathematical Notation
*   **Space (` `)**: Function application (juxtaposition). The finest structural element, naturally denoting Partial Application.
*   **Equal (`=`)**: An immutable binding. We are not Platonists — ideas need a context. The notion of a persistent **Environment** is necessary.
*   **Parentheses `()`**: Only for precedence and grouping, exactly as in math.
*   **Keywords**: We use "words" of mathematical language (`suchThat`, `given`, `where`) with their traditional meanings.

## The Trait/Impl Dilemma

We selected **Trait** and **Impl** over Class and Instance.
*   `class` implies a rigid hierarchy (Set-Subset relation) and is consistent with Predicate Logic but carries baggage.
*   `instance` is beautiful but less compositional in name.
*   **Choice**: We substitute `trait` for class and `impl` for instance to emphasize the compositional nature (Set-Union operation) and decouple from implicit class hierarchies.
*   **Syntax**: `impl Eq(List a) given Eq(a) where`. This unifies the syntax, replacing the `=>` symbol with `given` and reversing the order of arguments to read more like a logical statement: "Implement Eq for List a, given Eq for a".

## Style Choices

*   **Maybe vs Option**: `Just a | Nothing` is considered more "classy" than `Some a | None`.
*   **Result vs Either**: `Left | Right` are considered a disgrace due to their lack of semantic direction (which is error?). `Result` is explicit.

## Inspirations (The Giants We Stand On)

*   **SML/NJ & Mlton**: The uniform clause syntax (`|`) without `fun`. `andAlso`, `orElse`.
*   **F#**: Uniform `type` declaration and `let` indentation-based syntax.
*   **Ocaml**: The `= function` specialized syntax.
*   **Erlang**: Definition by clauses and uniform pattern matching.
*   **Haskell**: `case` expression, backtick infix syntax, Type Classes (adapted), Module syntax.
*   **Scala 3**: Monadic comprehensions (pattern matching, filtering), `ext <Trait> with` for extensions.
*   **Rust**: `impl` blocks for associated methods.
*   **Lisp**: The classic Hygienic Macro system (Quasiquote/Unquote) restricted to comprehensions.

## Testing Philosophy
Tests are *declarative* specifications of constraints using Monadic Comprehensions. We aim to mimic Scalatest's clarity using a minimal declarative DSL embedded in the library.
