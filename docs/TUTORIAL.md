This tutorial is designed for the developer transitioning from traditional functional languages (like Haskell or F#) to the **F-lang** "Clausal Way." In F-lang, we stop treating types, logic, and patterns as separate concepts and start treating them as a single, unified mathematical flow.

---

# 💎 THE F-LANG TUTORIAL: THINKING IN CLAUSES

Welcome to F-lang. This guide focuses on the three core pillars of the language: **Product-Sum Duality**, **Clausal Refinement**, and **Mathematical Grouping**.

---

## 1. Everything is a Pattern Match

In F-lang, there is no `if/else`. There are only **Clauses**. A function body or a type definition is simply a vertical list of cases separated by the pipe `|`.

```haskell
-- Traditional 'let' with clausal branches
let greet
    | "Alice" -> "Hello, Founder"
    | "Bob"   -> "Hello, Architect"
    | name    -> "Hello, " , name

```

---

## 2. The Power of the Product (`,`)

Forget the "Tuple" as a special data structure. In F-lang, the comma `,` is a first-class mathematical operator representing a **Product**.

* **Logic**: `a, b` means "I have an  AND a ."
* **Precedence**: The comma is lower than application but higher than the arrow.

```haskell
-- A function taking a product (2-tuple)
let area (width, height) -> width * height

-- A function returning a product
let getCoordinates | _ -> 10, 20

```

---

## 3. Parentheses are Only for Precedence

This is the most significant shift. Parentheses `( )` do not "create" a tuple; they only define the order of operations, exactly like in algebra.

* `f x, y`  `(f x), y` (A pair where the first element is the result of `f x`).
* `f (x, y)`  `f` applied to the pair `x, y`.

---

## 4. Refinement Types (`suchThat`)

F-lang allows you to attach logic directly to your data. Instead of checking for "Zero" inside a function, you define a type that *cannot be zero*.

```haskell
type Natural = Int
    suchThat
        | n : n >= 0 -> True
        | _          -> False

let sqrt n : Natural -> Float
-- The compiler guarantees 'n' is never negative here.

```

---

## 5. Behavioral Traits (`where`)

Traits in F-lang (like Type-classes) are applied via clauses. This allows for **Conditional Constraints**—a feature that allows a type to behave differently depending on its structure.

```haskell
type Box a
    | Full a
    | Empty
    where
        | Full a -> Show a  -- We only need 'Show' if the box is Full

```

---

## 🎯 SUMMARY: THE CLAUSAL CHEAT SHEET

| Goal | F-lang Notation | Mathematical Meaning |
| --- | --- | --- |
| **Combine Data** | `a, b` |  (Product) |
| **Branch Logic** | `| Case -> Result` |  (Sum) |
| **Constraint** | `where | ...` | Environmental Fact () |
| **Safety** | `suchThat | ...` | Predicate Filter () |
| **Nesting** | `( ... )` | Precedence Override |

---


## 1. The `with` Keyword: Structural Evolution

In F-lang, a "Record" is simply a named **Product**. The `with` operator allows us to create a new product based on an existing one, replacing or adding fields while maintaining the clausal invariants.

* **Logic**:  represents a structural update where  shadows .
* **Precedence**: Higher than the arrow `->`, lower than the comma `,`.

```haskell
type User
    | Account String, Int, Bool -- Username, ID, ActiveStatus

let deactivate user
    -- Pattern match the product and update the last element
    | Account name, id, _ -> user with (name, id, False)

```

---

## 2. Extensible Traits with `with`

Because our traits are clausal, we can use `with` to extend existing behavior. This is the F-lang answer to "Inheritance"—we call it **Clausal Composition**.

```haskell
trait Logger
    log : String -> IO Unit

-- Extend a standard logger with a timestamping 'with' clause
let timestampedLogger baseLogger
    | msg -> baseLogger with (log ("[" , currentTime , "] " , msg))

```

---

## 3. The Final Architecture: A Summary of Elegance

We leave F-lang with a design that is **Fixed, Finite, and Formal**:

1. **Syntactic Singularity**: Parentheses `()` for grouping, Commas `,` for products, Pipes `|` for sums.
2. **Clausal Unity**: The same syntax defines Types, Functions, Traits, and Refinements.
3. **Refinement Proofs**: `suchThat` ensures that logic is not an afterthought, but a requirement for compilation.
4. **Zero-Overhead Abstraction**: The STG VM ensures that these high-level concepts compile to efficient "Slide and Enter" machine code.

---

