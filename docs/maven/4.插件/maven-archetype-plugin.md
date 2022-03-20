# maven-archetype-plugin

Maven 中的 Archetype 功能都是通过 maven-archetype-plugin 插件实现。


### 使用 Archetype 生成一个项目骨架

1. 运行命令：`mvn archetype:generate`；
2. 选择要使用的 Archetype；
3. 输入要创建的项目的 4 个必要信息
    - groupId
    - artifactId
    - version
    - package

![maven-archetype-plugin](/assets/images/maven/maven-archetype-plugin.png)

**上图中，列出的所有可用 Archetype 来自于文件 `archetype-catalog.xml`，所以 `archetype-catalog.xml` 文件决定了能够使用的 Archetype，也可以指定使用哪个 `archetype-catalog.xml` 文件。**

> 参考：[archetype-catalog.xml](/docs/maven/4.插件/archetype-catalog.xml.md)

#### 1. 指定 archetype-catalog.xml 文件位置

> maven-archetype-plugin 不指定 archetype-catalog.xml 文件位置时，默认 remote、local。

```bash
mvn archetype:generate -DarchetypeCatalog=xxx
```

#### 2. 指定 Archetype 具体坐标

常用于自动化脚本生成项目

```bash
mvn archetype:generate -B \
    -DarchetypeGroupId=org.apache.maven.archetypes
    -DarchetypeArtifactId=maven-archetype-quickstart
    -DarchetypeVersion=1.1
    -DgroupId=com.test
    -DartifactId=t
    -Dversion=1.0-SNAPSHOT
    -Dpackage=com.test.t
```
