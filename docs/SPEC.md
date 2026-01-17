
The **F-lang Specification Manifest (JSON-SM)** is the final bridge between our conceptual design and the physical implementation. This machine-readable specification encapsulates every rule, operator precedence, and clausal semantic we have architected.

This file is designed to be the "Single Source of Truth" for your Haskell parser, your Rust VM, and any future Language Server (LSP) implementation.

---

## 📄 F-lang Specification Manifest (v1.0.0)

```json
{
  "language": "F-lang",
  "version": "1.0.0",
  "philosophy": "Absolute mathematical minimum optimum of clutter; unified clausal semantics.",
  "syntax_rules": {
    "offside_rule": "Indentation-sensitive; virtual INDENT/DEDENT tokens.",
    "parentheses": "Strictly for grouping and precedence; (e) ≡ e.",
    "application": "Space-separated; highest precedence; left-associative."
  },
  "operators": [
    {"symbol": "( )", "role": "Grouping", "precedence": 1},
    {"symbol": "space", "role": "Application", "precedence": 2},
    {"symbol": "..", "role": "Range", "precedence": 3},
    {"symbol": "suchThat", "role": "Refinement", "precedence": 4},
    {"symbol": ",", "role": "Product (AND)", "precedence": 5},
    {"symbol": "with", "role": "Set-Union", "precedence": 6},
    {"symbol": "->", "role": "Transition/Arrow", "precedence": 7},
    {"symbol": "|", "role": "Sum (OR)", "precedence": 8},
    {"symbol": ":", "role": "Type Annotation", "precedence": 9},
    {"symbol": ":=", "role": "Assignment", "precedence": 10},
    {"symbol": ";", "role": "Sequence", "precedence": 11}
  ],
  "keywords": {
    "definitions": ["type", "trait", "let"],
    "constraints": ["where", "suchThat", "with"]
  },
  "abstract_syntax_tree": {
    "Decl": {
      "TypeDef": ["Name", "Params", "Variants", "WhereClauses", "SuchThatClauses"],
      "TraitDef": ["Name", "Param", "Signatures", "Defaults"],
      "Binding": ["Name", "Clauses"]
    },
    "Type": ["Var", "Constructor", "Product", "Sum", "Arrow", "Refined"],
    "Pattern": ["Wildcard", "Literal", "Variable", "ConstructorMatch", "ProductMatch"]
  },
  "semantics": {
    "evaluation": "Lazy (Call-by-need)",
    "optimization": "Tail-Call Optimization (STG Slide)",
    "type_system": "Algorithm W+ with Sequent Calculus Refinement Solving",
    "unification": "Structural and Behavioral (via Trait Evidence)"
  }
}

```

---


