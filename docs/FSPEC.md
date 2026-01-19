# FSpec: The F-Lang Testing Standard

FSpec is the standard testing ecosystem for F-Lang, designed to be self-verifying and declarative. It leverages the language's advanced syntax (macros and comprehensions) to provide an expressive testing DSL.

## 1. Standard Library: `lib/fspec.fl`

The core implementation defines the assertion primitives and the test runner.

```haskell
-- lib/fspec.fl

-- | The Result Type: (Passed?, Message)
type TestResult = (Bool, String)

-- | The Core Assertion Primitive
-- Usage: actual `shouldBe` expected
let shouldBe = (actual, expected) ->
    | actual == expected -> (True, "")
    | otherwise          -> (False, "Expected " ++ show expected ++ ", but got " ++ show actual)

-- | Macro Assertion for Arbitrary Boolean Logic
-- Usage: check `(x > 10)
-- Note: Uses the macro system to capture the expression for reporting.
let check = quoted_expr -> {
    let result = eval quoted_expr ;
    | result    -> (True, "")
    | otherwise -> (False, "Check failed: " ++ show quoted_expr)
}

-- | The Test Runner
-- Consumes a suite name and a list of TestResults.
let runSpec = (suite_name, tests) -> {
    putLine ("\n📦 Suite: " , suite_name) ;
    
    -- Stream results, print progress, and collect failures.
    let failures = [ msg | 
        (passed, msg) <- tests,
        let _ = ( | passed -> putStr "." | otherwise -> putStr "F" ),
        not passed
    ] ;

    putLine "" ;
    
    | isEmpty failures -> putLine "✨ All tests passed."
    | otherwise -> {
        putLine ("💥 " , length failures , " failures detected:") ;
        mapM_ (\err -> putLine ("  - " , err)) failures
    }
}
```

## 2. Usage Patterns

FSpec adopts a Scala-like philosophy where test suites are treated as comprehensions.

### Unit Testing
Use list syntax `[...]` to group assertions.

```haskell
runSpec "Math" [
    (1 + 1) `shouldBe` 2,
    head [1,2] `shouldBe` 1
]
```

### Property-Based Testing
Use generator syntax `<-` to run assertions over data streams.

```haskell
runSpec "Properties" [
    check `(x * 2 % 2 == 0) | x <- 1..100
]
```

## 3. Self-Verification: `tests/stdlib_test.fl`

The standard library is verified using FSpec itself.

```haskell
import lib.fspec

let main = {
    -- 1. Test List Primitives
    runSpec "List Ops" [
        length [] `shouldBe` 0,
        length [1, 2, 3] `shouldBe` 3,
        
        -- Pattern Matching Guard in Test
        head `shouldBe` h | (h, t) <- [ (1, [2]), (5, []) ],
                            let head = listHead (h, t)
    ] ;

    -- 2. Test String Primitives (Unicode Check)
    runSpec "Unicode Safety" [
        "Hello" `shouldBe` "Hello",
        length "🟢" `shouldBe` 1,
        
        -- Property: Concatenation preserves length
        (length (s1 ++ s2)) `shouldBe` (len1 + len2) | 
            s1 <- ["A", "Γ", "😊"],
            s2 <- ["B", "Δ", "🚀"],
            let len1 = length s1,
            let len2 = length s2
    ]
}
```