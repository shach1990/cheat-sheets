## MySQL 8.0 自带的4个系统数据库
- **information_schema**：这个数据库保存了mysql服务器所有数据库的信息。比如数据库的名、数据库的表、访问权限、数据库表的数据类型，数据库索引的信息等等。
- **performance_schema**：主要用于收集数据库服务器性能参数，可用于监控服务器在一个较低级别的运行过程中的资源消耗、资源等待等情况。
- **sys**：库中所有的数据源来自：performance_schema。目标是把performance_schema的把复杂度降低，让DBA能更好的阅读这个库里的内容。让DBA更快的了解DB的运行情况。
- **mysql**：mysql的核心数据库，主要负责存储数据库的用户、权限设置、关键字等mysql自己需要使用的控制和管理信息。