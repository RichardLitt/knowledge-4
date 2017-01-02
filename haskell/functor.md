# Functor

```haskell
class Functor f where
  fmap :: (a -> b) -> f a -> f b
```

The typeclass `Functor` defines a function `fmap` that takes a function from `a` to `b`, a functor `a`, and returns a functor `b`.

Essentially, this applies the function to each element of the functor. Functor is a typeclass for function application "over", or "through", or "past" some structure `f` that we want to ignore and leave untouched.

## What about `f`?

`f` must have kind `* -> *`, awaiting application to a type constant of type `*`. This is because `f a` and `f b` must have `*` kind (each argument in a type signature must be fully applied).

## Functor laws

### Identity

```haskell
fmap id == id
```

### Composition

```haskell
fmap (f . g) == fmap f . fmap g
```

## Why does `fmap` only affect the second argument of a tuple and Either?

If we have:

```haskell
data Two a b = Two a b deriving (Eq, Show)
```

Something like this won't work:

```haskell
instance Functor (Two a) where
  fmap f (Two a b) = Two $ (f a) (f b)
```

Because the `a` is part of the functorial structure—the `f`. We're not supposed to do anything in the `f` referenced in the type of `fmap`. In `fmap :: Functor f => (a -> b) -> f a -> f b`, `f` is `(Two a)`.

We can only touch the second argument:

```haskell
instance Functor (Two a) where
  fmap f (Two a b) = Two a (f b)
```

Remember, Functor instances must have a `* -> *` kind!

For this reason, `fmap` works very well with `Maybe` and `Either`. In those two types, the first argument is an "error" value that doesn't need to be transformed.
