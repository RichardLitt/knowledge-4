# Lamport clocks

A replacement for physical clocks for multiple processes.

Each process maintains a counter using the following rules:

* When a process does work, increment the counter
* When a process sends a message, include the counter
* When a message is received, set the counter to `max(localCounter, receivedCounter) + 1`

This clock allows counters to be compared across systems. If `timestamp(a) < timestamp(b)`:

* `a` may have happened before `b`
* `a` have be incomparable with `b`

Lamport clocks containing data from different systems that never communicate with each other cannot be correctly ordered, even if they appear to be. This is because Lamport clocks can only carry information about one timeline.
