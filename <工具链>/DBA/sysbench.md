# [sysbench测试工具](http://www.cnblogs.com/cchust/p/4723672.html)

### sysbench简介

 Sysbench是一个模块化的、跨平台、多线程基准测试工具，主要用于评估测试各种不同系统参数下的数据库负载情况。它主要包括以下几种方式的测试：cpu性能，磁盘io性能，线程调度性能，内存分配及传输速度和数据库性能。由于本人是dba，因此重点关注sysbench测试数据库的场景。目前sysbench支持mysql，postgreSQL，oracle三种数据源。