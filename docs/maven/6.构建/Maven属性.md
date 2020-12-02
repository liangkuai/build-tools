# Maven 属性

Maven 中的属性

#### 1. 内置属性
- ***`${basedir}`*** ：表示项目根目录，即包含 pom.xml 文件的目录
- `${version}` ：表示项目版本


#### 2. pom 属性
也就是 pom.xml 文件中的元素
- `${project.groupId}` ：也就是 `<project><groupId>` 元素的值，项目的 groupId
- `${project.artifactId}`
- `${project.version}`
- ***`${project.build.sourceDirectory}`*** : 项目的主源码目录，默认：`src/main/java`
- ***`${project.build.testSourceDirectory}`*** : 项目的测试源码目录，默认：`src/test/java`
- `${project.build.directory}` ：项目构建输出目录，默认：`target/`


#### 3. 自定义属性
就是项目 pom.xml 文件中 `<properties>` 元素下自定义的 Maven 属性。


#### 4. Settings 属性
用户目录下 settings.xml 文件中的元素，例如：`${settings.localRepository}`


#### 5. Java 系统属性
例如：`${user.home}` 表示用户目录。`mvn help:system` 查看所有 Java 系统变量。


#### 6. 环境变量属性
使用时加上 env. 前缀，例如：`${env.JAVA_HOME}`。`mvn help:system` 查看所有环境变量。