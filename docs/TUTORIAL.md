# The F-Lang Tutorial: A Journey into Logic

Welcome! This guide is written for anyone who wants to understand **programming as pure logic**. We don't just write code here; we describe the universe using three simple, magical building blocks.

If you know basic math (like addition and multiplication), you already know F-Lang.

---

## 1. The Trinity: The Only Three Shapes You Need

Imagine you are building a universe. You only need three distinct "connectors" to build absolutely anything: data, logic, or programs. We call this **The Trinity**.

### 1. The Fork: OR (|
**Mathematical Name:** Sum Type (Addition)

This is a choice. You can go Left **OR** Right. You can have Chocolate **OR** Vanilla. You cannot have both at the same time.

```haskell
type IceCream
    | Chocolate
    | Vanilla
    | Strawberry
```

This is like a fork in the road. In math, this is **Addition**. If you have 2 choices of ice cream and 3 choices of toppings, you have $2 + 3$ distinct possibilities if you pick just one thing.

### 2. The Pair: AND (`,`)
**Mathematical Name:** Product Type (Multiplication)

This is a combination. You have a Burger **AND** Fries. You hold them both together.

```haskell
type Meal = (Burger, Fries)
```

In math, this is **Multiplication**. If you have 2 types of Burgers and 3 types of Fries, you have $2 \times 3 = 6$ possible distinct meals.

### 3. The Arrow: MAPS TO (`->`)
**Mathematical Name:** Function (Implication / Exponentiation)

This is a transformation. It is a magic machine. You put an Apple in, and it turns it **INTO** a Slice.

```haskell
let slice : Apple -> Slice
```

In math, this is **Implication**. "If you have an Apple, then you can get a Slice." It is the direction of time and logic. It only flows one way.

---

## 2. Making Decisions: The "Sorting Hat"

In many languages, you have `if`, `switch`, `for`, `while`. In F-Lang, we just have **Pattern Matching**. It's like a sorting machine.

You define a "Clause" using the vertical bar `|` (the Fork). You are listing the possibilities.

```haskell
let describeNumber x
    | 0 -> "It is Zero"
    | 1 -> "It is One"
    | _ -> "It is something else"
```

This effectively says: "Is it 0? Go this way. Is it 1? Go that way."

Even `true` and `false` are just a choice!

```haskell
type Bool | True | False

let not b
    | True  -> False
    | False -> True
```

**Key Principle:** Every decision in your code is just handling a "Fork" in the data.

---

## 3. No Nulls, No Surprises

In the real world, if you have a shoebox, it might be empty. But in bad programming languages, you assume there are shoes inside, reach in, and—*CRASH*—the universe breaks because it was `null` (empty void).

In F-Lang, we are honest. If a box *might* be empty, we use the **Fork** (`|`) to explicitly say so.

```haskell
type Maybe a
    | Just a    -- It has something!
    | Nothing   -- It is empty.
```

Now, the compiler forces you to handle both paths. You cannot accidentally use the "Nothing" as if it were a "Something."

---

## 4. Superpowers (Traits)

Think of a **Trait** as a superpower definition.
*   **Trait**: `Flyable` (Can fly).
*   **Impl**: `Bird` implements `Flyable`.

```haskell
-- The Superpower Definition
trait Eq a where
    equals : a -> a -> Bool

-- Teaching Integers how to be Equal
impl Eq(Int) where
    equals x y = primEqInt x y
```

We say: "Implement the `Eq` superpower for `Int`."
We can also add conditions: "Implement `Eq` for a `List` of things, **GIVEN** that the things themselves know how to be `Eq`."

```haskell
impl Eq(List a) given Eq(a) where ...
```

---

## 5. The Laws of Logic

F-Lang enforces strict rules to keep your program safe, like a physics engine for logic.

1.  **Immutability**: You cannot "change" a number from 5 to 6. 5 is always 5. You can only create a *new* value that is 6. This prevents history from changing behind your back.
2.  **Total Functions**: You must handle every possibility. If you write a function for `Bool`, you must handle `True` and `False`. No missing pieces.
3.  **Strict Typing**: You cannot add "Apple" to 5. It doesn't make sense. The universe rejects it.

---

## 6. Putting It All Together (A Real Example)

Let's write a function that finds the length of a list.

A `List` is either:
1.  Empty (`Nil`)
2.  A generic Item connected to another List (`Cons`)

```haskell
type List a
    | Nil                  -- The end of the line
    | Cons (a, List a)     -- An item AND the rest of the list

let length list
    | Nil -> 0
    | Cons (item, rest) -> 1 + (length rest)
```

**How it works:**
*   We use `|` to handle the two shapes of a List.
*   If it's `Nil`, the length is 0.
*   If it's `Cons`, we take 1 (for the item) and add the `length` of the `rest`.

This is **Recursion**. We defined the length of the list by asking for the length of the smaller list inside it.

---


## Summary for the Traveler

*   **`|` (OR)**: Options, Choices, Branching.
*   **`,` (AND)**: Groups, Records, Tuples.
*   **`->` (ACTION)**: Transformation, Functions, Flow.
*   **`impl`**: Giving superpowers to types.
*   **`given`**: Prerequisites (Context).

You now speak the language of F-Lang. Go forth and build logic!
