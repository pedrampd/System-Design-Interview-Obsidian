The URL frontier is an important component in the [[Web Crawler]] to ensure [[politeness]], [[Prioritization]] and [[Freshness]].

This is the high level view of the URL frontier:
### High Level View
![[URL frontier.JPG]]

### URL Frontier Workflow:
- When a URL is inserted into our URL frontier we give it a priority base on PageRank, website traffic, update frequency, etc.
- Multiple queues are created, each representing a priority and URLs are added to them accordingly.
- Front queue selector selects N URLs randomly with a bias toward higher priority URLs from all of the queues.
- These URLs are sent to the back queue router which checks every URL's host and map them to their relevant queues. ( b1, b2, ..., bn each have a different host)
- To ensure [[politeness]] we only select a single URL from each queue
- The selected URLs are sent to some worker threads to crawl. To ensure we don't exhaust a server ( worker thread) we could use [[Consistent Hashing]] to distribute URLs to servers
### Storage:
The majority of URLs are stored on disk, so the storage space is not a problem. To reduce the cost of reading from the disk and writing to the disk, we maintain buffers in memory for enqueue/dequeue operations. Data in the buffer is periodically written to the disk.