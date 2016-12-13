# Maybe

```haskell
data Maybe a = Nothing | Just a
```

Used when values may or may not be there.

## Examples

```haskell
ifEvenAdd :: Integer -> Maybe Integer
ifEvenAdd n = if even n then Just (n + 2) else Nothing
```

```haskell
type Name = String
type Age = Integer

data Person = Person Name Age deriving Show

makePerson :: Name -> Age -> Person
makePerson name Age
  | name /= "" && age >= 0 = Just $ Person name age
  | otherwise = Nothing
```

`makePerson` is a "smart" constructor that returns a explicit signal when input is invalid.

For more detailed error reporting, see `Either`.
