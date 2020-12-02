# 自定义 Archetype

> Archetype 本质上就是一个 JAR 包，而这个 JAR 包也是由一个 Maven 项目打包生成的，一样需要经过 maven 编译等操作打包到仓库。再通过 maven-archetype-plugin 插件使用仓库中打包好的 Archetype 生成一个项目和骨架。

### 1. 编写 Archetype Maven 项目

#### 手动编写
按 Archetype Maven 项目的规范编写项目，一个典型的 Archetype Maven 项目包括以下几个部分：

| 文件/目录 | 说明 |
| :-- | :-- |
| pom.xml | 当前项目的 pom |
| **src/main/resources/archetype-resources/pom.xml** | 基于当前 Archetype 生成的项目的 pom |
| src/main/resources/archetype-resources/** | Archetype 的其他初始文件。<br>也就是需要包含在基于当前 Archetype 生成的项目的其他文件。 |
| **src/main/resources/META-INF/maven/archetype-metadata.xml** | Archetype 描述文件，有特定的语法。参考：[archetype-metadata.xml](/dcos/maven/7.原型/archetype-metadata.xml.md) |

#### 使用 maven-archetype-plugin 生成
如果觉得手动编写 Archetype 的 Maven 项目有点麻烦，可以直接用 maven-archetype-plugin 插件生成一个 Archetype Maven 项目。
1. 创建一个空的 Maven 项目
2. 编写项目骨架
3. 执行 maven 命令：`mvn clean archetype:create-from-project`

这样，在项目目录：`target/generated-sources/archetype` 下就生成了一个 Archetype Maven 项目。


### 2. 生成 Archetype
对于手动编写的项目，直接在项目根目录下执行以下命令；而对于使用 maven-archetype-plugin 插件生成的 Archetype Maven 项目，进入项目根目录下 `target/generated-sources/archetype` 目录执行以下命令。

```bash
# 编译&打包到仓库
$ mvn clean install
```