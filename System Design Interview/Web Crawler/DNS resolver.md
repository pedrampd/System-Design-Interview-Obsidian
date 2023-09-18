The DNS resolver is a bottle neck for [[Web Crawler]]s because a DNS request might take between 10ms to 200ms. Once a DNS request is sent to the resolver, all other threads are **BLOCKED** till the request is resolved. We could solve this problem by implementing a caching system and storing the result of the DNS resolver.
Our DNS cache keeps the domain name to IP address mapping and is updated periodically by Cron jobs.