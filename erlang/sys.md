# sys

Very useful module for the logging of OTP Behavior information.

To turn the first two, pass them the process and `true`. To turn them off, do the same but pass `false`.

### `trace(process, is_active)`

Prints a log of messages sent/received by the process and its corresponding state.

### `log(process, is_active)`

Similar to the above but keeps the log in the process loop. Can be put in a file.

### `statistics(process, get)`

General statistics about the process: start time, messages sent/received, and reductions.

### `get_status(process)`

High level overview with statistics, running status, parent info, and state.

In Elixir, you can pass a tuple with a key of `:debug` and any function from above to a Behavior's `start_link` function to automatically call it.
