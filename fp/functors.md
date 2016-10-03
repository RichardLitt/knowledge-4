# Functors

A functor is simply a type that holds a value and exposes a `fmap` (sometimes `map`) function that applies a function `f` to the value, returning a new functor with the result in it.

```haskell
fmap (+3) (Just 2)
-- Just 5
```

In Haskell, the infix version of `fmap` is `<$>`.
