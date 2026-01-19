# Unicode Support & String Handling

F-Lang employs a "Strict UTF-8 at Boundary" strategy, ensuring correctness for internationalization while maintaining performance for standard operations.

## 1. Encoding Strategy

We adopt the **Rust Invariant**: A string value in F-Lang **must** be valid UTF-8. It is impossible to construct an invalid string within the VM.

*   **Source Code**: Must be UTF-8.
*   **Internal Memory**: UTF-8 bytes (`Vec<u8>` or equivalent).
*   **Input Boundary**: Bytes entering the system are validated. Invalid sequences are rejected or replaced with `` (U+FFFD).

## 2. Frontend Implementation (Stage 0)

The Haskell-based frontend avoids the legacy `String` type in favor of `Data.Text` to ensure performance and correctness.

**`src/FLang/CoreIR.hs`**:
```haskell
import qualified Data.Text as T

data Expr
    = Var T.Text             // Variable names are UTF-8
    | Lit Literal
    | ...

data Literal
    = LInt Int
    | LStr T.Text            // String Literals are packed UTF-8
```

**`src/FLang/Lexer.hs`**:
The Lexer processes the source as `Text`, enabling native Unicode identifiers.

## 3. Runtime Implementation (Stage 1)

The Rust VM utilizes `Rc<String>` for persistent, shared string values.

**`src/vm/lib.rs`**:
```rust
#[derive(Clone)]
pub enum Value {
    Node(Rc<Closure>),
    Int(i64),
    /// A persistent, immutable UTF-8 string.
    Str(Rc<String>), 
    /// The Unicode Scalar Value (equivalent to Haskell Char).
    Char(char),      
    WorldToken,
}
```

**Note**: `char` is a 32-bit Unicode Scalar Value, serving as the atom for text processing.

## 4. Input/Output Handling

Sanitization occurs at the I/O boundary.

**`src/vm/io.rs`**:
```rust
impl Machine {
    /// Primitive: getLine
    /// Reads raw bytes and sanitizes to UTF-8.
    pub fn prim_get_line(mut self) -> Self {
        use std::io::{stdin, BufRead};
        
        let stdin = stdin();
        let mut handle = stdin.lock();
        let mut buffer = Vec::new();
        
        match handle.read_until(b'\n', &mut buffer) {
            Ok(_) => {
                // Conversion: String::from_utf8_lossy
                // Guarantees the runtime invariant.
                let s = String::from_utf8_lossy(&buffer).to_string();
                let clean_s = s.trim_end_matches(&['\r', '\n'][..]).to_string();
                
                self.push(Value::Str(Rc::new(clean_s)))
                    .push(Value::WorldToken)
            }
            Err(_) => {
                self.push(Value::Str(Rc::new(String::new())))
                    .push(Value::WorldToken)
            }
        }
    }
}
```

## 5. String Manipulation

F-Lang supports iterator-based string manipulation. Indexing is discouraged due to variable-width encoding.

**`prim_str_uncons`**:
Applying a Sum choice (`|`) to a String treats it as a list of `char`.

*   **Syntax**: `| str -> (head, tail)`
*   **Semantics**: `head` is the first `char`; `tail` is the remaining substring.

## Summary

| Layer | Encoding | Implementation |
| :--- | :--- | :--- |
| **Source File** | UTF-8 | Haskell `Text` Lexer |
| **Compiler IR** | UTF-8 | `Data.Text` |
| **VM Storage** | UTF-8 | `Rc<String>` (Rust) |
| **VM Atom** | Unicode Scalar | `char` (u32) |
| **Input (Stdin)** | Raw Bytes | `String::from_utf8_lossy` |
| **Output (Stdout)** | UTF-8 Bytes | Rust `print!` |