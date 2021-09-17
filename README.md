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
