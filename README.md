Swift Style Guide
=================

Source Files
------------

### Filenames

  * All Swift source filenames end with the extension *.swift*.
  * A file containing a single type `MyType` is named *MyType.swift*. (It may
    also contain some helper functions or extensions.)
  * A file containing a single extension to a type `MyType` that adds
    conformance to a protocol `MyProtocol` is named *MyType+MyProtocol.swift*.
  * A file containing multiple extensions to a type `MyType` can be named more
    generally, as long as it is prefixed with *MyType+*
    (e.g., *MyType+Additions.swift*).
  * A file containing related declarations that are not scoped under a common
    type or namespace can be named descriptively.

### File Structure

Organize the material in each file as follows:

  1. Import statements for native Apple libraries (in alphabetical order)
  2. Import statements for third-party libraries (in alphabetical order)
  3. Types
      1. Structs
      2. Classes
      3. Enums
  4. Functions
  5. Extensions

**Exactly one blank line** separates each section that is present.

Next, organize the members of a type as follows:

  1. Initializers
  2. Deinitializer
  3. Static properties
  4. Stored properties
  5. Computed properties
  6. Static methods
  7. Instance methods
  8. Nested types
      1. Structs
      2. Classes
      3. Enums

For each section, list the public API first before the private API.
**Exactly one blank line** separates each individual member.

**NOTE:** You do not need to label each section with a `MARK:` comment.

General Formatting
------------------

### Semicolons

Do **NOT** use a semicolon at the end of a statement. (It is okay for them to
appear inside a string literal or comment.)

### Curly Braces

In control flow statements (i.e., `if`, `switch`, `for`, `while`, etc.),
functions, type implementations, et al.:

  * Curly braces generally open on the first line but close on a new line.
    
    ```swift
    // 🙂 CORRECT
    if conditionIsTrue {
        …
    }

    // 🙂 CORRECT
    func myMethod() {
        …
    }

    // 🙂 CORRECT
    struct MyType {
        …
    }

    // 😡 WRONG
    if conditionIsTrue
    {
        …
    }
    ```

  * However, if the body is empty, then the curly braces appear on the first
    line with no whitespace in between.

    ```swift
    // 🙂 CORRECT
    func myMethod() {}

    // 😡 WRONG
    func myMethod() {
    }
    ```

  * Always use curly braces, even when optional.

### Control Flow

Control flow keywords should always begin a line.

```swift
// 🙂 CORRECT
do {
    …
}
catch {
    …
}

// 😡 WRONG
do {
    …
} catch {
    …
}
```

### Indentation

Use **4 spaces** for indentation.

### Column Limit

Limit each line of code (LOC) to a maximum of **80 characters**. (This also
takes indentation into account.)

### Statements

A single LOC should have no more than 1 statement.

### Line Wrapping

These rules apply to LOCs that normally surpass the 80-character limit:

  * When breaking an expression into multiple lines, indent all continuation
    lines one level.
  * Never wrap an expression inside the `subscript` operator. Instead, declare
    a constant which holds that expression, and use the constant in the
    operator.
  * When breaking lines with operators, the operator should begin the
    continuation line.
  * Property access and method calls should include the `.` on the continuation
    line.
  * When breaking function calls/signatures, every argument/parameter gets at
    least one line.
  * Recursively apply the above rules as needed.

### Blank Lines

A single blank line also appears in the following locations:

  * Between parts of code with distinct purposes within a function or computed
    property.
  * Before the first member of a type (*mandatory* if the member has a
    documentation comment, and *optional* if it does not).

Do not put a blank line as the first line of a function or computed property.
If the start of the implementation is logically separate from the declaration,
rethink your naming.

### Parentheses

  * Do **NOT** wrap the condition of a control flow statement in parentheses.
    If the line it is on surpasses the 80-character limit, then wrap the
    condition in parentheses and follow the rules of line wrapping.
  * Function calls/signatures have no space in between the function name and the
    parentheses.
  * If a line that contains a mathematical expression or logical condition
    surpasses the 80-character limit, then wrap the expression in parentheses
    and follow the rules of line wrapping.
  * Always group similar logical conditions with parentheses.
  * If the condition in a ternary operation uses a binary operator, then wrap it
    in parentheses.

```swift
// 🙂 CORRECT
if conditionIsTrue {
    …
}

// 😡 WRONG
if (conditionIsTrue) {
    …
}

// 🙂 CORRECT
let result = (
    anExpression
    + thatIsMadeUpOf
    * aLargeNumber
    + ofTerms
    / andTherefore
    % mustBeWrapped
    + (andWeWill - keepMakingItLonger * soThatWeHave / aContrivedExample)
)

if (conditionIsTrue && relatedConditionIsTrue) || separateConditionIsTrue {
    …
}
```
