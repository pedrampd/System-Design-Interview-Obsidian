Assume that we have N servers and we want to monitor the status of all of our servers.

**Each Node** maintains a list of all other nodes and a heart-beat counter and the last time the heartbeat was updated.
(this data is shared between all nodes)

We start with one of our nodes, We send a heartbeat to some random other nodes.
When a node receives a heartbeat it then in return sends some heartbeats to other nodes in random and updates it heartbeat counter and timestamp.
when a node doesn't answer to a heartbeat the node sending the heartbeat will notify other servers (for example S0 sends a signal to S1 and S3 that S2 is down)
when some other servers also detect that a server is down we consider it down.

the "down" status is usually defined when a server has not updated its heartbeat after some time.

