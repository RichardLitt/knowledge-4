# `Data.Traversable`

A typeclass that represents structures that can be traversed from left to right.

Instances of `Traversable` must, among other things, expose a `traverse` function with type signature:

```haskell
traverse :: :: (Traversable t, Applicative f) => (a -> f b) -> t a -> f (t b)
```

All this means is that `traverse` takes in a function `f` that applies an action to each element of a structure from left to right.

If that sounds like `fmap` that's because it's very similar, but it also allows you to run effects while rebuilding the data structure.

## Examples

Let's say we have:

```haskell
data Tree a = Empty | Leaf a | Node (Tree a) a (Tree a)
```

The `Functor` interface is:

```haskell
instance Functor Tree where
  fmap f Empty        = Empty
  fmap f (Leaf x)     = Leaf (f x)
  fmap f (Node l k r) = Node (fmap f l) (f k) (fmap f r)
```

The `Traversable` interface is:

```haskell
instance Traversable Tree where
  traverse f Empty        = pure Empty
  traverse f (Leaf x)     = Leaf <$> f x
  traverse f (Node l k r) = Node <$> traverse f l <*> f k <*> traverse f r
```

Calling the constructors in Applicative style lets us have side effects while rebuilding the tree.

A simpler example from an exercise I did recently:

Assume we have the following:

```haskell
import qualified Data.Map as Map

-- Maps a DNA nucleotide to an RNA one (G becomes C) in a map
toRnaNucleotide = Map.fromList [('G','C'), ('C','G'), ('T','A'), ('A','U')]
```

Using `Map.lookup` we can query for a value in the map with a key. So `Map.lookup 'G'` returns `Just 'C'`. A nonexistent key returns `Nothing`.

To use it in `traverse`, we need to use `Map.lookup` in an infix (Applicative) style, taking the key in the left and the map in the right:

```haskell
-- Returns `Just 'G'`
'C' `Map.lookup` toRnaNucleotide
```

Now we can do:

```haskell
-- Returns "UGCACCAGAAUU"
traverse (`Map.lookup` toRnaNucleotide) "ACGTGGTCTTAA"
```

To convert any DNA strand to a RNA strand. Even better, `Map.lookup` will handle invalid values for us and return `Nothing`.
