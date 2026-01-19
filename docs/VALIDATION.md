# Project Status & Validation

## 1. Syntactic Consistency

*   **Operator Precedence**: Standardized across specification and parser.
    1.  **Application**: Highest (Left-associative).
    2.  **Refinement** (`suchThat` / `where`): Level 2.
    3.  **Product** (`,`): Level 3.
    4.  **Update** (`with`): Level 4.
    5.  **Sum** (`|`): Level 5.
    6.  **Flow** (`->`): Weakest (Level 6).
*   **Constructor Application**: Standardized to `Cons (head, tail)` (Product Application) in documentation and examples.

## 2. Core Implementation Status

*   **AST (`src/FLang/Core.hs`)**: Complete binary-node structure (`GNode`, `Decl`) reflecting the "Trinity" philosophy.
*   **Parser (`src/FLang/Parser.hs`)**: Robust Megaparsec implementation handling precedence and indentation (Off-side Rule).
*   **Lexer (`src/FLang/Lexer.hs`)**: Handles whitespace, tokenization, and UTF-8 support.

## 3. Mathematical Verification

The language strictly maps to a **Monoidal Category** with **Coproducts**:

*   **Product (`,`)** $\rightarrow$ Monoidal Product ($\times$).
*   **Sum** (`|`) $\rightarrow$ Coproduct ($+$).
*   **Arrow** (`->`) $\rightarrow$ Exponential Object ($B^A$).
*   **Evaluation** $\rightarrow$ Evaluation Morphism.

### Graph Properties
Every F-Lang program represents a DAG:
*   **Vertex**: Data constructor or function node.
*   **Edge** (`->`): Directed flow of transformation.
*   **Fork** (`|`): Coproduct injection (Choice).
*   **Join** (`,`): Product formation (Parallelism).

The clausal function definition `| A -> B | C -> D` is formally verified as a sum of morphisms.