## 1. 示例项目介绍
基于项目[boot-data-elasticsearch](https://github.com/hantsy/spring-reactive-sample/tree/master/boot-data-elasticsearch)修改得到。

当中解决了连接新版本Elasticsearch时需要SSL连接的问题。

并且通过Active profile动态的插入不同的索引。详见：class Post上的`@Document(indexName = "#{ @environment.getActiveProfiles()[0] + '-' + 'posts'}")`

## 2. 如何使用？
### 下载项目
复制你的Elasticsearch的证书覆盖`elastic-search/http_ca.crt`

如果你也是使用Docker的话，可以使用如下命令，记得修改你的容器名称
```shell
docker cp es01:/usr/share/elasticsearch/config/certs/http_ca.crt .
```

### 修改配置文件中ES的链接
修改[application-dev.yaml](src%2Fmain%2Fresources%2Fapplication-dev.yaml)文件，并且启动的时候带上active profile

顺利的话你就能看到ES中被插入了两条数据

以下是英文版

## 1. Project Introduction
This project is based on the [boot-data-elasticsearch](https://github.com/hantsy/spring-reactive-sample/tree/master/boot-data-elasticsearch) repository with modifications. 
It resolved the SSL connection issue when connecting to a newer version of Elasticsearch.

Additionally, it dynamically inserts different indexes on ES based on the active profile. This can be seen in the `@Document(indexName = "#{ @environment.getActiveProfiles()[0] + '-' + 'posts'}")` annotation on the class `Post` .

## 2. How to Use?

### Download the Project
Copy your Elasticsearch certificate to overwrite `elastic-search/http_ca.crt`

If you are using Docker, you can use the following command (make sure to modify your container name):
```shell
docker cp es01:/usr/share/elasticsearch/config/certs/http_ca.crt .
```

### Update the ES Connection in the Configuration File
Modify the `application-*.yaml` file and start the application with the active profile.

If everything goes smoothly, you should see two data entries inserted into Elasticsearch.





