# Maven

> 以下内容总结自：《Maven 实战》—— 许晓斌

Maven 是什么？

- 自动化构建工具
- 依赖管理工具


---

### 1. 构件

在 Maven 中，任何一个依赖、插件或者项目构件的输出，都可以称为构件。

- [依赖](./1.构件/依赖.md)


### 2. 仓库

- [intro](./2.仓库/README.md)
- [镜像](./2.仓库/镜像.md)


### 3. 生命周期

- [intro](./3.生命周期/README.md)


### 4. 插件

- [intro](./4.插件/README.md)
- 常用插件
    - [maven-surefire-plugin](./4.插件/maven-surefire-plugin.md)
    - [maven-archetype-plugin](./4.插件/maven-archetype-plugin.md)
        - [archetype-catalog.xml](./4.插件/archetype-catalog.xml.md)


### 5. 聚合 & 继承
- [聚合](./5.聚合&继承/聚合.md)
- [继承](./5.聚合&继承/继承.md)

### 6. 构建
- [intro](./6.构建/README.md)
- [Maven 属性](./6.构建/Maven属性.md)


### 7. 原型（Archetype）

- [intro](./7.原型/README.md)
- [自定义 Archetype](./7.原型/自定义Archetype.md)
    - [archetype-metadata.xml](./7.原型/archetype-metadata.xml.md)


### 8. 生成项目站点
- [intro](./8.生成项目站点/README.md)


### 9. 附录

- [pom.xml](./附录pom.xml.md)
- [settings.xml](./附录settings.xml.md)



## archetype

### [1. maven-archetype](/maven-archetype)

Java 项目通用原型。包含以下内容，

- pom.xml
- .gitignore
- README.md


### [2. ddd-archetype](/ddd-archetype)

Java DDD 项目通用原型。包含以下内容，

- modules
- pom.xml
- .gitignore
- README.md
