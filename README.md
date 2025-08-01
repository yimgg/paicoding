## 项目演示

### 前台社区系统


![](https://cdn.tobebetterjavaer.com/images/20230602/d7d341c557e7470d9fb41245e5bb4209.png)

### 后台社区系统


![](https://cdn.tobebetterjavaer.com/images/20230602/83139e13a4784c0fbf0adedd8e287c5b.png)


### 组织结构

```
paicoding
├── pai-coding-front -- 前台社区系统
├── pai-coding-admin -- 后台社区系统
├── paicoding-api -- 定义一些通用的枚举、实体类，定义 DO\DTO\VO 等
├── paicoding-core -- 核心工具/组件相关模块，如工具包 util， 通用的组件都放在这个模块（以包路径对模块功能进行拆分，如搜索、缓存、推荐等）
├── paicoding-service -- 服务模块，业务相关的主要逻辑，DB 的操作都在这里
├── paicoding-web -- Web模块、HTTP入口、项目启动入口，包括权限身份校验、全局异常处理等
```

### 环境配置说明

资源配置都放在 `paicoding-web` 模块的资源路径下，通过maven的env进行环境选择切换

当前提供了四种开发环境
```
- resources-env/dev: 本地开发环境，也是默认环境
- resources-env/test: 测试环境
- resources-env/pre: 预发环境
- resources-env/prod: 生产环境
```
环境切换命令

```bash
# 如切换生产环境
mvn clean install -DskipTests=true -Pprod
```

### 配置文件说明

- resources
  - application.yml: 主配置文件入口
  - application-config.yml: 全局的站点信息配置文件
  - logback-spring.xml: 日志打印相关配置文件
  - liquibase: 由liquibase进行数据库表结构管理
- resources-env
  - xxx/application-dal.yml: 定义数据库相关的配置信息
  - xxx/application-image.yml: 定义上传图片的相关配置信息
  - xxx/application-web.yml: 定义web相关的配置信息


### 前端环境配置说明

- 前台前端环境使用的是Vue3，所以需要安装Vue3的环境
- 后台前端环境使用React18，所以需要安装React18的环境
- 本地的用户名和密码均为 admin 和 admin 
- 后端的地址目前配置需要在`src/http/URL.ts`中配置`BASE_URL`和`WS_URL`，分别对应后端的HTTP和WebSocket地址
- 其余配置只需要运行
    ``` bash
    npm install
    npm run dev
    ```


### 开发环境

|      工具       | 版本      | 下载                                                                                                                     |
|:-------------:|:--------|------------------------------------------------------------------------------------------------------------------------|
|      jdk      | 17+     | [https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html) |
|     maven     | 3.5+    | [https://maven.apache.org/](https://maven.apache.org/)                                                                 |
|     mysql     | 8.0+    | [https://www.mysql.com/downloads/](https://www.mysql.com/downloads/)                                                   |
|     redis     | 6.0+    | [https://redis.io/download/](https://redis.io/download/)                                                               |
| elasticsearch | 8.0.0+  | [https://www.elastic.co/cn/downloads/elasticsearch](https://www.elastic.co/cn/downloads/elasticsearch)                 |
|     nginx     | 1.10+   | [https://nginx.org/en/download.html](https://nginx.org/en/download.html)                                               |
|   rabbitmq    | 3.12+   | [https://www.rabbitmq.com/news.html](https://www.rabbitmq.com/news.html)                                               |
|    ali-oss    | 3.15.1  | [https://help.aliyun.com/document_detail/31946.html](https://help.aliyun.com/document_detail/31946.html)               |
|      git      | 2.34.1  | [http://github.com/](http://github.com/)                                                                               |
|    docker     | 4.10.0+ | [https://docs.docker.com/desktop/](https://docs.docker.com/desktop/)                                                   |
| let's encrypt | https证书 | [https://letsencrypt.org/](https://letsencrypt.org/)                                                                   |



