When we want to check if we previously seen a content on the internet we first hash the HTML page and look it up in the database this look up method is time consuming so we use [[bloom filter]]
for this task.
The structure for detecting changes or differences between two web pages could be something similar to [[Merkel Trees]] maybe?