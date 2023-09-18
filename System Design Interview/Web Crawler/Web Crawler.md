### Design Requirements :
- The web crawler needs to crawl 1 billion pages per month
- The web crawler should update its content
- The web crawler needs to store its data for 5 years
- Pages with duplicate inputs should be ignored

### [[Back of the Envelope Estimation]]: 
- QPS: 1 billion / 30 days /24 hours / 3600 seconds = 400 pages per second
- Peak QPS ~= 800 
- Assume the average HTML size is 500k
- we need to store 500k x 1 billion x 12 months =500TB x 12 = 60PB per year and 30 PB for 5 years

![[Web Crawler High level Design]]