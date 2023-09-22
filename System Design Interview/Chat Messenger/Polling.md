When a client wants to know the status of something for example if they have a pending message, is their download ready etc, they send http requests to the server to get the new desired status.

If the servers returns a negative response (result is not ready) the client sends another request after an interval.