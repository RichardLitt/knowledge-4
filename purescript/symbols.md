# Cool PureScript symbols

Assuming `filter` takes in a function `isFinished` and operates on `book`.

## `$`

```purescript
head $ filter isFinished book
```

is the same as

```purescript
head (filter isFinished book)
```

## `<<<`

```purescript
(head <<< filter isFinished) book
```

is the same as

```purescript
head (filter isFinished book)
```

## `>>>`

```purescript
(filter isFinished >>> head) book
```

is the same as

```purescript
head (filter isFinished book)
```
