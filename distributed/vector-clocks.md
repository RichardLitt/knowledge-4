# Vector clocks

An extension of a Lamport clock. It maintains an array of N logical locks (one per node). Each node increments its own logical clock in the vector by one on each internal event. The rules are:

* When a process does work, increment the logical clock value in the vector corresponding to the process
* When a process sends a message, include the full vector of logical clocks
* When a message is received:
  * Update each element in the vector to be `max(local, received)`
  * Increment the logical clock value representing the current node in the vector

The problem is that since you are passing around a vector or array of values, it may grow too big in a large system.
