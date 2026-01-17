
# The Principles ("set in stone")

## The Trinity
- `|` (*OR*, fork)-- a Universal, most abstract and general Algebraic Sum Type
- `,` (*AND*, join) -- a Universal, most abstract and general Algebraic Product Type
- `->` (*IMPLY*, step) - a Universal, most abstract and general Step (in a particular direction)

These are 'built-in'. Haskell nicely defines a tuple type `(,)`, and has a whole sophisticated machinery to be able to do so. We resist the temptation.

## The Clauses
- An Universal Implication (Modus Ponens) can be informally denoted as a single IF-THEN clause -- "If This (is true) Then That (must be true)".
- Some funtions can be defined as a set (disjount union) of idividual clauses, so that each clause is "naturally" defiens a *parial function*, thus partitioning the domain.
- A Sum-Type is indded a set (a disjount union) of individual clauses, which formalizes the explicit partitioning of the domain.
- Pattern-matching expressions on Sum-Types or results of Partial Functions have the particular shapes which are "structural duals".
- It follows that a (single) clause (which denotes a single **arrow**) is the most abstract and most general, universal building block.
- The "Nested lets are nested lambdas with an in-place application" -- the famous structual isomorphism can be reduced to clauses.

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
- Clearly capures the notion of a "partially filled enzyme", or just "Not all necessary and sufficent conditions are meet yet" for a reaction to proceed.
- Currying and Partial Application unifies the single-argument `lambda` expression, and with impliit nesting it capures the notion of "arrows going in".
- There is another fundamental view -- "under-application" is a "suspension", while "over-application" is an implicit recursion.

## The Class-instance, Trait-impl dillema
- `class` (a keyword) -- the original Haskell notation for Wadler's **Type-Classes**. All consistent with the language of Predicate Logic.
- `instance` (a keyword) -- denotes a particualr instance of a given class. This one is simply beautiful.
- `trait` + `impl` -- decoupled from the implicit notion of a rigid class hierarchy (The **Set-Subset** relation) to a **Set-Union** operation.

## Advanced Syntactic forms
- `:` (colon) -- type annotation. Universal, after any expression (Evetything is an expression).
- `...` (triple dot) -- and so on
- `1..5` (standard range notation)

## Imperarive syntactic forms
- `{}` (curly braces) -- imperative blocks
- `;` (semicolon) -- imperative explicit delimiter
- `:=` (colon-equal) -- imperative assignment (a destructive over-write)
