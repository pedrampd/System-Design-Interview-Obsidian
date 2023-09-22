The basic design of a chat system is
1. A client sends a message to a server 
2. The server sends the message to the receiver
while the sender could send their message via HTTP, it is more complicated on the receiver's side. because we can not send request from our server to the client(receiver).

We could use [[Polling]], [[Long Polling]] or [[Web Socket]] to handle this. in this design the preferred choice is the [[Web Socket]]

## High Level Design
![[Chat system.JPG]]


## Database and Data Models:
There are two types of data in our chat system, first the user data, settings. friends list ([[Graph DB]]) which we can store in a relational database.
Second, there are the actual messages. Since the data is quite large and also not relational in nature we could use a NoSQL like [[Cassandra]]. Our data model for a message could be something like this:
![[chat datamodel.JPG]]
![[group chat data model.JPG]]
To create an id for each message we cannot use an auto incremental id like in a traditional relational database but we could use a [[UUID]] generator like [[Twitter Snowflake]]


## Service Discovery and Message Delivery:
Since we have a lot of servers to connect to (many of them could be far away from the user with a high ping) we could use a service discovery like [[Zookeeper]] to select a server and return it to the sender(client) and then the client connect to that server via [[Web Socket]]

For detailed view of the message delivery system see [[Chat System message delivery]]
## Reading The Message :
The receiver simply pulls the message from their message queue.


## Further improvement:
- Use a blob database ([[Amazon S3]]) to store media content (videos, images) and also store thumbnails 
- Use [[end-to-end message encryption]] 
- database Read Replicas
-