When a client sends a read request :
1. If the data is in the cache, return the data
2. If the data is not in the cache, check the [[bloom filter]]
3. the bloom filter finds the [[SSTable]] which contains the key
4. The [[SSTable]] then returns the value
5. The data is sent back to the client