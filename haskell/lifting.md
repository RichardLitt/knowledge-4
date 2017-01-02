# Lifting

What do we mean by lifting? We mean that we lift a function over some layer of structure to apply it:

```haskell
fmap (+ 1) $ Just 1 -- Just 2
fmap (+ 1) [1, 2, 3] -- [2, 3, 4]
```

In both cases, the function we’re lifing is the same. In the first case, we lift it over a Maybe context in order to apply it. In the second case, it's the list context.

The context we’ve lifted the function into determines how the function will get applied.
 