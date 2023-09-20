### High level Design
![[news feed publisher.png]]

### Flow Explanation:
1. The user sends a request from his mobile app or web app, to our [[Load Balancer]]
2. The [[Load Balancer]] decides which of our [[news feed servers]] will handle the request.
3. Then the request is distributed to [[News feed Post Service]] , [[Fanout Service]]. [[News Feed Notification Service]] 