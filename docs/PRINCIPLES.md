
# The Principles ("set in stone")

## The Trinity
- `|` (*OR*, fork)-- a Universal, most abstract and general Algebraic Sum Type
- `,` (*AND*, join) -- a Universal, most abstract and general Algebraic Product Type
- `->` (*IMPLY*, maps to, step) - a Universal, most abstract and general Step (in a particular direction)

We desugar to just these Universal constructs (most basic structural elements of a DAG).

### Algebraic Data Types are built-in.
- `|`, `,` and `->` (**maps to**) are 'built-in' (in the fabric of Reality).
- Every occurrence of any of these symbols denote a corresponding proper Algebraic Data Type.

We desugar ADTS to just there Universal Types.

### Universal unbound Nesting
- `|` and `,`, as well as `->` can be *naturally* (I am serious) *nested*, and this is how **Nested** Algebraic Types are defined (desugar to).
- Haskell nicely defines a Tuple type `(,)`, and has a whole sophisticated machinery to be able to do so. We resist the temptation.

### Indentation 
- Everything is an expresssion, which denotes a value it is reducible to.
- We use indentation to define and express code block-structure (expressions).

### Minimal uniform syntax
- A Clause is an ultimate building block of the uniform, minimalist syntax, used consistently with indentation. No extra symbol or keyword clutter.
- When we are defining a function we shall prefer clauses. When we use clauses we should not use match or case, just clauses and |. The rule is to prefer the uniform and minimalist clausal  │ │   notation whenever possible, and reverse the "full" match or case expressions ONLY for special cases.
- Prefer minimalist syntax in defining function clause -- use only `|` and indentation.

### Unified Syntax
-   `match | p -> e`: Generalized clausal mapping.
-   `let f | p -> e`: Functions as clausal mappings.
-   `if p then a else b`: Sugar for clausal choice.

### Mathematical Integrity
-   `->`: Only for curried signatures and mappings.
-   `,`: Only for product types and data.
-   `|`: Only for sum types and clausal branching. 

### Functions defined by Clauses
- The prefered form (shape) must be `let <function_name> | <patterns> -> <body> | <patterns> -> <body>` -- exactly the **Uniform** Anonymous Mapping syntax
- This form is shared with the generalized pattern-mathing -- an idividual (or single) Clause syntax. This is the most crucial part.
- Ocaml's specialized `function` expression, which pattern-matches on the implicit last argument is the inspiration.

### The arrow
- In mathematics the `->` arrows used to denote an anonymous *mapping*, i.e. `x -> x + 1` with a well-defined meaning "x maps to".
- `->` traditionally stands for *maps to*, so its use *ONLY* in the Curried Functions type-signatures is justified.
- The classic Haskell use of the arrow `->` in the Lambda Notation -- `\x -> \y -> x + y` is the only way to denote Currying properly.
- It is also used with individual Clauses in pattern-matching expressions, which semantically is exactly an anonymous mapping.

These must be the *ONLY* uses, to remove clutter and ambiguity. One use at the Type-level, and two uses at the level of Code.

### Direction
- A direction of a DAG is not arbitrary and cannot be reversed on a whim, just because that would be a structural "dual".
- Direction "Naturally" arise from the flow of implications (connecting every single step). Implications are not reversible (have no inverse).

## The Clauses
- An Universal Implication (Modus Ponens) can be informally denoted as a single IF-THEN clause -- "If This (is true) Then That (must be true)".
- Some functions can be defined as a set (disjoint union) of individual clauses, so that each clause is "naturally" defines a *partial function*, thus partitioning the domain.
- A Sum-Type is indeed a set (a disjoint union) of individual clauses, which formalizes the explicit partitioning of the domain.
- Pattern-matching expressions on Sum-Types or results of Partial Functions have the particular shapes which are "structural duals".
- It follows that a (single) clause (which denotes a single **arrow**) is the most abstract and most general, universal building block.
- The "Nested lets are nested lambdas with an in-place application" -- the famous structural isomorphism can be reduced to clauses.

## The homage to mathematical notation
- `_`  (juxtaposition) -- function application. The finest structural element of any written human language. This is also "naturally" denotes Partial Application.
- `=` (the equal sign) -- an immutable binding. We are not Platonists -- not mere ideas in a vacuum. The notion of an persistent **Environment** is necessary.
- `()` (parenthesis) -- *ONLY* for precedence (explicit nesting) and explicit grouping, just as in mathematics.
- `suchThat` (a keyword) -- denotes a refinement -- nested predicates, as in the classic Set-comprehension notation.
- `where` (a keyword) -- denotes a nested set of bindings, which implicitly defines terms before they are being used.
- `let` (a keyword) -- reduces cognitive burden by uniformly unifying all the binding sites.
- `with` (a keyword) -- a better 'word' to denote the Universal **Set Union** operation (at the level of abstract interfaces)
- `'` (single quote) -- a prime, as in `let f' = ... in ...`

## Currying and Partial application
- Uniformity (unification): Every function, including Type-Constructors, is "really" a single-argument `lambda` and every function application is of a curried function (partial or complete).
- Every multi-argument Type-Signature is a Curried signature with `->` *arrows* between argument types.
- Just as in SML or Haskell `f x y` is semantically equal to `\x -> \y ->`
- Clearly captures the notion of a "partially filled enzyme", or just "Not all necessary and sufficient conditions are meet yet" for a reaction to proceed.
- Currying and Partial Application unifies the single-argument `lambda` expression, and with implicit nesting it captures the notion of "arrows going in".
- There is another fundamental view -- "under-application" is a "suspension", while "over-application" is an implicit recursion.

## The Class-instance, Trait-impl dillema
- `class` (a keyword) -- the original Haskell notation for Wadler's **Type-Classes**. All consistent with the language of Predicate Logic.
- `instance` (a keyword) -- denotes a particular instance of a given class. This one is simply beautiful.
- `trait` + `impl` -- decoupled from the implicit notion of a rigid class hierarchy (The **Set-Subset** relation) to a **Set-Union** operation.

## Advanced Syntactic forms
- `:` (colon) -- type annotation. Universal, after any expression (Everything is an expression).
- `...` (triple dot) -- and so on
- `1..5` (standard range notation)

## Tribute to SML/NJ (and Mlton)
- The uniform clause syntax for defining functions by clauses (|) (without the `fun` keyword).
- `andAlso` (a keyword) for short-circuiting logical Connective **AND** in the Predicate Logic sections.
- `orElse` (a keyword) for short-circuiting logical Connective **OR** in the Predicate Logic sections.
- `suchThat` (a keyword) for a set of Predicate that follow

## Type-Level Syntax
- `->` (an arrow) must be used in Type-Signatures (of Curried functions)
- `,` (a comma) must be used for an in-place Product Type definition

### Constructors
- Capitalized Type-Names (Type-Constructors).
- Capitalized Sum-Type clauses (Data-Constructors and implicit "type-tags").

### Traits
- Capitalized Trait-Names (Abstract Data Types).
- Capitalized named Trait-Bounds (Type-Level predicates).
- The **Trait-Subtrait** relation shall be expressed with `<:` and `>:` since Traits could, in theory, have a "lower" and "upper" bounds.
- Trait Bounds are just type-level Equations (Equational Reasoning)

## Disambibuation
- Every function is uniformly (potentially) a Curried Function, including parameterized Type-Constructors and Data-Constructors.
- In Trait definitions we use `->` instead of `,` ONLY for type-signatures of Curried Functions (this is a nasty kludge).
- Trait bounds has to be specified *before* the where clause, simply because mathematical constraints comes prior to code.
- We say `suchThat` when what follows are mathematical equations -- statements of truth. **Logical Constraints** (required predicares), complex **Trait-Bound** (mathematical equations).
- In general, we use `suchThat` when we write mathematics (equational reasoning), and we use `where` when we write the code (binding in the Environemnt).
- At the **Type-Level** we naturally use `suchThat`

## Style
- `Maybe` instead of `Option` -- `Just a | Nothing` is much more classy than `Some a | None`
- `Result` instead of `Either` -- `Left | Right` are a disgrace. 
- Either can be defined for compatibility, as well as Option, as type-aliases (`where Some a = Just a`, etc).

## The core syntacitc forms
- Haskell style generic and uniform multi-clause  `case <boolean exoression> of  <expression> `
- `if` is a syntactic sugar for exactly two-clause `case` with required `else` clause.
- `when` is a single-clause `case` without an `else` clause
- Generalized and uniform multi-clause `match | <pattterns> -> <body> | <pattern> -> <body> ... `
- A function defined by clauses has the same syntax and semantics as `match` multi-clause expression. It desugars into "a single match-body" function.
- Maybe should generalize to just one single generalized `match` expression, and case being its specialization.

## Imperarive syntactic forms
- `{}` (curly braces) -- imperative blocks
- `;` (semicolon) -- imperative explicit delimiter
- `:=` (colon-equal) -- imperative assignment (a destructive over-write)
