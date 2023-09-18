This is one of the [[Approaches for designing an ID generator]], in this design. we will simply increment the id by the number of our servers instead of 1.

**Pros** :
- easy to use
**Cons**:
- Hard to scale
- Hard to synchronize across multiple datacenters
- Issues when adding or removing a server