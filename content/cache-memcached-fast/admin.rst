Administrator Interface
=======================

This package has no dedicated administrator interface, but adds the MemcachedFast cache backend to OTRS.

The MemcachedFast OTRS cache backend uses the CPAN module `Cache::Memcached::Fast <https://metacpan.org/pod/release/KROKI/Cache-Memcached-Fast-0.23/lib/Cache/Memcached/Fast.pm>`__, which is a Perl client for memcached, a memory cache daemon.

`Memcached <https://www.memcached.org/>`__ is a free and open source, high-performance, distributed memory object caching system. It is often used to speed up big dynamic database-driven websites by caching data and objects in RAM to reduce the number of times an external data source (such as a database or API) must be read.


Basics
------

.. note::

   After installation and configuration, you need to change the ``Cache::Module`` setting to use ``MemcachedFast``, if you haven't done this yet.

It is required to have at least 1 memcache server. It is recommended to have more (smaller) servers than a single big one. High availability clusters will definitely need more than 1 server. Only 1 server means a single point of failure.

It is recommended to use the latest versions of the required CPAN modules ``Storable`` and ``Cache::Memcached::Fast``.

.. note::

   Memcached does not handle authentification and replication.

.. warning::

   Do not use patches that will install replication, like ``repcached``. It is not supported.


Memory Settings
---------------

By default, memcached generally only sets aside a small amount of RAM for the cache. This may differ depending on the operating system or Linux distribution, but it varies between 64MB and 512MB. The more memory you can give to memcached, the better is. At least 4GB is required for OTRS. Large deployments may want to give even more.

A rough guideline from our experience for a frontend server without database is to divide the memory equally between the OS, apache and memcached (1/3).

To increase the amount of memory available to memcached, modify the value passed along with ``-m``. This value is in megabytes. For example, to specify 2GB of cache space, pass ``-m 2048``. Your setup most likely has a configuration file where you can set this. On Linux, memcached stores its settings in ``/etc/memcached.conf``.

.. note::

   Restart the memcache daemon, when changing the configuration.


Security
--------

Memcached does not handle authentification. The user is responsible for data security. So make sure to secure your network (e.g. subnetting, separated network or firewalling).

But also make sure that each OTRS instance can communicate with each memcached server.


Monitoring
----------

It is recommended to use monitoring tools, like `phpmemcacheadmin <https://code.google.com/archive/p/phpmemcacheadmin/>`__.

There are also extensions for Nagios, like `these <https://exchange.nagios.org/index.php?option=com_mtree&amp;task=search&amp;Itemid=74&amp;searchword=memcached>`__.
