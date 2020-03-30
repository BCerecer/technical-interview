# SYSTEMS DESIGN CHEATSHEET
***
### Distributed System 
- **Vertical** scaling refers to adding resources to a single machine
    - Examples: Buying more RAM, or higher CPU
- **Horizontal** scaling refers to adding more machines
#### Horizontal is preferred
##### Pros:
- **Fault Tolerant:** There is not a single point of failure
- **Low latency:** You can have nodes located in different regions over the world that can decrease the amount of time it takes to get to your service from certain areas of the world
- There is going to be a point where it is cheaper

***
### Distributed Datastores

The way distributed datastores work is by having a cluster of nodes(databases), where each node have a **primary responsibility** of storing some kind of unique data and a **secondary reponsibility** of storing a part of the data of another node. The way this is done is by having a hashing stating which node is the corresponding of backing up which part of the data of other node. The reason to backup a part of the data is to increase the **fault tolerant** capabilities of our system design since in the case of a region of multiple nodes going down, in most cases we will have parts or ideally all of the backup saved on other nodes.

#### CAP Theorem:
- **Consistency:** The read value return from the database is always the latest write value
- **Availability:** The application is always available to write/read even if we take down any db node
- **Partition tolerant:** The application must be working even if we take out the connection between db nodes

Basically, you can only pick two. For highly available applications that need to be up all the time, the best choice would be **availability** and **partition**, and having a **eventually consistent** data. This means, that the data may have some buffering time to synchronize. 

##### RDBMS: 
ACID: 

##### NoSQL:
BASE: Basically Available Soft Estate Eventually Consistent

***
### Distributed Locks

A **lock** allows only one thread to enter the part that's locked and the lock is not shared with any other processes.

A **mutex** is the same as a lock but it can be system wide (shared by multiple processes).

A **semaphore** does the same as a mutex but allows x number of threads to enter, this can be used for example to limit the number of cpu, io or ram intensive tasks running at the same time.

There are times when using distributed systems that multiple nodes want to access the **same resource**, which can be dangerous since they both can modified it without wanting this as the expected behavior. To handle this scenarios we need a **lock manager**, which administers which node can access to which resource. 

In a distributed design, it is optimal to have **distrbuted locks**. 

#### Distributed Locks Properties:

- **Fault tolerance:** To avoid single points of failure, we need to have multiple nodes replicating the information of current locked resources to which nodes. 
*The problem that originates with this is that if we replicate the information and the main node having the lock manager approver goes down, we end up without knowing what lock information is true*
- **Truthfulness:** To achieve multiple points of truth, all the nodes that we use to replicate information need to become **lock managers** and the way we verified that the lock manager approve a resource to some node is by adding **multiple lock manager approvals** a commonly number use for this is **n/2 + 1**, which says that as long as half of the lock managers approve it, the resource is assigned to that node. 

**Example:** Suppose we have a distributed system that is in charge of bank transactions. The way the transactions are made is by using **ditributed locks** to ensure that two transactions involving withdrawals from the same account at exactly the same time to make a payment to another account are synchronous and the withdrawal account gets charged correctly.



