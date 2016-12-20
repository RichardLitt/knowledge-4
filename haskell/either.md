# Either

```haskell
data Either a b = Left a | Right b
```

Useful to express *why* we didn't get a successful value after an error (as opposted to just `Nothing`).

## Examples

```haskell
type Name = String
type Age = Integer

data Person = Person Name Age deriving Show

data PersonInvalid = NameEmpty | AgeTooLow deriving (Eq, Show)

mkPerson :: Name -> Age -> Either PersonInvalid Person
mkPerson name age
  | name /= "" && age >= 0 = Right $ Person name age
  | name == "" = Left NameEmpty
  | otherwise = Left AgeTooLow
```

`mkPerson` now tells you what was wrong with your input in a `Left` type.
