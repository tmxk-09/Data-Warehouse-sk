# Data-Warehouse-sk
企业级的一站式数据中枢。它以高效的 ETL 引擎为核心，通过强大的分布式调度系统，驱动海量数据在预设的定时任务下精准流转。它打破了数据孤岛，完美适配主流的关系型、非关系型及云端数据库，确保企业数据资产如脉搏般稳定、实时地汇聚与更新。
是一款专注于全链路自动化的数据集成平台。系统深度集成了清洗、转换、加载（ETL）全过程，支持复杂拓扑结构的任务调度与多频率定时触发。凭借卓越的多源数据库连接能力，NexusFlow 能够将破碎的原始数据转化为标准化的生产力，为决策提供坚实的数据底座。

# 核心关键词提取：
 * ETL: Extract, Transform, Load (抽取、转换、加载)
 * Scheduler: 调度
 * Multi-source: 多源支持
 * Automation: 自动化
 * 支持在线kettle 文件查看编辑。

 * 全向集成： 零门槛对接多种异构数据库，实现数据的无缝跨库迁移与同步。
 * 敏捷 ETL： 可视化构建数据清洗与加工逻辑，让原始数据快速转化为高质量资产。
 * 智能调度： 毫秒级任务触发机制，支持周期性定时任务与依赖管理，保障数据生产永不停歇。
 * 可靠监控： 实时追踪任务流向与运行状态，异常自动告警，确保数据管道始终畅通。


# 系统运行截图如下
## 登录页面
<img width="2992" height="1634" alt="image_6" src="https://github.com/user-attachments/assets/3cf1d9ce-e119-4058-932d-86c1a0639332" />

## 调度日志页面

<img width="2992" height="1634" alt="image_10" src="https://github.com/user-attachments/assets/796e97a5-5761-4f35-982a-3185312a9a41" />

<img width="2992" height="1634" alt="image_9" src="https://github.com/user-attachments/assets/3382afc8-11b3-4818-b3cf-1245e19b76c4" />
<img width="2992" height="1634" alt="image_8" src="https://github.com/user-attachments/assets/adb81e88-a8b8-4b94-bcbc-0b605da49755" />
<img width="2992" height="1634" alt="image_7" src="https://github.com/user-attachments/assets/5928c6ae-4c3e-4fa2-b6d6-49814fc47332" />

<img width="2992" height="1634" alt="image_5" src="https://github.com/user-attachments/assets/696586a4-42e6-4a3d-8b9e-5b4f34cfa8bd" />
<img width="2992" height="1634" alt="image_4" src="https://github.com/user-attachments/assets/e59dcd45-44f7-4ecb-8c32-c1c7ce44b2d2" />
<img width="2992" height="1634" alt="image_3" src="https://github.com/user-attachments/assets/7ddabd54-13a3-4263-b173-7b3ef996ba5f" />



## 作业调度

<img width="2992" height="1634" alt="image_2" src="https://github.com/user-attachments/assets/ba6a4feb-931a-44ff-9ca2-039e3a451b4b" />

## 定时管理

<img width="2992" height="1634" alt="image_1" src="https://github.com/user-attachments/assets/ee364c06-3471-4bc2-8c96-25f4f292e3a1" />


# 项目技术栈分析文档

## 📌 项目概述

**项目名称**: 数据调度平台
**项目描述**: 基于 Pentaho Kettle 的企业级 ETL 数据集成平台
**项目版本**: 0.0.1-SNAPSHOT

---

## 🏗️ 项目架构


### 架构特点

- **分层架构**: 采用经典的三层架构 (Controller-Service-Dao)
- **模块化设计**: 按功能拆分为多个独立模块，便于维护和扩展
- **插件化扩展**: 基于 Kettle 的插件机制，支持自定义插件
- **微服务准备**: 已引入 Spring Cloud，为微服务化预留空间

---

## ⚙️ 核心技术栈

### 1. 基础框架层

| 技术 | 版本 | 说明 |
|------|------|------|
| Java | JDK 1.8 | 开发语言 |
| Spring Boot | 2.0.8.RELEASE | 应用框架 |
| Spring Cloud | Edgware.SR1 | 微服务框架 |
| Spring Security | 2.0.8.RELEASE | 安全认证框架 |
| Spring AOP | 2.0.8.RELEASE | 面向切面编程 |
| AspectJ | 1.9.7 | AOP增强 |

**特性说明**:
- 使用 Spring Boot 快速搭建应用
- 集成 Spring Security 实现权限控制
- 通过 AOP 实现日志记录、数据源切换等横切关注点

### 2. ETL 引擎层

| 技术 | 版本 | 说明 |
|------|------|------|
| Pentaho Kettle Core | 9.2.0.0-179 | ETL 核心引擎 |
| Kettle Engine | 9.2.0.0-179 | 转换和作业执行引擎 |
| Kettle DB Dialog | 9.2.0.0-179 | 数据库连接对话框 |
| Kettle UI SWT | 9.2.0.0-179 | UI 组件 |

**Kettle 插件扩展**:
- `elasticsearch-bulk-insert-core` (8.3.0.0-371): Elasticsearch 批量插入
- `kettle-json-plugin-core` (9.2.0.0-159): JSON 数据处理
- `pentaho-mongodb-plugin` (9.3.0.0): MongoDB 数据源支持
- `pentaho-mongo-utils` (9.3.0.0): MongoDB 工具类

### 3. 持久层技术

| 技术 | 版本 | 说明 |
|------|------|------|
| MyBatis | 3.4.2 | ORM 框架 |
| MyBatis Spring Boot Starter | 1.3.5 | MyBatis 自动配置 |
| TK MyBatis | 3.5.2 | 通用 Mapper |
| Mapper Spring Boot Starter | 2.1.4 | Mapper 自动配置 |
| PageHelper | 4.2.1 | 分页插件 |
| MyBatis Generator | 1.3.7 | 代码生成器 |

**数据库支持**:
- MySQL: 8.0.20
- Oracle: 12.2.0.1 (ojdbc8)
- MongoDB: 3.12.14 (mongo-java-driver)
- SQL Server: 4.0 (sqljdbc4)

**连接池**:
- Alibaba Druid: 1.1.9
- Druid Spring Boot Starter: 1.1.9

### 4. 分布式 & 中间件

| 技术 | 版本 | 说明 |
|------|------|------|
| Apache ShardingSphere | 4.0.0 | 分库分表中间件 |
| Sharding JDBC Core | 4.0.0 | 数据分片核心 |
| Sharding Transaction XA | 4.0.0 | 分布式事务 |
| Zookeeper | 3.4.13 | 分布式协调 |
| ZkClient | 0.11 | Zookeeper 客户端 |
| Redis | 2.0.8.RELEASE | 缓存中间件 |

**分布式特性**:
- 支持分库分表，处理大数据量场景
- 基于 XA 协议的分布式事务
- Zookeeper 实现分布式锁和配置管理
- Redis 实现分布式缓存和会话共享

### 5. Web 层技术

| 技术 | 版本 | 说明 |
|------|------|------|
| Spring Web MVC | 2.0.8.RELEASE | Web 框架 |
| Servlet API | 3.0.1 | Servlet 规范 |
| Eclipse Jetty | 8.1.15.v20140411 | 嵌入式服务器 (Kettle) |
| Swagger2 | 2.9.2 | API 文档 |
| Springfox Swagger UI | 2.9.2 | Swagger UI |

**Jetty 组件** (Kettle 依赖):
- jetty-server, jetty-http, jetty-io
- jetty-webapp, jetty-servlet
- jetty-security, jetty-plus
- jetty-xml, jetty-util, jetty-continuation

### 6. 安全认证

| 技术 | 版本 | 说明 |
|------|------|------|
| Spring Security | 2.0.8.RELEASE | 安全框架 |
| JWT | 0.9.1 (jjwt) | Token 认证 |
| Kaptcha | 2.3.2 | 验证码生成 |

**安全特性**:
- MD5 密码加密
- JWT Token 认证机制
- XSS 攻击防护
- 图形验证码
- 登录日志审计
- 操作日志记录

### 7. 工具类库

| 分类 | 技术 | 版本 |
|------|------|------|
| JSON 处理 | Fastjson | 1.2.75 |
| | JSON-Lib | 2.4 |
| 工具类 | Apache Commons Lang3 | 3.8.1 |
| | Apache Commons IO | 2.5 |
| | Apache Commons Codec | 1.14 |
| | Apache Commons CLI | 1.4 |
| | Apache Commons Net | 3.6 |
| | Google Guava | 28.2-jre |
| HTTP 客户端 | Apache HttpClient | 4.5.10 |
| | Commons HttpClient | 3.1 |
| 动态代理 | CGLib | 3.2.11 |
| 模板引擎 | FreeMarker | 2.3.23 |
| Excel 处理 | Apache POI | 4.1.2 |
| 文件传输 | JSch | 0.1.54 (SFTP) |
| | Commons Net | 3.6 (FTP) |
| 用户代理 | UserAgentUtils | 1.21 |
| 系统信息 | OSHI | 5.6.0 |
| Git 操作 | JGit | 5.9.0.202009080501-r |
| YAML 解析 | SnakeYAML | 1.23 |
| 数据框架 | JDFrame | 0.0.5 |

### 8. 日志 & 监控

| 技术 | 版本 | 说明 |
|------|------|------|
| SLF4J | 1.7.25 | 日志门面 |
| SLF4J-Log4j12 | 1.7.7 | Log4j 适配器 |
| Spring Boot Actuator | 2.0.8.RELEASE | 应用监控 |
| Logback | 内置 | 日志实现 |

### 9. 开发辅助

| 技术 | 版本 | 说明 |
|------|------|------|
| Lombok | 1.18.30 | 代码简化 |
| Spring Boot Configuration Processor | 2.0.8.RELEASE | 配置元数据 |
| Spring Boot DevTools | 2.0.8.RELEASE | 开发工具 |

---

## 🔧 核心功能模块

### 1. 认证授权模块 (rec-best-kettle-auth)

**核心类**:
- `LoginHandlerService`: 登录处理服务
- `TokenHandlerService`: Token 管理服务
- `CaptchaHandlerService`: 验证码服务
- `UserDetailServiceImpl`: 用户详情服务
- `Md5PasswordEncoder`: MD5 密码编码器

**功能特性**:
- 用户登录/登出
- JWT Token 生成与验证
- 图形验证码生成
- 用户权限加载

### 2. 基础服务模块 (rec-best-kettle-base)

**核心配置**:
- `DruidConfig`: Druid 连接池配置
- `RedisConfig`: Redis 缓存配置

### 3. 核心引擎模块 (rec-best-kettle-core)

**核心类**:
- `KettleInit`: Kettle 初始化配置
- `RepositoryTree`: 资源库树结构
- `XtlExceptions`: 异常处理

**常量定义**:
- `Constant`: 系统常量
- `XJobStatus`: 作业状态枚举
- `XTransStatus`: 转换状态枚举

### 4. 任务调度模块 (rec-best-kettle-job)

**核心类**:
- `ClassCacheFactory`: 类缓存工厂

**功能**:
- 定时任务管理
- 作业调度执行
- 任务状态监控

### 5. 启动器模块 (rec-best-kettle-starter)

**启动类**: `StartServer`
- 初始化 Kettle 插件
- 设置时区为 Asia/Shanghai
- 扫描所有模块的 Mapper
- 排除默认数据源和 MongoDB 自动配置

---

## 🐳 容器化部署

### Dockerfile 分析

**基础镜像**: `frolvlad/alpine-java:jdk8-slim`

**多阶段构建**:
1. **构建阶段**:
   - 安装 fontconfig 和字体
   - 复制应用 JAR 包
   - 复制 Kettle 插件目录
   - 复制中文字体 (SimSun)
   - 生成字体缓存

2. **运行阶段**:
   - 使用轻量级基础镜像
   - 从构建阶段复制必要文件
   - 暴露 9990 端口
   - 启动 Spring Boot 应用

**Docker 插件配置**:
- `docker-maven-plugin`: 1.2.2
- 镜像名称: `bedts-v2.0.0-r01-{timestamp}`
- 镜像标签: `v2.0.0-r01`


## 📊 数据库设计

### 核心表结构

1. **用户权限表**:
   - `x_user`: 用户表
   - `x_role`: 角色表
   - `x_menu`: 菜单表
   - `x_dept`: 部门表
   - `x_user_role`: 用户角色关联表
   - `x_role_menu`: 角色菜单关联表

2. **日志审计表**:
   - `x_login_info`: 登录日志表
   - `x_oper_log`: 操作日志表

3. **在线用户表**:
   - `x_online_user`: 在线用户表

### 数据源配置

**动态数据源**:
- `DynamicDataSource`: 动态数据源路由
- `DataSourceRouterHolder`: 数据源上下文持有者
- `@SetDataSource`: 数据源切换注解

**支持场景**:
- 读写分离
- 多租户数据隔离
- 分库分表路由


## 🔒 安全机制

### 1. 认证流程

```
用户登录请求
    ↓
验证码校验
    ↓
用户名密码验证
    ↓
生成 JWT Token
    ↓
记录登录日志
    ↓
返回 Token
```

### 2. 鉴权流程

```
请求携带 Token
    ↓
Token 有效性验证
    ↓
解析用户信息
    ↓
加载用户权限
    ↓
权限匹配校验
    ↓
放行/拒绝
```

### 3. XSS 防护

**防护策略**:
- 过滤特殊字符
- HTML 实体转义
- URL 白名单配置

### 4. 操作审计

**审计内容**:
- 操作时间
- 操作人员
- 操作模块
- 操作类型
- 操作 IP
- 请求参数
- 返回结果
- 操作状态

---

## 📈 性能优化

### 1. 缓存策略

**Redis 缓存**:
- Token 缓存
- 用户信息缓存
- 权限数据缓存
- 字典数据缓存

**本地缓存**:
- `ClassCacheFactory`: 类加载缓存
- `MapTemplate`: Map 缓存模板

### 2. 数据库优化

**连接池优化**:
- Druid 连接池
- 最小连接数配置
- 最大连接数配置
- 连接超时配置

**分页优化**:
- PageHelper 物理分页
- 避免全表扫描

**分库分表**:
- ShardingSphere 数据分片
- 支持水平扩展

### 3. 异步处理

**异步管理**:
- `ASyncManager`: 异步任务管理器
- `ASyncFactory`: 异步任务工厂

**异步场景**:
- 操作日志异步记录
- 登录日志异步保存
- 邮件异步发送

---

## 🛠️ 构建部署

### Maven 构建

**父 POM 配置**:
- 统一版本管理
- 依赖声明管理
- 资源过滤配置
- 编译配置

**打包插件**:
- `spring-boot-maven-plugin`: 打包 Fat Jar
- `maven-antrun-plugin`: 复制文件到 Docker 目录
- `docker-maven-plugin`: 构建 Docker 镜像

**构建命令**:
```bash
# 编译
mvn clean compile

# 打包
mvn clean package

# 安装 (会触发 Docker 构建)
mvn clean install

# 跳过测试打包
mvn clean package -DskipTests
```

### 部署方式

**1. JAR 包部署**:
```bash
java -jar xxxx-v1.0.0-.jar
```

**2. Docker 部署**:
```bash
docker build -t warehouse-v2.0.0-r01 .
docker run -d -p xxxx:xxxx warehouse-v2.0.0-r01
```

**3. Kubernetes 部署**:
- 支持容器化部署
- 支持水平扩展
- 支持滚动更新

---

## 📝 配置说明

### application.yml 配置

**核心配置**:
```yaml
spring:
  profiles:
    active: druid,dev  # 激活 Druid 和开发环境配置
  messages:
    encoding: UTF-8
    basename: i18n/messages  # 国际化资源位置
```

**环境配置**:
- `application-dev.yml`: 开发环境
- `application-test.yml`: 测试环境
- `application-prod.yml`: 生产环境

---

## 🎯 系统特性

### 1. 高可用

- 支持集群部署
- Redis 会话共享
- Zookeeper 分布式协调
- 健康检查端点

### 2. 高性能

- 连接池优化
- 多级缓存
- 异步处理
- 分库分表

### 3. 可扩展

- 插件化架构
- 模块化设计
- 支持自定义数据源
- 支持自定义 Kettle 插件

### 4. 易维护

- 统一异常处理
- 统一返回格式
- 完善的日志记录
- Swagger API 文档

### 5. 安全性

- 认证授权
- XSS 防护
- SQL 注入防护
- 操作审计

---

## 🚀 技术亮点

1. **基于成熟的 Kettle ETL 引擎**: 支持复杂的数据转换和集成场景
2. **插件化扩展机制**: 支持 Elasticsearch、MongoDB、JSON 等多种数据源
3. **分库分表支持**: 基于 ShardingSphere，支持海量数据处理
4. **完善的权限体系**: RBAC 权限模型，细粒度权限控制
5. **多数据源动态切换**: 支持读写分离、多租户场景
6. **全面的监控审计**: 登录日志、操作日志、在线用户监控
7. **容器化部署**: Docker 多阶段构建，支持 Kubernetes
8. **前后端分离**: 后端提供 RESTful API，Swagger 文档
