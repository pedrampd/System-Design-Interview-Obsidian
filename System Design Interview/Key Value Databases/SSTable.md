When storing data in a mem-cache we want to eventually flush in into the disk. When the mem-cache is an ordered binary balanced tree (usually red-black tree) we can iterate over the data and save the sorted data to disk. then we create a separate table with two keys: **Key** and **Offset**. this is basically an [[SSTable]]. So what are offset and key?

When we reach our maximum capacity in the mem-cache we want to flush the data (in order) to the disk(SSTable). we partition them virtually, for example if we have 10mb of data in the SSTable we partition them for every 10kb of data. Now that we have chunked our data, we will get the top key (keys are sorted) and the offset which is how much we should move(?) in the hard disk to get to the next partition. This meta-data enables us to **Search** very faster in SSTables.

This will create an issue, because overtime, we will flush many SStables onto our hard-disk and to search for a key in all those SSTables in a costly operation. On top of that we can not easily delete data in this **Immutable** data structure. 

To handle disk space and redundant data, we will periodically merge these SSTables together and put them on a lower level ( like a pyramid or a tree). This will get rid of the duplicate and old values and will keep the SStable property.

To handle search, We will store a meta data for each SSTable which will tell us the min and max value of the keys contained in each level.

To handle a search for a missing key( because it consumes a lot of I/O) we use a [[bloom filter]] to tell us if a key doesn't exist in a block with O(1) time.

[[Cassandra]] uses SStables.

![[LSM tree.jpg]]