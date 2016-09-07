# ETS

In-memory data structure that can store Erlang terms.

## Characteristics

* Identified by its ID or a global name (an atom)
* Mutable
* Concurrent writes and reads that support many processes
* Minimum isolation is ensured
* Deeply connected to its owner process (the process that created it), so it will terminate if the owner does

## Examples

```elixir
table = table = :ets.new(:my_table, [])

:ets.insert(table, {:key_1, 1})
:ets.insert(table, {:key_2, 2})
# Overwrites
:ets.insert(table, {:key_1, 3})

:ets.lookup(table, :key_2)
# -> [key_2: 2]
```

By default an ETS table is considered a `set`: one row per distinct key is allowed. There are other options such as `bag` (multiple rows with the same key allowed, but they can't be identical) or `ordered_set`, which orders rows in term order.

Tables also have access permisions. By default, only the owner can read or write. Other processes can only read.
