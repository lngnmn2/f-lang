# F-Lang Specification Manifest

This document defines the F-Lang specification in a machine-readable JSON format (JSON-SM). It serves as the authoritative reference for the parser, VM, and tooling.

## F-Lang Specification Manifest (v1.0.0)

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
    {"symbol": "suchThat", "role": "Logical Refinement", "precedence": 4},
    {"symbol": ",", "role": "Product (AND)", "precedence": 5},
    {"symbol": "with", "role": "Set-Union", "precedence": 6},
    {"symbol": "->", "role": "Transition/Arrow", "precedence": 7},
    {"symbol": "|", "role": "Sum (OR)", "precedence": 8},
    {"symbol": "andAlso", "role": "Short-circuit AND", "precedence": 9},
    {"symbol": "orElse", "role": "Short-circuit OR", "precedence": 9},
    {"symbol": "<:", "role": "Subtrait Bound (Traditional)", "precedence": 10},
    {"symbol": ">:", "role": "Supertrait Bound", "precedence": 10},
    {"symbol": "where", "role": "Local Environment", "precedence": 11},
    {"symbol": ":", "role": "Type Annotation / Trait Supertype", "precedence": 12},
    {"symbol": ":=", "role": "Assignment", "precedence": 13},
    {"symbol": ";", "role": "Sequence", "precedence": 14}
  ],
  "keywords": {
    "definitions": ["type", "trait", "let"],
    "constraints": ["where", "suchThat", "with", "given"]
  },
  "abstract_syntax_tree": {
    "Decl": {
      "TypeDef": ["Name", "Params", "Variants", "WhereClauses", "SuchThatClauses"],
      "TraitDef": ["Name", "Param", "SuperTraits (via ':')", "Signatures"],
      "ImplDef": ["Trait", "Type", "GivenConstraints (via '<:')", "Methods"],
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