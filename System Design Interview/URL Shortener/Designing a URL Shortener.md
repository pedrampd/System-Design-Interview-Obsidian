Suppose we have to store more than 365 million URLs and their short versions. We can use , all English letters and numbers (62 characters). 
- We need at most 7 characters to store this data since 62 ^ 7 > 365 * 10^6.
after creating this short URL we need to store it in DB to look-up when a request is sent to our server or create one to use for later usage.

### Approaches
- **Hash function with collision resolution:
	We use some form of [[Uniform Hashing]] to hash the long URL and store it in our DB.
	However! Hash functions are usually more than 7 characters.  We can take the first 7 characters of the hash string, look it up in our DB, if the data exist, we will add a random or pre-defined string to the original long URL and repeat this process till there is no collision in our database.
	The look-up operation is quite costly, to avoid this  we can search the database using [[bloom filter]] 
-  **Base62-Encoding** :
	Since we only have 62 characters, we can change a URL to its base62 form. the characters in the base 62 are : 0=0, 1=1, ..., a=10, b=11, ..., Z=61. Just like all other base encodings we can convert base 62 encoded string back to its original form.
	In this way, the short URL that is generated is always unique and we don't need to resolve any conflicts in our database.
	However When we want to add a new URL pair to our DB we have to use a Unique ID Generator. ![[Approaches for designing an ID generator]]
### System Overview: 
When the user sends a POST request to our server, we use a [[Load Balancer]] to select which of our servers is going to handle the request. After that we check if the request is in our cache. If the request is not in our cache we check the DB ( using [[bloom filter]]) and if the request is not in the DB either we create a new URL, and a new ID insert it into our DB and possibly in our cache. And send back a [[301 Redirect]] or [[302 Redirect]] to the client

**We Could add a [[rate limiter]] to handle malicious requests to our servers** 

### Some Notes: 
- Our database is sharded and replicated  see : [[Data Replication]]
- we use some form of [[caching]] before looking up the DB
- since our servers are stateless we can scale them horizontally.


