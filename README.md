Swift Style Guide
=================

Source Files
------------

### Filenames

  * All Swift source filenames are `UpperCamelCase` and end with the extension
    *.swift*.
  * If the file contains a single type `MyType`, then it is named
    *MyType.swift*.
  * If the file contains a single extension to a type `MyType` that adds
    conformance to a protocol `MyProtocol`, then it is named
    *MyType+MyProtocol.swift*.
  * If the file contains multiple extensions to a type `MyType`, then it is
    named more generally, as long as it is prefixed with *MyType+*
    (e.g., *MyType+Additions.swift*).
  * All other files are named appropriately based on their contents.

### File Structure

The content in a Swift source file is organized as follows:

  1. Import statements for native Apple libraries (in alphabetical order)
  2. Import statements for third-party libraries (in alphabetical order)
  3. Types
      1. Structs
      2. Enums
      3. Classes
      4. Actors
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
      2. Enums
      3. Classes
      4. Actors

For each section, list the public API first before the private API.
**Exactly one blank line** separates each individual member.

**NOTE:** You do not need to label each section with a `MARK:` comment.

General Formatting
------------------

### Indentation

Use **4 spaces** for indentation.

### Column Limit

Limit each line to a maximum of **80 characters**. (This also takes indentation
levels into account.)

### Statements

A single line should have no more than 1 statement.

### Semicolons

Do **NOT** use a semicolon at the end of a statement. (It is okay for them to
appear inside a string literal or comment.)

### Curly Braces

  * Always use curly braces on control flow blocks, even when optional.
  * The opening brace is on the same line as the start of the block the braces
    wrap, separated by a space, if the line can fit. Otherwise, follow rule 6 in
    [Line Wrapping](#line-wrapping).
  * There is a space between the opening brace of a closure and its parameters.
  * Empty blocks may be written as `{}`.

```swift
// 🙂 CORRECT
if conditionIsTrue {
    …
}

// 😡 WRONG
if conditionIsTrue
{
    …
}
```

```swift
let closure = { (parameters) in
    …
}
```

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

### Line Wrapping

These rules apply to lines that normally surpass (or do not fit) the
80-character limit:

  1. Never wrap an expression inside the `subscript` operator.
  2. If an expression with binary operators cannot fit on the same line, then
     wrap the expression in parentheses before placing each operand on its own
     line, **indented one level**. The operator should begin the new line.
  3. If an expression with the ternary operator `?:` cannot fit on the same
     line, then the `?` and `:` should begin the two new lines.
  4. Property access and method calls should always include the `.` on the new
     line.
  5. If all items in a comma-separated list cannot fit on the same line, then
     each item must be on its own line (with the comma directly after each item
     except the last), **indented one level**.
  6. When an opening curly brace follows a line-wrapped declaration or
     expression, it is on the same line as the final continuation line if that
     line is indented at the same level as the original line. Otherwise, the
     brace is placed on its own line.
  7. Recursively apply the above rules as needed.

#### Function Declarations

Follow the numbered steps below as needed:

```swift
@MyAnnotation  // (1) Put the top-level annotation on its own line.
func index<
    Elements,  // (4) Put each generic type on its own line.
    Element
>(
    of element: Element,  // (2) Put each parameter on its own line.
    in collection: Elements
) -> Elements.Index?
where
    Elements: Collection,  // (3) Put each generic type constraint on its own line.
    Elements.Element == Element,
    Element: Equatable
{
    …
}
```

#### Type and Extension Declarations

Follow the numbered steps below as needed:

```swift
@MyAnnotation  // (1) Put the top-level annotation on its own line.
class MyType<
    Elements,  // (4) Put each generic type on its own line.
    Element
>:
    MySuperclass,  // (2) Put the superclass and protocols on their own lines.
    MyProtocols
) -> Elements.Index?
where
    Elements: Collection,  // (3) Put each generic type constraint on its own line.
    Elements.Element == Element,
    Element: Equatable
{
    …
}
```

### Blank Lines

A single blank line also appears in the following locations:

  * Between parts of code with distinct purposes within the body of a control
    flow block, function, computed property, or observed stored property.
  * Before the first member of a type (*mandatory* if the member has a
    documentation comment, and *optional* if it does not).

Do not put a blank line as the first line in the body of a function. If the
start of the implementation is logically separate from the declaration, rethink
your naming!

### Parentheses

  * Do **NOT** wrap the entire condition of a control flow block in parentheses.
    If the line it is on does not fit, then follow rule 2 in
    [Line Wrapping](#line-wrapping).
  * Function calls/signatures have no space in between the function name and the
    parentheses.
  * Always wrap the parameters of a closure in parentheses.
  * Always group similar logical conditions with parentheses.
  * If the condition in the ternary operation `?:` uses a binary operator, then
    wrap it in parentheses.

```swift
// 🙂 CORRECT
if conditionIsTrue {
    …
}

// 😡 WRONG
if (conditionIsTrue) {
    …
}
```

```swift
// 🙂 CORRECT
let closure = { (parameters) in
    …
}

// 😡 WRONG
let closure = { parameters in
    …
}
```

```swift
// 🙂 CORRECT
let result = (score > 90) ? "Pass" : "Fail"

// 😡 WRONG
let result = score > 90 ? "Pass" : "Fail"
```

```swift
let value = (
    (someValue + otherValue + anotherValue - adjustmentValue)
    / partCount
)

if (conditionIsTrue && relatedConditionIsTrue) || separateConditionIsTrue {
    …
}
```

### Comments

  * Only documentation, `MARK:`, `TODO:`, and `FIXME:` comments are allowed.
  * Documentation comments should conform to Apple’s official
    [API design guidelines](https://swift.org/documentation/api-design-guidelines).

Naming
------

  * Use `UpperCamelCase` for type names. All other naming is in
    `lowerCamelCase`.
  * Always give constants, variables, functions, types, et al. meaningful names
    based on their contexts. Use context to communicate your code’s intention
    more effectively.
  * Naming should conform to Apple’s official
    [API design guidelines](https://swift.org/documentation/api-design-guidelines).
