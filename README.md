# Cache

[![Latest Stable Version](https://poser.pugx.org/desarrolla2/cache/v/stable.png)](https://packagist.org/packages/desarrolla2/cache) [![Total Downloads](https://poser.pugx.org/desarrolla2/cache/downloads.png)](https://packagist.org/packages/desarrolla2/cache) [![Build Status](https://secure.travis-ci.org/desarrolla2/Cache.png)](http://travis-ci.org/desarrolla2/Cache)

A symple cache library. Implements different adapters that you can use and change 
easily by a manager or similar.


## Installation

### With Composer

It is best installed it through [packagist](http://packagist.org/packages/desarrolla2/cache) 
by including
`desarrolla2/cache` in your project composer.json require:

``` json
    "require": {
        // ...
        "desarrolla2/cache":  "dev-master"
    }
```

### Without Composer

You can also download it from [Github] (https://github.com/desarrolla2/Cache), 
but no autoloader is provided so you'll need to register it with your own PSR-0 
compatible autoloader.

## Usage


``` php
<?php

use Desarrolla2\Cache\Cache;
use Desarrolla2\Cache\Adapter\NotCache;

$cache = new Cache(new NotCache());

$cache->set('key', 'myKeyValue', 3600);

// later ...

echo $cache->get('key');

```

## Adapters

### NotCache

Use it if you will not implement any cache adapter is an adapter that will serve 
to fool the test environments.

### File

Use it if you will you have dont have other cache system available in your system
or if you like to do your code more portable.

``` php
<?php
    
use Desarrolla2\Cache\Cache;
use Desarrolla2\Cache\Adapter\File;

$cacheDir = '/tmp';
$adapter = new File($cacheDir);
$adapter->setOption('ttl', 3600);
$cache = new Cache($adapter);

```

### Apc

Use it if you will you have APC cache available in your system.

``` php
<?php
    
use Desarrolla2\Cache\Cache;
use Desarrolla2\Cache\Adapter\Apc;

$adapter = new Apc();
$adapter->setOption('ttl', 3600);
$cache = new Cache($adapter);

```

### Memory

This is the fastest cache type, since the elements are stored in memory. 
Cache Memory such is very volatile and is removed when the process terminates.
Also it is not shared between different processes.

Memory cache have a option "limit", that limit the max items in cache.

``` php
<?php
    
use Desarrolla2\Cache\Cache;
use Desarrolla2\Cache\Adapter\Memory;

$adapter = new Apc();
$adapter->setOption('ttl', 3600);
$adapter->setOption('limit', 200);
$cache = new Cache($adapter);

```

### Mongo

Use it if you will you have mongodb available in your system.

``` php
<?php
    
use Desarrolla2\Cache\Cache;
use Desarrolla2\Cache\Adapter\Mongo;

$server = 'mongodb://localhost:27017';
$adapter = new Mongo($server);
$adapter->setOption('ttl', 3600);
$cache = new Cache($adapter);

```

### MySQL

Use it if you will you have mysqlnd available in your system.

``` php
<?php

use Desarrolla2\Cache\Cache;
use Desarrolla2\Cache\Adapter\MySQL;

$adapter = new Cache(new MySQL('localhost', 'user', 'pass', 'port'));
$adapter->setOption('ttl', 3600);
$cache = new Cache($adapter);

```



## Coming soon

This library implements other adapters as soon as possible, feel free to send 
new adapters if you think it appropriate.

This can be a list of pending tasks.

* Cleanning cache
* MemcachedAdapter
* Other Adapters

## Contact

You can contact with me on [@desarrolla2](https://twitter.com/desarrolla2).

## Other

* [API docs](http://cache.desarrolla2.com/api/namespaces/Desarrolla2.html)
* [Code coverage](http://cache.desarrolla2.com/coverage/src_Desarrolla2_Cache_Adapter.dashboard.html)
* [Code dependencies](http://cache.desarrolla2.com/pdepend/dependencies.svg)
* [Code overview pyramid](http://cache.desarrolla2.com/pdepend/overview-pyramid.svg)
* [Coding standard report](http://cache.desarrolla2.com/phpcs/sumary.txt)
* [Coding standard report full](http://cache.desarrolla2.com/phpcs/full.txt)
* [Code mess report ](http://cache.desarrolla2.com/phpmd/report.txt)

