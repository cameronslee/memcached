# Hack of Memcached: Implement MULT
Got the idea from [this article](https://quuxplusone.github.io/blog/2022/01/06/memcached-interview/) to implement a 'MULT' function 
as a fun lil challange

Became a better grepper bc this code base is gigantic and also LLDB is [schway](https://www.quora.com/What-does-Nora-mean-in-The-Flash-when-she-says-schway#:~:text=The%20word%20“Schway”%20is%20a,a%20substitute%20for%20those%20words.)

Works just like incr and decr, no slab test stats implemented though (out of scope)

```
// Usage
>> set age 0 3600 2
>> 20
STORED
>> mult age 2
40
```


# Memcached

Memcached is a high performance multithreaded event-based key/value cache
store intended to be used in a distributed system.

See: https://memcached.org/about

A fun story explaining usage: https://memcached.org/tutorial

If you're having trouble, try the wiki: https://memcached.org/wiki

If you're trying to troubleshoot odd behavior or timeouts, see:
https://memcached.org/timeouts

https://memcached.org/ is a good resource in general. Please use the mailing
list to ask questions, github issues aren't seen by everyone!

## Dependencies

* libevent - https://www.monkey.org/~provos/libevent/ (libevent-dev)
* libseccomp (optional, experimental, linux) - enables process restrictions for
  better security. Tested only on x86-64 architectures.
* openssl (optional) - enables TLS support. need relatively up to date
  version. pkg-config is needed to find openssl dependencies (such as -lz).

## Environment

Be warned that the -k (mlockall) option to memcached might be
dangerous when using a large cache. Just make sure the memcached machines
don't swap.  memcached does non-blocking network I/O, but not disk.  (it
should never go to disk, or you've lost the whole point of it)

## Build status

See https://build.memcached.org/ for multi-platform regression testing status.

## Bug reports

Feel free to use the issue tracker on github.

**If you are reporting a security bug** please contact a maintainer privately.
We follow responsible disclosure: we handle reports privately, prepare a
patch, allow notifications to vendor lists. Then we push a fix release and your
bug can be posted publicly with credit in our release notes and commit
history.

## Website

* https://www.memcached.org

## Contributing

See https://github.com/memcached/memcached/wiki/DevelopmentRepos
