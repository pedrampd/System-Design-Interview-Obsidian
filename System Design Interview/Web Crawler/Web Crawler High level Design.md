![[Web crawler high level design.JPG]]

1. We need to first select one or some [[Seed URLs]] and add them into our [[URL Frontier]]
2.  Select some URLs from the [[URL Frontier]] and send them to HTML downloader
3. [[HTML Downloader]] sends these URLs to a [[DNS resolver]] and will download their contents
4. [[Content Parser]] is used to detect malicious content on the downloaded html.
5. Check if the [[Content is Seen]] and store/cache them in a database.
6. Extract other links from the parsed URL with [[Link Extractor]]
7. Filter out unwanted URLs
8. Check if the URL is seen before and store them in our DB, we could search the DB with a [[bloom filter]] and a cache (We could use a URL shortener service here maybe? see [[Designing a URL Shortener]])
9. Send back all the URLs that are not seen back to the [[URL Frontier]] and repeat this process from step 2.
