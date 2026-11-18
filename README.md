# final

基于 Spring Boot 的店铺信息展示与后台管理项目。前台通过 Thymeleaf 分页展示店铺信息，后台结合 Layui 提供信息维护界面，使用 MySQL 保存用户与店铺数据。

## 主要功能

- **店铺信息展示**：分页展示店铺名称、图片、介绍和地址。
- **店铺信息管理**：提供新增、编辑、删除和批量删除入口，管理编号、名称、联系电话、地址、介绍及配图。
- **图片上传与访问**：接收上传图片并保存到本地目录，通过静态资源映射提供图片访问。
- **账号登录与注册**：提供用户注册和登录接口，根据查询结果返回管理员或普通用户标识；当前实现未形成完整的会话与权限控制。

## 核心模块

- **`UserController`**：处理登录、注册和前台首页请求，将分页查询结果交给模板展示。
- **`StoreController`**：提供店铺数据加载、新增、修改、单条与批量删除、图片上传等接口。
- **`StoreService` / `UserService`**：组织店铺与用户相关的业务调用，连接控制器和数据访问层。
- **`StoreRepository` / DAO / MyBatis Mapper**：通过 Spring Data JPA 与 MyBatis 完成分页查询及数据增删改查。
- **`Store` / `User`**：数据模型，描述店铺资料和用户信息。
- **Thymeleaf 模板与前端脚本**：组织首页、登录、管理、新增与编辑页面，使用 Layui 和 jQuery 完成交互。
- **`WebMvcConfig`**：将本地图片目录映射到 `/images/**`，供页面读取店铺配图。

## 运行说明

- 使用 Java 8、Maven 和 MySQL；项目基于 Spring Boot 2.4.1。
- 在 `src/main/resources/application.properties` 中配置数据库连接，并准备与实体及 Mapper 对应的表结构；仓库未提供数据库初始化脚本。
- 图片上传目录在 `StoreController` 中指定，图片访问目录在 `WebMvcConfig` 中指定；运行前需将两处调整为同一个可用的本地目录。
- 从 IDE 启动 `com.example.demo.DemoApplication`，访问 `/toIndex` 查看前台页面，或通过 `/toLogin` 进入登录页面。
