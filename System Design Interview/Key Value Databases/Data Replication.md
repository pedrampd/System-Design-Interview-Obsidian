To achieve high **availability** and **reliability** we need to replicate our data across multiple servers.

The way to do this is partially like [[Consistent Hashing]] where we first hash our data, put it on a hash ring and select the first N servers we come across.

Whilst choosing the first N server to store our data, we may encounter 2 or more virtual nodes representing the same server. To avoid this, we can select unique servers and ignore duplicate ones.

Why should we do this? Because usually when a server goes down the whole datacenter is down due to some natural disaster or power outage or etc. 