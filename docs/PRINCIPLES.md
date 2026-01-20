# The Principles ("set in stone")

The *main principle* is to use traditional *declarative* mathematical notation at the *Type-level*, and the syntax which is best suited for defining functions by clauses, function composition, and uniform pattern matching at the level of code.

## 1. The Trinity (Universal Constructs)

We desugar High-Level types to these three Universal constructs:

*   `|` : **OR** (Sum Type, Fork)
*   `,` : **AND** (Product Type, Join)
*   `->` : **MAPS TO** (Step, Implication, Flow)

### Algebraic Data Types
*   `|`, `,`, and `->` are built-in. Every occurrence denotes the corresponding Algebraic Data Type.
*   **Nesting**: These can be naturally nested to define complex types.

## 2. Syntax & Structure

### Indentation
*   Everything is an expression reducing to a value.
*   Indentation is used to define code block-structure and scope.

### The Clause
*   The **Clause** is the fundamental building block.
*   Syntax: `| pattern -> body`
*   **Rule**: Prefer uniform, minimalist clausal notation. Use `|` and indentation over keywords like `match` or `case` where possible.

### Unified Syntax
*   **Application**: `f x` (Juxtaposition).
*   **Currying**: Universal. Every function is curried.
*   **Infix**: `x \`shouldBe\` 2` (Backticks turn a function into infix).
*   **Graph Structure**:
    *   `<var> | p -> e | ...` (Generalized clausal mapping).
    *   `if p then a else b` desugars to `p | True -> a | False -> b`.

## 3. Type-Level Syntax

*   **Arrows (`->`)**: strictly for Curried Function type signatures (`A -> B -> C`).
*   **Commas (`,`)**: strictly for Product Types / Tuples (`A, B`).
*   **Constructors**:
    *   **Type-Constructors**: Capitalized (e.g., `List`, `Map`).
    *   **Data-Constructors**: Capitalized (e.g., `True`, `Just`).

## 4. Traits and Implementations

*   **Keywords**: `trait`, `impl`, `given`, `where`.
*   **Trait Definition**: `trait Name(param) suchThat <bounds> where ...`
*   **Implementation**: `impl Trait(Type) given Context where ...`
    *   **Syntax Rule**: `impl Eq(List a) given Eq(a) where`
    *   Replaces `=>` with `given` and reverses the order (Constraint follows the Type).
*   **Bounds**: `<:` (Subtrait/Lower bound) and `>:` (Supertrait/Upper bound).

## 5. Mathematical Integrity

*   `suchThat`: Denotes mathematical equations / Trait bounds (Equational Reasoning).
*   `where`: Denotes code bindings / Local Environment.
*   `andAlso` / `orElse`: Logical connectives.

## 6. Advanced Forms

### Monadic Comprehensions
*   **Delimiters**: `[` and `]` are reserved **exclusively** for comprehensions.
*   **Binding**: `<-` is reserved for monadic binding within these blocks.
*   **Macros**: Classic Lisp-style macros (`'`, `` ` ``, `,`, `,@`) are allowed **only** within comprehension blocks.

### Imperative Forms
*   `{}`: Imperative blocks.
*   `;`: Explicit delimiter.
*   `:=`: Destructive assignment.

### Annotations & Ranges
*   `:`: Type annotation (`x : Int`).
*   `...`: Ellipsis.
*   `1..5`: Range.

## 7. Style & Conventions

*   **Maybe** (`Just | Nothing`) over Option.
*   **Result** (`Ok | Err`) over Either.
*   **Naming**: Consistent capitalization for Types/Constructors, lowercase for functions/variables.

## 8. Experimental Features
*   `extension` syntax: `extension (List a) { ... }` (or similar, mimicking Scala 3).
*   `macro`: Hygienic macro definitions.