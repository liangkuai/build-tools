# archetype-metadata.xml

#### 模板

```xml
<?xml version="1.0" encoding="UTF-8"?>
<archetype-descriptor
        xsi:schemaLocation="http://maven.apache.org/plugins/maven-archetype-plugin/archetype-descriptor/1.0.0 http://maven.apache.org/xsd/archetype-descriptor-1.0.0.xsd"
        name="maven-archetype"
        xmlns="http://maven.apache.org/plugins/maven-archetype-plugin/archetype-descriptor/1.0.0"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <!--
    <modules>: 项目包含多模块
        <module>: 某一个模块
    -->
    <modules>
        <module dir="web">
            <!--
            <fileSets>: 整个模块的目录结构
                <fileSet>: 某一个目录
                    encoding: 编码
                    filtered: 是否替换目录下文件中 ${} 的数据
                    packaged: 是否将该目录下的文件放到生成项目时指定的 package 路径下
            -->
            <fileSets>
                <fileSet filtered="true" packaged="true" encoding="UTF-8">
                    <!--
                    <directory>: 目录路径和名字
                     <includes>: 过滤哪些文件可以放到生成项目中
                        <include>: 过滤规则
                            **: 任意目录
                            *: 任意数量任意字符
                    -->
                    <directory>src/main/java</directory>
                    <includes>
                        <include>**/*.java</include>
                    </includes>
                </fileSet>
                <fileSet filtered="true" packaged="true" encoding="UTF-8">
                    <directory>src/test/java</directory>
                    <includes>
                        <include>**/*.java</include>
                    </includes>
                </fileSet>

                <!-- 过滤模块根目录文件 -->
                <fileSet filtered="true" encoding="UTF-8">
                    <directory></directory>
                    <includes>
                        <include>pom.xml</include>
                        <include>.gitignore</include>
                    </includes>
                </fileSet>
            </fileSets>
        </module>

        <module dir="api">
            <fileSets>
                <fileSet filtered="true" encoding="UTF-8" packaged="true">
                    <directory>src/main/java</directory>
                </fileSet>
            </fileSets>
        </module>
    </modules>

    
    <!--
    在使用 Archetype 生成项目时，必须输入 4 个必要信息: groupId, artifactId, version, package。
    可以用一下方式指定默认值。
    
    <requiredProperties>:
        <requiredProperty>: 指定生成项目时需要的参数和默认值
            key: 属性名
    -->
    <requiredProperties>
        <requiredProperty key="groupId">
            <!--
            <defaultValue>: 默认值
            -->
            <defaultValue>org.test</defaultValue>
        </requiredProperty>
        <requiredProperty key="package">
            <defaultValue>org.test</defaultValue>
        </requiredProperty>
    </requiredProperties>
</archetype-descriptor>
```