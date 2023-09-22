### Design Overview:
![[Chat system send flow.JPG]]
1. after the user connects to a server (after a service discovery sends them a valid server) the user connects to a chat server via [[Web Socket]] and posts a message. 
2. Then we generate an ID for this message using a [[UUID]] generator.
3. the chat server publishes this message to a message queue.
4. the message queue stores this message in a NoSQL database like [[Cassandra]]
5. if the user receiving the message is online(see [[Online Discovery]]) then we sends them the actual message if not we store the messages in a [[Push Notification]] server and after the user gets online we will deliver the message.
### Group Chats:
for group chats the design is similar, we simply publish the message we are sending to group member's message queues.