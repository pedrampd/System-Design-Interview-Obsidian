Since the data is stored on multiple nodes and replicas we need to ensure consistency. [[Quorum ]] consensus can guarantee consistency. 

First we define some terms:
**N**: number of replicas
**W**: number of  [[Quorum]] for a write request to be considered successful.
**R**: Number of [[Quorum]] for a read request to be considered successful

**Designing the algorithm**:
We create a form of coordinator that acts like a [[Proxy]]. every read or write request first goes through it and it distribute it across all or some of our nodes.
Note that W or R = 1 doesn't mean that our coordinator sends the data to one node. It means that it only needs to wait for a single ACK for a request to be considered alright.

**Some Typical W,R,N values**:
When choosing these values we are often choosing between latency and consistency.
W=1, R = N : ensures faster write requests and slower read
W= N, R=1: ensures faster read
W + R > N : ensures[[Strong consistency]] ( usually N=3 , W=R=2)
W + R < N : weak consistency
Weak consistency means that the client gets the data asap but subsequent read request may differ from each other.


It is recommended to use [[Eventual Consistency]] used by [[Cassandra]] to ensure that, given time, our data will eventually be consistent.