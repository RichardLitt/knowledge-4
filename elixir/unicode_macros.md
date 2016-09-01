# How Elixir handles Unicode so well

Elixir has awesome Unicode support. The way the team achieves this is through a clever use of macros.

All the Unicode character information is stored in [a text file](https://github.com/elixir-lang/elixir/blob/e1a1065/lib/elixir/unicode/UnicodeData.txt).

Elixir parses this text file and *dynamically* creates functions that match each Unicode character. These functions add transformations to the characters based on the parsed file's contents.

For example, this is the code generated to transform Unicode to upper case:

```elixir
def upcase(string), do: do_upcase(string) |> IO.iodata_to_binary

defp do_upcase("é" <> rest) do
  :binary.bin_to_list("É") ++ do_upcase(rest)
end
```

Each Unicode character in the text file gets its own `do_upcase` function. The recursive call to `do_upcase(rest)` will pattern match on whatever character is next.

Essentially, Elixir builds up Unicode support by adding functions at compile time based on a text file that can easily be changed and extended any time.

That's pretty cool!
