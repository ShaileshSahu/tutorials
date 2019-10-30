Redis tutorial 

-- Basically redis is open source key value in memory db which is extremely fast 
comparison to other dbs. Reason is because developed on C language and used cache memory due
to this it's extremely fast and accessible.
 
 Point to remember :-
    1) Extremely fast - 110000 SET's per seconds and 81000 GET's per seconds.
    2) support rich data type - SET, HASHMAP, LIST, SORTED SET due to this makes complex theory are quite faster.
    3) operation are atomic - All redis operation are atomic, which ensures that if two client s concurrently access Redis
    server will receive the updated value.
    4) Web application session,pub sub , page hit count etc.
    
Redis configuration
command:
    config set CONFIG_COMMAND_NAME 'shailesh'
    config get * (provide all the configuration of that redis) otherwise we can provide specific instead of astrick(*)
    
Redis data type
There are basically 5 data type & structure could say:

1) String: 
     they are binary safe and store upto 512 mb.
     COMMANDS: 
      a) set your_key_name your_key_value
         for eg: set name 'shailesh'
      b) get your_key_name
         for eg: get name
  
2) Hash:
 Basically hash is an object which store value as key-value pair and one hash can store upto 4B of the
 key value pair in it
   COMMANDS:
    a) HMSET your_hash_key key1 value1 key2 value2 .... so on.
       for eg: HSET user name 'shailesh' year '23' gender 'male'
    b) HGETALL your_hash_key
        for eg: HGETALL user

3) LIST: 
 This is list which stored the value insertion sort order and duplicate are allowed and in 
 one list we can store upto 3B values.
   COMMANDS: 
    a) lpush your_list_name value
        for eg: lpush cars 'santro'
    b) lrange yout_list_name 0 10
       for eg: lpush cars 0 10

4) SET:
    Set doesn't allows duplicate values and unordered and store upto 4B.
    COMMANDS:
        a) sadd your_set_name value
        for eg: sadd books java
        b) smembers your_set_name 
        for eg: smember books
 
5) SORTED SET: 
    sorted set is similar to set but only difference is that they are arranged into the 
    score value from low to high they are arranged.
    COMMANDS: 
        a) zadd your_set_name order_number value
        for eg: zadd countries 1 India
        b) zrangebyscore your_set_name low high
        for eg: zrangebyscore countries 0 100
         
Redis remote connection:
    redis-cli -h host -p port -a password
    ## Connect the remote server or localhost also
 
Redis key management
    key commands used to manage the redis keys and their life cycle
    integer(1) - means that key exist or deleted 
    integer (0) - means that key doesn't exist !!
    
    a) del key :
        this key used to delete the particular key
        COMMANDS:
            del your_key_name
            for eg:
             del java
       
    b) exists key:
        this key used to check wether the exist or not
        integer(1) : exists
        integer(0) : Not exists
        COMMANDS:
         exists your_key_name
         for eg:
            exists java
   
    c) expire key:
        this key used to expire the particular key at specified about time(second)
        integer(1) : set
        integer(0): not exist the key
        COMMANDS:
            expire your_key_name time_seconds
            for eg:
                expire java 60
                
     d) expireat key:
          this key used to expired the particular key at specified timestamp(unix format)
          integer(1) : set
          integer(0) : not exist the key
          COMMANDS:
            expireat your_key_name timestamp_unixformat
            for eg:
                expireat java 19203203000
     
     e) pexpire key:
           this key used to expired the particular key at specidied time(millisecond)
           integer(1): set
           integer(0): not set
           COMMANDS:
            pexpire your_key_name time_millis
            for eg:
                pexpire java 5000
      
     f) keys key:
            this is pattern key used to find the key in the redis
            COMMANDS:
                keys your_key_name* or keys * 
                for eg: 
                    keys ja*
               
     g) persist key:
            this key used remove the expire time from the particular key
            COMMANDS:
                persist your_key_name
                for eg:
                    persist java
     
     h) pttl key: 
            this key gives the remaining time in millis.
            COMMANDS:
                pttl your_key_name
                for eg:
                    pttl java                    
            
     i) ttl key:
            this key gives the remaining time in seconds.
            integer(-1) : persist
            integer(0): not exist
            COMMANDS:
                ttl your_key_name
                for eg:
                    ttl java 
     
     j) type key:
          this key used to get the type of the particular key data type
          COMMANDS:
            type your_key_name
            
     k) rename key:
          this key used to rename the existing to new particular key
          COMMANDS:
            rename existing_key new_key
            