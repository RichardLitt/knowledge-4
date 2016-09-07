# Via tuples

A tuple in the form `{:via, module, alias}` that you can send to a `GenServer` to be used in `start_link`, `call`, or `cast`.

The `module` must export `register_name/2`, `unregister_name/1`, `whereis_name/1`, and `send/2` functions.

Basically, we tell Elixir we want a special module to handle our process registering. It requires the above four functions for its methods. Those methods can delegate to `GenServer` callbacks.

## Example

Let's say we have a module where this is sent via a `GenServer` call or cast:

```elixir
{:via, Todo.ProcessRegistry, {:database_worker, worker_pid}}
```

We can expect `Todo.ProcessRegistry` to have the four above functions, one of which may look like this:

```elixir
def register_name(key, pid) do
  GenServer.call(:process_registry, {:register_name, key, pid})
end
```

And, of course:

```elixir
def handle_call({:register_name, key, pid}, _, process_registry) do
  # Do stuff here
end
```

This way, we can have a standard protocol when registering processes on our own. Elixir will take care of registering processes for you as needed.
