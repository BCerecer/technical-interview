# Instagram

## Summary
![overview](../img/instagram-detail.png)

## Requirements
- **Features**
  - ***Upload/view*** photos
  - ***Search*** photo/video titles
  - User can ***follow*** other users
  - ***Newsfeed/Timeline***

- **Good Practice**
  - ***Highly available***
  - ***Low latency*** for timeline generation
  - ***Eventual consistency*** 
  - ***Highly reliable***

## Estimations
- **Assumption**
  - ***1M*** daily users
  - ***Read-heavy***
  - ***2M*** photos uploaded per day. ***23*** new photos every second.
  - Avg photo is ***200KB***

- **Storage estimates**
  - Total space required for 1 day of photos
  `2M * 200KB` = **400 GB** of storage per day

## Databases
- **Schema**
  - **User**
    Column | Type
    ---- | ----
    `user_id` | varchar(20) Key
    `name` | varchar(20)
    `email` | varchar(32)
    `creation_date` | datetime
    `last_login` | datetime
  - **Photo**
    Column | Type
    ---- | ----
    `photo_id` | varchar(20) Key
    `user_id` | varchar(32)
    `photo_latitude` | int
    `photo_longitude` | int
    `user_latitude` | int
    `user_longitude` | int
    `creation_date` | datetime
  - **Followers**
    Column | Type
    ---- | ----
    `users_id[]` | varchar[](16)

- **Database**
  - Store photos in distributed ***file storage*** like S3 or HDFS. 
  - Store the above schema in a distributed key-value store to enjoy the benefits offered by ***NoSQL***.
  - ***Metadata*** related to photos can go to a table where the ‘key’ would be the ‘PhotoID’ and the ‘value’ would be an object containing PhotoLocation, UserLocation, CreationTimestamp, etc.
  - Use ***Cassandra*** to store relationships between users and photos, to know who owns which photo. Also to store the list of people a user follows. 

## System Design
Photo ***uploads*** can be slow as they have to go to the database, whereas ***reads*** will be faster, especially if they are being served from cache. Have separate servers for ***read*** and ***write*** to avoid bottlenecks.

![overview](../img/instagram-detail.png)

## Reliability and redundancy
Multiple replicas of the system are needed to be ***highly reliable*** compliant. See picture above

## Newsfeed/Timeline
***Preprocess*** newsfeed of people we are following by doing a push to our timeline everytime they post something. For celebrities, since they have a lot of users, we pull the data from their posts. Alternatively, we could be following a similary approach to push by limiting the followers by an x amount per minute to not overload the system (first approach is better)

## News Feed Creation with Sharded Data
- Since need to show latest photos on newsfeed, use the creation_date to order them.
- Can append timestamp to the photo_id for faster retrieval and that way we don't need to call the photo metadata

## Caching
- Use ***80-20 rule*** to cache 20% of popular photos that generate 80% of traffic. Can use Redis or Memcache to cache data and application servers befor hitting db
- Use ***LRU*** eviction policy to change cached photos
- Use CDN to locate server nearby worldwide users
