# Structs

Structs are fancy maps with compile-time checks and default values.

```elixir
defmodule User do
  defstruct name: "Juan", job: "developer"
end
```

In this case, we have a struct called `User` with two default values.

```elixir
%User{}
# -> %User{job: "developer", name: "Juan"}
%User{name: "John"}
# -> %User{job: "developer", name: "John"}

# This will not compile
%User{age: 22}
```

You can also easily [update](http://elixir-lang.org/getting-started/structs.html#accessing-and-updating-structs) and modify structs.

## In APIs

Projects like Ecto and Plug have composable APIs in which you start with a simple struct and modify it with piping.

For example:

```elixir
conn
|> put_resp_content_type("text/plain")
|> send_resp(200, "Hello world")
```

One of these piped functions may look like this:

```elixir
def change_stuff(model, param) do
  %{model | stuff: param}
end
```

This makes it easy to hide a complex struct and provide a simple API!
