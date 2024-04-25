**Atomicity:** All queries in a transaction must succeed. If one fails, all should rollback.

**Consistency:** The database must be consistent before and after the transaction. The goal is to ensure that the database before and after the transaction be consistent. If a transaction leaves data in an invalid state, the transaction is aborted and an error is reported.

The data that is saved in the database must always be valid (the data will be valid according to defined rules, including any constraints, cascades, and triggers that have been applied on the database), this way the corruption of the database that can be caused by an illegal transaction is avoided.

if you have a column that does not allow negative numbers, and try to add or modify a record using a value lower than zero on this column, the transaction will fail.

**Isolation:** This property ensures the isolation of each transaction, ensuring that the transaction will not be changed by any other concurrent transaction.  It means that each transaction in progress will not be interfered by any other transaction until it is completed.the result should be the same as the result obtained if the transactions were running sequentially.

A transaction occurs independently without any interference. Any changes that occur in any particular transaction would NOT be ever visible to the other transactions unless and until this particular change in this transaction has been committed or written to the memory.

For example, if two clients are trying to buy at the same time the last available product on the web site, when the first user finishes the shopping, it will make the transaction of the other user be interrupted.

**Durability:** Successful transaction must be persisted in a durable non-volatile storage. The database’s durability should be such that even if the system fails or crashes, the database will survive. However, if the database is lost, the recovery manager is responsible for guaranteeing the database’s long-term viability. Every time we make a change, we must use the COMMIT command to commit the values.

