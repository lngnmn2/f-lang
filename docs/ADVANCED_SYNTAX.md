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
