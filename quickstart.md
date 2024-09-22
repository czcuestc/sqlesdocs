下载[SqlEs demo](https://github.com/czcuestc/sqles)

1. 环境要求

```java
JDK1.8
Springboot 2.7.5
```



2. 添加SqlEs依赖

```xml
<properties>
  <sqles.version>1.0.0-SNAPSHOT</sqles.version>
</properties>
```

```xml
<dependency>
    <groupId>com.czcuestc.sqles</groupId>
    <artifactId>sqles-core</artifactId>
    <version>${sqles.version}</version>
</dependency>
```

3. 在配置类添加扫描

```java
@MapperScan(basePackages = "com.sqles.demo.mapper")
@SqlEsMapperScan(basePackages = "com.sqles.demo")
```

SqlEsMapperScan会扫描所有索引实体类的注解配置，注册IndexMapper bean，indexMapper为索引管理接口，通过它可以创建，新增，删除索引等功能。



4. 数据源配置

  sqles配置和数据库配置一样，唯一区别是连接字符串为jdbc:es开头。

```yaml
spring:
  datasource:
    sqles:
      url: jdbc:es://localhost:9200
      username: root
      password: xxxxxx
      driver-class-name: com.czcuestc.sqles.jdbc.Driver
      type: com.alibaba.druid.pool.DruidDataSource
      druid:
        initial-size: 15 #连接池初始化大小
        min-idle: 20 #最小空闲连接数
        max-active: 30 #最大连接数
```



5. 和Mybatis，druid集成

  集成方式和数据库一样，不做说明。



6. 支持的sql语法

  

```plsql
SELECT column1, column2, ...
FROM index_name
WHERE condition
ORDER BY column1, column2, ... ASC|DESC
LIMIT number;
```







