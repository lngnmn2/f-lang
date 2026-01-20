# The Standard Prelude

The F-Lang Prelude defines the core types, traits, and functions available in every program. It serves as the foundation for the language's ecosystem, providing a minimal yet powerful set of abstractions.

## Core Types

### Primitive Types
*   `Bool`: True | False
*   `Int`: 64-bit Signed Integer
*   `Double`: 64-bit IEEE 754 Float
*   `Char`: Unicode Scalar Value
*   `String`: UTF-8 String
*   `Unit`: ()

### Algebraic Data Types
*   `Maybe a`: Represents an optional value (`Just a | Nothing`).
*   `Result a e`: Represents a value or an error (`Ok a | Err e`).
*   `List a`: A homogeneous linked list (`Nil | Cons (a, List a)`).
*   `IO a`: An effectful computation returning `a`.

## Fundamental Traits

### Eq (Equality)
```haskell
trait Eq a where
    equals : a, a -> Bool
    infix let (==) = equals
    infix let (!=) x, y = not (equals x, y)
```

### Ord (Ordering)
```haskell
trait Ord a where Eq a
    compare : a, a -> Ordering
    infix let (<) x, y  = (compare x, y) == LT
    -- ... (<=, >, >=)
```

### Show (String Conversion)
```haskell
trait Show a where
    show : a -> String
```

## Monadic Hierarchy

The Prelude defines the standard hierarchy of monadic traits:
1.  `Functor`: Mappable structures.
2.  `Applicative`: Function application within a context.
3.  `Monad`: Sequential composition of effectful computations.
4.  `Alternative`: Associative binary operation and identity (empty).

## Standard Implementations

The Prelude includes implementations for all core types:

```haskell
-- List
impl Functor(List a) where ...
impl Monad(List a) where ...
impl Show(List a) given Show(a) where ...

-- Result
impl Monad(Result a e) where ...

-- IO
impl Monad(IO) where ...
```
