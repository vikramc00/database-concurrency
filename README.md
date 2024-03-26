# Database Concurrency
Implemented concurrency for a database, based on multigranularity locking.

Database keeps track of transactions, tables, and indices and delegates work to its disk manager, buffer manager, lock manager and recovery manager.

## Design
Multigranularity locking is divided into 3 layers: 
- LockManager object: manages all the locks, treating each resource as independent
- A collection of LockContext objects: each represents a single lockable object that lies on top of the LockManager
- LockUtil: A declarative layer lies on top of the collection of LockContext objects, and is responsible for acquiring all the intent locks needed for each database request
