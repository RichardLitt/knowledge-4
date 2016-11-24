# `mix test`

Elixir's test library is great and has a few interesting commands.

## `mix test --trace`

A verbose mode. Tells you how long each individual test took, for example.

## `mix test --stale`

Only runs the test that reference modules that changed. This is useful when you have a large, possibly slow test collection.

## `mix test --cover`

This will output coverage information.

## `mix test --include [filter]`, `--exclude [filter]`, `--only [filter]`

This will filter or add the tests that match the given `filter`. More information about filters [here](http://elixir-lang.org/docs/stable/mix/Mix.Tasks.Test.html#module-filters).

