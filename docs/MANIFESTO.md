# The F-Lang Manifesto

## I. Core Philosophy

F-Lang eliminates the artificial distinction between **structure** (data), **behavior** (traits), and **logic** (refinements). It treats source code as a set of mathematical constraints resolved into an optimized state machine. The design prioritizes:
*   **Minimalism**: Zero syntactic noise.
*   **Uniformity**: Consistent application of clausal logic.
*   **Rigor**: Type-level enforcement of invariants.

## II. Syntactic Structure

The syntax is reduced to a "Minimum Optimum" set of operators, utilizing five levels of precedence to manage complexity:

*   **Application**: `f x` (Highest Precedence)
*   **Product**: `a, b` (Logical AND / Pairing)
*   **Arrow**: `a -> b` (Mapping / Implication)
*   **Sum**: `A | B` (Logical OR / Choice)
*   **Grouping**: `( )` (Identity / Override)

## III. The Three Pillars of Refinement

Every type is a "Managed Type," subject to three layers of verification:

1.  **Structure (`type`)**: Defined as a Sum of Products.
2.  **Behavior (`where`)**: Conditional constraints proving trait satisfaction.
3.  **Integrity (`suchThat`)**: Logical predicates discharged by a Sequent Calculus solver.

## IV. Technical Specification Summary

| Component | Technology | Role |
| :--- | :--- | :--- |
| **Frontend** | Haskell | Lexing, Precedence Parsing, AST Generation. |
| **Inference** | Algorithm W+ | Clausal constraint propagation. |
| **Solver** | Sequent Calculus | Discharging `suchThat` proof obligations. |
| **Backend** | Rust VM | **STG Machine** execution (Spineless Tagless G-Machine). |
| **Memory** | Immutability/GC | TCO-optimized stack frames with `Slide` instructions. |

## V. Syntactic Landscape

F-Lang reconciles mathematical notation with practical imperative control:

1.  **Refinement**: `suchThat` and `where` for logical and structural constraints.
2.  **Annotation**: `:` for type assertions.
3.  **Advanced**: `..` for ranges and `...` for continuations.
4.  **Imperative**: `{}` blocks, `;` sequencing, and `:=` destructive assignment (strictly controlled).