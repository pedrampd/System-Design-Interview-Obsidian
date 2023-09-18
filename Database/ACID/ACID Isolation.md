A part of [[ACID]] transaction properties. 

Shows how much a transaction is isolated from other transactions

There are 4 levels of isolation

1. [[Read Uncommitted]] : Basically no isolation whatsoever
2. [[Read Committed]]: Only reads committed changes (No [[Dirty Read]])
3. [[Read Repeatable]]:  The row the transaction is reading will remain unchanged
4. [[Snapshot/Serialized Transactions]]: the query will see a snapshot of the db
