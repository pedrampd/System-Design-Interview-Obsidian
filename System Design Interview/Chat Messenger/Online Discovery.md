To check the online status of a user we connect the client to a online discovery service( Presence Service) which checks their connection and store them in a NoSQL database ([[Cassandra]])

when the user logs out (after going through our logout api) the service discovery marks the user as offline and store this data in the database.

### Handling Internet connection issues:
When a user disconnects due to internet connection problems we could check build a service that checks the [[Web Socket]] connection and report back to the server when a client disconnects and then we mark them as offline. However, with this design we change the status of a  user whose internet connection is bad too frequently. This could result in a bad user experience. What we should do instead is to send a heartbeat from the user to our presence server every x seconds and store the timestamp. 
If we don't receive a heartbeat after an interval (for example 30 seconds) then we consider the user offline and update our database

After storing all these information, we need to somehow tell the user's friends that he is offline.
for detailed information, see:  [[Online Discovery Fanout]]