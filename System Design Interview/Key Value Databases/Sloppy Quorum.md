Unlike [[Strong consistency]], in sloppy quorum we ignore a server which status is down on our hash table.

The procedure is :
When our coordinator wants to distribute the data between our [[virtual nodes]], if a node status is down we ignore the node and send the request/data to the next node so we can have our W,R values and get the consistency we want (or availability, depends on the value of W and R).

When the down server eventually becomes online we use [[Hinted Handoff]] to sync the data.
