This is one of the [[Approaches for designing an ID generator]]. In this design we will simply generate a UUID for a given row of our database. we could even generate this UUID using only some of its columns. Each server is responsible for creating it's own UUID. so there is a id generator in every server.

**Pros**:
- easy to scale
- no coordination is needed between servers
**Cons**:
- 128 bit is quite large for an id
- The id could contain non numeric values