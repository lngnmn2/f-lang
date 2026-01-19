# F-Lang Prelude: Standard Library Fundamentals

This document outlines the core types and traits of the F-Lang Standard Library.

## 1. Basic Types

We define the fundamental algebraic data types using clausal syntax.

```haskell
-- Optional values
type Maybe a
    | Just a
    | Nothing

-- Error handling
type Result a e
    | Ok a
    | Err e

-- Compatibility Aliases
let Either = Result
let Left   = Err
let Right  = Ok
```

## 2. Recursive Types

Recursive structures demonstrate the composition of sum and product types.

```haskell
-- Linked List
type List a
    | Nil
    | Cons (a, List a)

-- Functorial Map for List
let map f list =
    list
        | Nil          -> Nil
        | Cons (x, xs) -> Cons (f x, map f xs)
```

## 3. Core Traits

The `Monad` trait defines the sequencing of computational flows.

```haskell
trait Monad m
    pure : a -> m a
    bind : m a -> (a -> m b) -> m b

-- Instance for Result
instance Monad (Result a e)
    where
        pure x = Ok x
        bind res f =
            res
                | Ok x  -> f x
                | Err e -> Err e
```

## 4. Monadic Structures

### Reader (Environment)
Models access to an immutable environment.

```haskell
type Reader r a
    | Reader (r -> a)

let ask = | r -> r
let run reader r = 
    let Reader f = reader
    f r
```

### State (Persistent)
Models state transformation via a persistent DAG.

```haskell
type State s a
    | State (s -> (a, s))

instance Monad (State s a)
    where
        pure x = State ( \s -> (x, s) )
        bind stateM f = State ( \s -> 
            let State g = stateM
            let (val, nextState) = g s
            let State h = f val
            h nextState )
```

## 5. Numeric Traits

Numeric types support arithmetic operations and can be refined.

```haskell
type Ordering | LT | EQ | GT

trait Eq a where
    equals : a -> a -> Bool

trait Ord a where
    compare : a -> a -> Ordering

-- Implementation for Int
instance Ord Int where
    compare x y =
        (x < y)
            | True  -> LT
            | False -> 
                (x == y)
                    | True  -> EQ
                    | False -> GT

trait Num a
    plus  : a -> a -> a
    minus : a -> a -> a
    times : a -> a -> a

-- Real math using suchThat to prevent undefined behavior
trait Floating a
    where | _ -> Num a
    div : a -> (a suchThat val != 0) -> a
```

## Summary

| Module | Concept | Representation |
| :--- | :--- | :--- |
| **Logic** | Choice (`|`) | `Maybe`, `Result`, `Ordering` |
| **Data** | Parallel (`,`) | `List`, `Product`, `State` |
| **Control** | Flow (`->`) | `Monad`, `Reader`, `Math` |