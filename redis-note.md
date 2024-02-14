## Redis
[Course Link](https://www.youtube.com/watch?v=8sHCdz_tOjk&list=PL4cUxeGkcC9h3V2eqhi8rRdIDJshP-b4P)
- Redis Database
  1. in-memory data store
  2. use key-values structures
  3. uesd as a cashing layer
  4. Data store in RAM(very fast)
  - note - data might be lost as server crashing  
- Thanks to progresss, redis can be used as primary database for some features:
  1. Data persistance and replication to make data durable
  2. JSON support
  3. Search
  4. Tools: Redis OM - object mapping
  5. redis cloud  
  ~aboves are redis core~
  6. Tools: Redis stack
- Redis data types
  1. key - value pairs
  2. data type for value can be:
    - string 'Mario'
    - sets {'mario', 'luigi', 'peach'} - unsorted collections and unique
    - sorted sets {
        'mario': 1,
        'luigi': 2,
        'peach': 3,
      }
    - hashes {
        title: 'Final Empire',
        author: 'Brandon Sanderson'
      }
    - lists {'mario', 'luigi'} - not unique
  3. data type for key can be:
    - key is hashed
- How to install? [Here](https://redis.io/docs/install/install-stack/)
- [redis insight](https://redis.com/redis-enterprise/redis-insight/) - GUI tool
- String: 
  - ```SET name Mario // name - key; Mario - string value```
  - ```SET name2 "Chun Li"```
  - ```GET name```
  - ```DEL name2```
  - ```MSET name2 Yoshi color green rating 10```
  - ```MGET name name2 rating```
  - ```GETRANGE name 0 3 // "mari" ```
  - ```GETRANGE name -3 -1 // "rio" ```
  - ```SETRANGE name 2 abc // "maabc" ```
  - ```INCR rating // 11```
  - ```DECR rating // 10```
  - ```INCRBY rating 5 // 15```
  - ```SET name yoshi EX 10 // expired in 7 seconds```
  - ```SET name Yoshi NX // Only set the key if it does not already exist ```
  - ```SET name Yoshi XX // Only set the key if it already exists ```
  - ```SET name Toad GET // return prev value Yoshi ```
- [Redis Command](https://redis.io/commands/ "Link here") 

- Sets:
  - ```SADD names mario```
  - ```SADD names yoshi peach```
  - ```SREM names yoshi // remove yoshi ```
  - ```SADD moreNames link zelda```
  - ```SUNION names moreNames```
  - ```SISMEMBER names link // 0 for not found; 1 for found```
- Lists:
  - ```LPUSH orders ryu```
  - ```LPUSH orders chun-li // index 0 - chun-li and index 1 - ryu; push from left```
  - ```RPUSH orders blanka ken // push from right ```
  - ```LPUSH orders sagat balrog```
  - ```Lpop orders 1 // balrog```
  - ```RPOP orders 2 // ken blanka```
  - ```LLEN orders // 3```
  - ```LRANGE orders 0 1```
  - ```LINDEX orders 1```
  - ```LPOS orders ryu // 2```
- Hashes
  - can't store "multiple types" and no "nested properties"
  - ```HSET books:1 title "Name of the wind"```
  - ```HSET books:1 author "Patric Rothfuss"```
  - ```HSET books:1 rating 9```
  - ```HSET books:1 rating 10 // overwrite ```
  - ```HSET books:2 title "A wise man'fear" author "Patric rothfuss" rating 8```
  - ```HGET books:1 title```
  - ```HGETALL books:2```
  - ```HEXISTS books:1 title```
  - ```HKEYS books:2```
  - ```HVALS books:2```
  - ```HEDL books:1 author```
  - ```DEL books:1```
- Sorted Sets
  - ```ZADD books 7 "the name of the wind" 2 "the wise man's fear" 9 "the final empire" ```
- [Node-Redis Client library](https://github.com/redis/node-redis "Link here")
  1. ```npm install redis```
  2. 1. copy connection syntax from redis
     2. create ```.env.local``` file in src folder  
        fetch by ```process.env.${var}```
- Redis Stack
  - JSON support - Redis OM
  - RediSearch
    - create secondary indexes
    - easily perform search queries
  - ~~~ redis
    JSON.SET authors:1 $ '{
      "name": "brandon sanderson",
      "age": 55,
      "books": [
        {
          "title": "the final empire",
          "rating": 10
        },
        {
          "title": "the way fo kings",
          "rating": 9
        },
      ]}'
    ~~~
  - ```JSON.GET authors:1```
  - ```JSON.GET authors:1 $.name```
  - ```JSON.GET authors:1 $.books[0].title```
  - ```JSON.SET authors:1 $.books[0].rating 7```

