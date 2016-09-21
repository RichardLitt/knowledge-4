# Test tags

You can add tags to an ExUnit test to ask for more data or an action.

```elixir
@tag login_as: "juan"
test "do stuff" do
  # Test here
end
```

In `setup`:

```elixir
setup config do
  if username = config[:login_as] do
    # If we used the `login_as` tag in a test, this branch will be evaluated and
    # whatever was passed will be available
    
    # We can also pass stuff to the connection so it'll be available in test that use the tag
    user = insert_user(%{"username": username})
    conn = assign(conn, :current_user, user)
    {:ok, conn: conn, user: user}
  else
    # Do something else if we didn't use the tag
  end
end
```

Pretty cool!
