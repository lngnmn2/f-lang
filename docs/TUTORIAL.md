# F-Lang Tutorial: The Clausal Paradigm

This guide introduces the core concepts of F-Lang: **Unified Pattern Matching**, **Product Types**, and **Refinements**.

## 1. Unified Pattern Matching

In F-Lang, everything is a pattern match. Functions and `let` bindings are defined by clauses.

### Function Definition
Variables come first, followed by indented clauses.

```haskell
-- Clausal function
let greet =
    | "Alice" -> "Hello, Founder"
    | "Bob"   -> "Hello, Architect"
    | name    -> "Hello, " ++ name

-- Pattern matching on arguments
let describe x =
    x
        | 0 -> "Zero"
        | _ -> "Non-zero"
```

## 2. Control Flow Desugaring

Standard control flow constructs are syntactic sugar for generalized clausal application.

*   **`if`**: A two-clause match on `Bool`.
*   **`when`**: A single-clause match.

```haskell
-- Desugars to clauses
let absolute x =
    (x >= 0)
        | True  -> x
        | False -> -x
```

## 3. Product Types (`,`)

The comma `,` is the **Product** operator. It creates values that hold multiple items simultaneously.

*   **Logic**: `a, b` (AND).
*   **Precedence**: Lower than application, higher than arrow `->`.

```haskell
-- Function taking a product (tuple)
let area (width, height) = width * height

-- Function returning a product
let getCoordinates = | _ -> (10, 20)
```

**Note**: Parentheses `( )` are strictly for precedence. `f x, y` parses as `(f x), y` (a pair). `f (x, y)` passes a pair to `f`.

## 4. Refinement Types (`suchThat`)

Refinements attach logical predicates to types, strictly enforced by the compiler.

```haskell
type Natural = Int
    suchThat
        | n : n >= 0 -> True
        | _          -> False

-- 'n' is guaranteed to be non-negative
let sqrt n : Natural -> Float
```

## 5. Traits and Constraints (`where`)

Traits are applied via clauses, enabling conditional conformance based on structure.

```haskell
type Box a
    | Full a
    | Empty
    where
        | Full a -> Show a  -- 'Show' required only if Full
```

## 6. Extensible Records (`with`)

The `with` operator performs structural updates on Product types (Records).

```haskell
type User
    | Account (String, Int, Bool)

let deactivate user =
    -- Update the 3rd element of the product
    | Account (name, id, _) -> user with (name, id, False)
```

## Summary

| Concept | Syntax | Meaning |
| :--- | :--- | :--- |
| **Product** | `a, b` | Grouping / AND |
| **Sum** | `| Case -> Result` | Branching / OR |
| **Constraint** | `where` | Contextual Fact |
| **Refinement** | `suchThat` | Logical Filter |