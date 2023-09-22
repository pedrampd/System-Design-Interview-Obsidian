Fanout is the process of delivering a user's post to all of the user's friends.

Two types of fanout models are [[Fanout on Write]] and [[Fanout on Read]] both of them have their own pros and cons. we could use a [[Hybrid approach to faning out]].

### High Level Design :
![[Fanout.png]]

1. The user firsts get their friend ids from a [[Graph DB]]
2. Then they get their friends data from their cache which is connected to a DB, This data may include which friends the user wants to include on their content and stuff.(mute hide close friend)
3. We put the <friends_id, post_id> in a message que
4. Some fanout workers will pull messages from this message queue and insert them in the news feed cache