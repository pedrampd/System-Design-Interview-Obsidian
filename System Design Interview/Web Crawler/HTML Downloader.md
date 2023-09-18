An HTML downloader component for a [[Web Crawler]] system's core concepts are as follows :
- Performance Optimization 
	**Distributed Crawl** 
	- We load balance a crawl request to our HTML downloader and create multiple html downloader workers. 
	- The requests are distributed equally between them using a [[Consistent Hashing]] policy.
- DNS resolver![[DNS resolver]]
-  **Locality**
	We could move our servers closer to the locations we want to crawl to ensure better and faster connection and download more efficiently.
- **Request timeout**
	There might be traps or crashing websites or simply very time consuming requests on the internet, to solve this issue we set a maximum time for our crawl to be resolved or else be terminated.