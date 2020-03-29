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