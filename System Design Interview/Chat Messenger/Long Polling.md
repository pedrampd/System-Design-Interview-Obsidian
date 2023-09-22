Just like [[Polling]], but when the client sends a request to the server the server doesn't immediately respond. It waits for the result to be readied and then sends a respond to the client. 

We also set a timeout for this type of polling if the result is not ready for some time, we return a negative response to the client and then the client would try again after an interval has passed.