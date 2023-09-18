![[Write path.jpg]]
(This is mainly based on how [[Cassandra]] works)
When the client sends a data the request is persisted on a commit log in disk. then the data will be cached the cache is usually a ordered binary balanced tree. when the cache reaches a limit it is flushed onto the disk into an [[SSTable]] (sorted string table)