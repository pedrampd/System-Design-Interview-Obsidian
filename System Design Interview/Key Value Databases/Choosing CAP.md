When choosing [[CAP theorem]], It's said that CA is impossible due to the eventual network problems.

we can either choose **CP** or or **AP**.

AP ensures that the system is available even though the data you are getting when you request something may be inaccurate or stale(old).

CP ensures that the data you're getting is valid and in sync with the system. But when a network error occurs the system stops all transaction till it is resolved. ( Bank systems usually use CP)