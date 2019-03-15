Eureka
=====
[![Build Status](https://travis-ci.org/Netflix/eureka.svg?branch=master)](https://travis-ci.org/Netflix/eureka)

Eureka is a REST (Representational State Transfer) based service that is primarily used in the AWS cloud for locating services for the purpose of load balancing and failover of middle-tier servers.

At Netflix, Eureka is used for the following purposes apart from playing a critical part in mid-tier load balancing.

* For aiding Netflix Asgard - an open source service which makes cloud deployments easier, in  
    + Fast rollback of versions in case of problems avoiding the re-launch of 100's of instances which 
      could take a long time.
    + In rolling pushes, for avoiding propagation of a new version to all instances in case of problems.

* For our cassandra deployments to take instances out of traffic for maintenance.

* For our memcached caching services to identify the list of nodes in the ring.

* For carrying other additional application specific metadata about services for various other reasons.


Building
----------
The build requires java8 because of some required libraries that are java8 (servo), but the source and target compatibility are still set to 1.7.


Support
----------
[Eureka Google Group](https://groups.google.com/forum/?fromgroups#!forum/eureka_netflix)


Documentation
--------------
Please see [wiki](https://github.com/Netflix/eureka/wiki) for detailed documentation.


Eureka 是 Netflix 开源的服务注册发现组件，分成 Client 和 Server 两部分

Eureka-Server ：通过 REST 协议暴露服务，提供应用服务的注册和发现的功能。
Application Provider ：应用服务提供者，内嵌 Eureka-Client ，通过它向 Eureka-Server 注册自身服务。
Application Consumer ：应用服务消费者，内嵌 Eureka-Client ，通过它从 Eureka-Server 获取服务列表。
请注意下，Application Provider 和 Application Consumer 强调扮演的角色，实际可以在同一 JVM 进程，即是服务的提供者，又是服务的消费者。