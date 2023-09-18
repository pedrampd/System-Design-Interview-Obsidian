When dealing with large data in key value databases, it is impossible to fit all those data in a single partition.

The thing we need to do is to partition the data in multiple nodes of our database(these nodes can be virtual nodes) .The best way to do that is to use [[Consistent Hashing]]

This way we can scale our system automatically whilst also increasing or decreasing the number of [[virtual nodes]] based on our server's capacity.