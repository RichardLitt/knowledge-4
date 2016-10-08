# Pointfree

Pointfree refers to a style of composing functions without specifiying their arguments.

For example:

```haskell
-- Not pointfree
let x = negate . sum $ [1, 2, 3, 4, 5]
-- -15

-- Pointfree
let f = negate . sum
f [1, 2, 3, 4, 5]
-- -15
```
