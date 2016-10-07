# Applicatives

An Applicative is a Functor, so it wraps values in a context. However, Applicatives also wrap functions.

Applicatives unwrap both the function and value given, apply the function to the value, and wrap the result back.

```haskell
Just (+3) <*> Just 2
-- Just 5
```

A more involved example:

```haskell
(*) <$> Just 5 <*> Just 3
-- Just 15
```

`(*) <$> Just 5` returns something like `Just (*5)`, which we can apply to `Just 3` through `<*>`.

This means that we can take any function that expects any number of unwrapped values, pass it all wrapped values, and get a wrapped value back.
