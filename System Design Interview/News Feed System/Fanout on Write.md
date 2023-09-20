When a user create a post this post is immediately written on each of their friend's post cache. 

### Pros:
- Because the news feed is pre-computed (on cache), it doesn't take much time to load.
- The news feed is generated in real time.

### Cons:
- For inactive users, we waste resources by pushing to their post cache.
- If a user has many followers, pushing a post to all of them takes a lot of resources and time. This is called the [[Hotkey Problem]]
-