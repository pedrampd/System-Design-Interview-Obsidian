Failure detection in more complex system is a vital task. We need to ensure if and when one or some of our servers are down. In practice, we can not say that a server is down because a single server says so. So how do we detect system failures?

**Naive Approach** :
We can connect all our servers to each other. this is inefficient obviously.

We can use [[Gossip Protocol]] to detect when one of our servers is down.

After detecting that a node is down, we should then proceed to somehow handle this situation.

To deal with this problem we use [[Sloppy Quorum]]. (This is when a server is **temporarily** down)

When a server is permanently down, we use [[Merkel Trees]] or [[Hash Trees]] to ensure data synchronization. 