# CAP Theorem

The CAP Theorem describes three properties:

* Consistency: All nodes see the same data at the same time
* Availability: Node failures don't prevent survivors from operating
* Partition tolerance: System continues to operate despite message loss due to network and/or node failure

Of these three, only two can be satisfied simultaneously. That means we can have "CA" or "CP" systems, for example. These have predictable properties:

## CA system

A CA system doesn't know the difference between between node and network failures. This means it has to stop accepting writes to avoid divergence (many copies of data). Because the system can't tell if a node or the network is down, the safest thing to do is to just stop accepting writes.

## CP system

A CP system prevents divergence by forcing "asymmetric" behavior on partitions. CP systems only keep the majority partition. This ensures data consistency and retains a degree of availability.

## Consistency

There's a tension between "strong" consistency and high availability during network partitions. Note that strong consistency isn't the only kind of consistency. We can work around our problems by weakening our consistency needs.

There's also a tension between consistency and performance. Strong consistency requires that nodes communicate and agree on every operation. This can mean high latency.

Choosing an appropriate consistency model can make our life easier. For example, a web service's data centers might lose connection with each other. A user should still be able to log in and use the service—the data can be reconciled later.

Consistency isn't a singular property: ACID != CAP != Oatmeal. A consistency model is just any kind of guarantee that the contents of a data stores will be predictable. It can be as strong or as weak as needed.
