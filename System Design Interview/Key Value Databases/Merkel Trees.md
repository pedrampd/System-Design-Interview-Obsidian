For each server node, we divide our database **keys** into some buckets of size k (for example a bucket would be {[1,2,3], [3,4,5] , [6,7,8]}) and construct a graph.

The buckets are our leaves, we hash the buckets using some form of [[Uniform Hashing]] and create a parent node. then we merge parent nodes two by two and hash them to construct our graph.

we can detect inconsistency in our data when the value of the root nodes differ in our servers.
we can then iterate over nodes which values are different easily and detect the exact bucket which values are not consistent across all our servers.

this way instead of loading all of our data and comparing them together we will only compare the different or missing data in our servers

Using Merkle trees, the amount of data needed to be synchronized is proportional to the differences between the two replicas, and not the amount of data they contain. In real-world systems, the bucket size is quite big. For instance, a possible configuration is one million buckets per one billion keys, so each bucket only contains 1000 keys.