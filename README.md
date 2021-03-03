# Getting Started with Php and Redis

In order to use Redis with PHP you will need a PHP Redis client. In the following sections, we will demonstrate the use of PhpRedis, a flexible and feature-complete Redis client library for PHP. Additional PHP clients for Redis can be found under the PHP section of the Redis Clients page



## Clone the repository


```
git clone https://github.com/redis-developer/redis-php-getting-started
```

# Installing PhpRedis

## On Linux System

PhpRedis’ installation instructions are given in its INSTALL.markdown file. The recommended method for installing PhpRedis is to use pecl.

### Get pecl:

```
apt install pkg-php-tools
```

## Install PhpRedis:

```
pecl install redis
```

You can also download the latest PhpRedis release from the GitHub repository.

## Opening a Connection to Redis Using PhpRredis

The following code creates a connection to Redis using PhpRredis:

```
<?php
 
$redis = new Redis();
//Connecting to Redis
$redis->connect('hostname', port);
$redis->auth('password');
 
if ($redis->ping()) {
        echo "PONGn";
}
 
?>
```

To adapt this example to your code, make sure that you replace the following values with those of your database:

In line 5,
hostname, port

should refer to your database’s hostname or IP address and your database’s port 

In line 6,
password

should be your database’s password

## Using OSS Cluster API with PhpRedis

The above example can be modified to support working with OSS Cluster API

```
$redis = new RedisCluster(NULL, Array("host:port", "host:port", 
"host:port"), 2, 1.5, true, "password");
```

Where

host:port
should be your database’s endpoint details 

2, 1.5
defines the read/write timeout 

true
defines using persistent connection to each node in the cluster 

password
should be your database’s password

## Reading and Writing Data with PhpRedis

Once connected to Redis, you can start reading and writing data. The following code snippet writes the value

```
bar
```

to the Redis key 

```
foo
```

reads it back, and prints it:

```
// open a connection to Redis
...
 
$redis->set("foo", "bar");
var_dump($redis->get("foo"));
The output of the above code should be:
```

```
$ php foo.php
PONG
string(3) "bar"
```
