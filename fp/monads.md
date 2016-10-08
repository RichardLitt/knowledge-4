# Monads

Functors apply a function to a wrapped value. Applicatives apply a wrapped function to a wrapped value. Monads apply a function that **returns a wrapped** value to a wrapped value.

Monads expose a function called `bind` (`>>=` in Haskell, `chain` in some JavaScript libraries) that does this.

Assume we have this function:

```haskell
half x = if even x then Just (x `div` 2) else Nothing
```

`bind` takes a Monad (like `Just 3`) and a function that returns a Monad (like `half`). It returns a Monad.

So:

```haskell
Just 20 >>= half
-- Just 10

Just 21 >>= half
-- Nothing
```

`bind` unwraps the value 20 and passes it to `half` which returns a wrapped value based on the value given.

Of course, there's more to Monads than just this! I'll keep adding stuff about them as I learn.
