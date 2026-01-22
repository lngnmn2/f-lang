# The F-Lang Tutorial: Math, Magic, and No More Crashes

Welcome to F-Lang! This isn't just a programming language; it's a way of thinking.

If you know how to add ($+$), multiply ($\times$), and follow an arrow ($\rightarrow$), you already understand the deep magic behind F-Lang. We built this language because we wanted to stop writing bugs. We found that the best way to do that was to stop "coding" and start doing "math."

Here is the story of why F-Lang exists and how it works.

---\n

## 1. The Playground: Sets (Types)

Imagine a giant playground with different buckets.
*   One bucket has all the Integers: {\(\dots\), -1, 0, 1, 2, \(\dots\)}. We call this bucket `Int`.
*   One bucket has only two things: {True, False}. We call this bucket `Bool`.
*   One bucket has every possible String: {\("hello"\), \("world"\), \(\dots\)}. We call this bucket `String`.

In math, we call these **Sets**. In F-Lang, we call them **Types**.

When we say `x : Int`, we are just writing the math symbol $x \in \mathbb{Z}$ ("x is in the set of Integers").

**Why?**
If you try to put a `String` into the `Int` bucket, it doesn't fit. In other languages, you might force it, and your program crashes later. In F-Lang, the universe (the compiler) says "No" before you even run it. This creates a **Type-Safe** world.

---\n

## 2. The Building Blocks: Logic

We need to build complex things out of simple things. We only need two mathematical tools for this: **AND** and **OR**.

### The "AND" (Multiplication)
Imagine you have a red box and a blue box. You want to carry *both* of them.
*   **Math:** Cartesian Product ($A \times B$).
*   **F-Lang:** `(A, B)` (The Pair).

If you have 2 shirts (Red, Blue) and 3 pants (Jeans, Shorts, Skirt), how many outfits can you make? $2 \times 3 = 6$.
This is why we use the comma `,` to mean **AND**. It multiplies the possibilities.

### The "OR" (Addition)
Imagine a fork in the road. You can go Left **OR** Right. You cannot go both ways.
*   **Math:** Disjoint Union ($A + B$).
*   **F-Lang:** `A | B` (The Sum).

If you can have chocolate (1 flavor) **OR** vanilla (1 flavor), you have $1 + 1 = 2$ choices.
This is why we use the bar `|` to mean **OR**. It adds the possibilities.

**The "Why":**
Most bugs happen because we forget a possibility (a "path"). By treating data as **Sum Types** (`|`), F-Lang forces you to handle every single path. You can't forget the "Vanilla" path, or the code won't compile.

---\n

## 3. The Arrows: Functions

In math, a function $f: A \rightarrow B$ is a mapping. It draws a line from every item in Set $A$ to an item in Set $B$.

In F-Lang, we write:
```haskell
f : A -> B
```

**Composition: The Lego Principle**
If you have a function $f$ that turns `Apples -> Slices`, and a function $g$ that turns `Slices -> Pie`, you can snap them together!
$$h(x) = g(f(x))$$
In F-Lang, we just chain them.

**The "Why":**
We don't build big, scary programs. We write tiny, simple functions that are obviously correct ($1+1=2$). Then we compose them like Lego bricks. If the small bricks are solid, the castle is solid.

---\n

## 4. Traits: Sets of Sets

This is where it gets cool. Imagine we want to talk about "Any bucket where you can check if two things are equal."
*   Can you check Integers? Yes ($1 = 1$).
*   Can you check Booleans? Yes ($True = True$).
*   Can you check Functions? No (usually).

We call this a **Trait**. A Trait is a **Set of Types**.
If `Int` is inside the `Eq` (Equality) set, we say "Int implements Eq."

**Code Level:**
```haskell
trait Eq a where
    (==) : a -> a -> Bool
```
This defines a rule: "To be in the `Eq` club, you must have a `==` function."

**Math Level:**
This is **Bounded Quantification**. When we write a function `sort <T>(list: List T)`, we can't just sort *anything*. We need to compare them!
So we say: "For all types $T$, WHERE $T$ is in the set `Ord` (Orderable)..."
```haskell
given Ord(a)
```
**Why?**
This lets us write generic code that works on *any* data, as long as that data follows the rules. It makes code reusable and safe.

---\n

## 5. The Advanced Magic: Category Theory

Now for the "University Math" made simple. We use patterns from a field called **Category Theory**. Don't be scared by the names!

### The Monoid (The Combiner)
A Monoid is just a fancy name for a set that has:
1.  A way to smash two things together ($+$).
2.  A "Zero" value that changes nothing.

*   **Integers:** $0$ is the zero. $+$ is the smash. ($5 + 0 = 5$).
*   **Strings:** `""` (empty string) is the zero. concatenation is the smash. (`"Hi" + "" = "Hi"`).
*   **Lists:** `[]` is the zero. joining is the smash.

**Why?**
If we know something is a Monoid, we can fold (smash) a list of a million items into one item automatically. We don't need to write a loop. We just say "Smash it."

### The Functor (The Magic Box)
Imagine a value wrapped in a box. `Just 5` is a `5` inside a `Maybe` box.
A **Functor** is a box that lets you use a function on the inside *without opening the box*.

If you have a function `double(x) = x * 2`:
*   Normal: `double(5) = 10`.
*   Functor: `map(double, Box(5)) = Box(10)`.

**Why?**
This handles errors for us!
*   If the box is empty (`Nothing`), `map` does nothing.
*   If the box has a value (`Just 5`), `map` works.
You never have to check for `null`. The math of the Functor handles the empty case automatically.

---\n

## Summary: The Philosophy

We made F-Lang choices for specific reasons:

1.  **Why Types?** Because Types are Sets, and Sets adhere to Logic. If the Logic is valid, the Program is valid.
2.  **Why `|` and `,`?** Because they are the fundamental operations of Algebra (Sum and Product). They cover every way to structure data.
3.  **Why Traits?** To categorize Types by their behavior, not their name.
4.  **Why Monoids and Functors?** To use proven mathematical patterns instead of inventing our own messy loops.

**In F-Lang, we don't fix bugs. We make them impossible.**

Go forth and calculate!