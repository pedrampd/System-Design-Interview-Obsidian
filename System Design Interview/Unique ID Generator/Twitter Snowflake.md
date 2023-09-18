This is one of the [[Approaches for designing an ID generator]].
![[Snowflake.jpg]]

I guess the only vague part is the sequence number and maybe the timestamp.

- **Time Stamp**:
	We will measure a time stamp from a specific date (twitter uses November 10 2010 or something).
	We can also sort our ids based on their timestamp.
- **Sequence Number**:
	This is an auto increment field, so when a data is added this number will be incremented. Note that this number is reset to 0 every milliseconds or so (because we have timestamp to handle unique data for every milliseconds)
	
This approach is considered best practice.