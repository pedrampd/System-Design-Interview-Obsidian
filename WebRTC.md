Stands for Web Real Time Communication. WebRTC is a peer to peer connection for low latency media streaming.

### Overview:
When two clients wants to connect. Client 1 sends a request to a signaling server and the server sends the data to the client 2 and send them a feedback to let them know about each other. Then they will connect !

### More detailed overview:
Client 1 sends an offer object which contains an SDP [[Session Description Protocol]] which contains media configuration of this client. The signaling server offers this SDP to client 2, if accepted, client 2 will store this SDP in its memory and Will send another SDP back to the signaling server. The signaling server sends this SDP back to the client 1. Now these clients know about each other.
The signaling server provides some [[ICE candidate]] (basically how to connect to the other server which port and stuff) to both clients. Using all these information these two clients then will connect peer-to-peer.