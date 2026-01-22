# F-Lang Advanced Syntax Specification

## 1. Monadic Comprehensions

Square brackets `[` and `]` are reserved **exclusively** for the comprehension embedded DSL, providing a declarative syntax for monadic processing.

### 1.1 Syntax
`[ expression | qualifiers ]`

Qualifiers include:
*   **Generators**: `pattern <- expression` (Monadic bind).
*   **Guards**: Boolean expressions (Filters).
*   **Local Bindings**: `let pattern = expression`.

### 1.2 Patterns as Filters
Pattern mismatches in generators result in implicit filtering, streamlining data pipeline definitions.

```haskell
-- Extract prices of all 'Buy' orders, skipping 'Sell'
[ price | Order(Buy, price, _) <- orders ]
```

## 2. Infix Annotations

Functions can be used in an infix position to enhance readability.

### 2.1 Call Site Infix
Any binary function can be applied infix by surrounding it with backticks `` ` ``.

```haskell
let result = x `compare` y
```

### 2.2 Definition Site (Modifier)
The `infix` modifier indicates a function is primarily intended for infix use.

```haskell
infix let shouldBe(a, b) = ...
```

## 3. Hygienic Macro System (Classic Lisp)

Structural code generation uses Quasiquote and Unquote, restricted to Comprehension blocks.

*   `` `expr ``: **Quasiquote** (Code template).
*   `,expr`: **Unquote** (Evaluate inside template).
*   `,@expr`: **Splice-Unquote** (Splice list inside template).
*   `'expr`: **Quote** (Literal symbol/list).

```haskell
macro assert(cond) = 
    `(if ,cond then Ok(()) else panic("Assertion failed"))
```

## 4. Syntactic Constraints

To maintain minimalism and ambiguity-free parsing:

*   **Square Brackets**: Reserved strictly for comprehensions. Never used for type parameters or array indexing.
*   **Type Parameters**: Use juxtaposition `List Order`. Parentheses `List (Order)` denote grouping/precedence only.
*   **Blocks**: Defined by indentation or explicit braces `{}` (imperative context only).

## 5. Trait System & Bounded Quantification

F-Lang uses a rigorous syntax derived from standard Type Theory for defining and implementing traits.

### 5.1 Trait Definition (Inheritance)
Traits form a hierarchy. We use the colon `:` (similar to Rust) to define "Supertrait" requirements. This creates a lower bound on the type.

**Syntax:** `trait Name Param : SuperTrait where ...`

```haskell
-- To be 'Ord'erable, a type must first be 'Eq'utable.
trait Ord a : Eq a where
    (<) : a -> a -> Bool
    ...
```

### 5.2 Implementation (Context)
When implementing a trait, we often need to constrain the generic type parameters. We use the `given` keyword to introduce this context, and the `<:` (Subtype) operator to express the constraint.

**Syntax:** `impl Trait(Type) given Context where ...`

*   `given`: Introduces the logical context ($\Gamma \vdash \dots$).
*   `<:`: "Is a subtype of" / "Implements".

```haskell
-- Implement Equality for a List of 'a', GIVEN that 'a' itself implements Equality.
impl Eq(List a) given a <: Eq where
    (==) list1 list2 | ...
```

This notation aligns with the set-theoretic view: `a <: Eq` means the type `a` is a member of the set defined by trait `Eq`.