# 附录 pom.xml

```xml
<project>

    <!--项目坐标-->
    <groupId></groupId>
    <artifactId></artifactId>
    <version></version>
    <packaging></packaging>

    <!--继承配置-->
    <parent>
        <groupId>com.test</groupId>
        <artifactId>parent</artifactId>
        <version>1.0.0-SNAPSHOT</version>
        <!--父模块 pom 文件相对路径，默认：../pom.xml-->
        <relativePath></relativePath>
    </parent>

    <!--聚合配置-->
    <modules>
        <module>模块A pom 文件的相对路径</module>
        <module>模块B pom 文件的相对路径</module>
    </modules>

    <!--变量-->
    <properties></properties>

    <build>
        <extensions>扩展 maven 的核心</extensions>
    </build>

</project>
```

### \<dependencies> & \<dependencyManagement>

```xml
<project>
    ...

    <!--依赖配置-->
    <dependencies>
        <!--
        <type>: 相当于坐标中的 packing，默认 jar
        <scope>: 依赖的作用范围
        <exclusions>: 用来排除传递性依赖
        -->
        <dependency>
            <groupId>com.test</groupId>
            <artifactId>xxx</artifactId>
            <version>${xxx.version}</version>
            <type></type>
            <scope>作用域</scope>
            <exclusions>
                <exclusion>
                    <groupId>com.test</groupId>
                    <artifactId>B</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
        ...
    </dependencies>

    <!--依赖管理配置-->
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>com.test</groupId>
                <artifactId>xxx</artifactId>
                <version>${xxx.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>

            <!--
            scope = import 只有在 <dependencyManagement> 才有用
            作用就是导入并合并所声明的依赖的 pom 文件中的 <dependencyManagement> 配置到当前 pom 文件的 <dependencyManagement> 中
            -->
            <dependency>
                <groupId>com.test</groupId>
                <artifactId>parent</artifactId>
                <version>${parent.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            ...
        </dependencies>
    </dependencyManagement>

    ...
</project>
```

### \<build>

#### \<plugins> & \<pluginManagement>

```xml
<project>
    ...

    <build>

        <plugins>
            <plugin>
                <groupId>com.test</groupId>
                <artifactId>xxx</artifactId>
                <version>${xxx.version}</version>
                <configuration>
                    <source>${java.version}</source>
                    <target>${java.version}</target>
                    <encoding>${project.encoding}</encoding>
                </configuration>
            </plugin>
            ...
        </plugins>

        <!-- 插件管理 -->
        <pluginManagement>
            <plugins>
                <plugin>
                    <groupId>org.apache.maven.plugins</groupId>
                    <artifactId>maven-compiler-plugin</artifactId>
                    <version>${maven-compiler-plugin.version}</version>
                    <configuration>
                        <source>${java.version}</source>
                        <target>${java.version}</target>
                        <encoding>${project.encoding}</encoding>
                    </configuration>
                </plugin>
                <plugin>
                    <groupId>org.apache.maven.plugins</groupId>
                    <artifactId>maven-resources-plugin</artifactId>
                    <version>${maven-resources-plugin.version}</version>
                    <configuration>
                        <encoding>${project.encoding}</encoding>
                    </configuration>
                </plugin>
                ...
            </plugins>
        </pluginManagement>

    </build>

    ...
</project>
```

### \<repositories>

```xml
<project>
    ...

    <!--远程仓库配置-->
    <repositories>
        <repository>
            <!--所配置的每个远程仓库的 id 必须唯一，不然会覆盖配置-->
            <id>test</id>
            <name>test repo</name>
            <url>https://repo.test.com/repository/public/</url>
            <!--
            <releases>: 发布版本使用策略
            <enabled>: 是否开启发布版依赖的下载
            <updatePolicy>: 从远程仓库检查并更新本地依赖的频率
            -->
            <releases>
                <enabled>true</enabled>
                <updatePolicy>interval:2</updatePolicy>
            </releases>
            <!--<snapshots>: 快照版本使用策略-->
            <snapshots>
                <enabled>false</enabled>
                <updatePolicy>interval:2</updatePolicy>
            </snapshots>
        </repository>
        ...
    </repositories>

    ...
</project>
```

### \<pluginRepositories>

```xml
<project>
    ...

    <!--远程插件仓库配置-->
    <pluginRepositories>
        <pluginRepository>
            <!--所配置的每个远程仓库的 id 必须唯一，不然会覆盖配置-->
            <id>test</id>
            <name>test repo</name>
            <url>https://repo.test.com/repository/public/</url>
            <!--
            <releases>: 发布版本使用策略
            <enabled>: 是否开启发布版依赖的下载
            <updatePolicy>: 从远程仓库检查并更新本地依赖的频率
            -->
            <releases>
                <enabled>true</enabled>
                <updatePolicy>interval:2</updatePolicy>
            </releases>
            <!--<snapshots>: 快照版本使用策略-->
            <snapshots>
                <enabled>false</enabled>
                <updatePolicy>interval:2</updatePolicy>
            </snapshots>
        </pluginRepository>
        ...
    </pluginRepositories>

    ...
</project>
```

### \<distributionManagement>

```xml
<project>
    ...

    <!--部署到远程仓库配置-->
    <distributionManagement>
        <!--发布版本部署仓库-->
        <repository>
            <id>releases</id>
            <name>Releases</name>
            <url>http://repo.test.com/content/repositories/releases</url>
        </repository>
        <!--快照版本部署仓库-->
        <snapshotRepository>
            <id>snapshots</id>
            <name>Snapshots</name>
            <url>http://repo.test.com/content/repositories/snapshots</url>
        </snapshotRepository>
    </distributionManagement>

    ...
</project>
```

### \<reporting> \<plugins>

```xml
<project>
    ...

    <!--报告插件配置-->
    <reporting>
        <plugins>
            <plugin>
                <groupId>com.test</groupId>
                <artifactId>xxx</artifactId>
                <version>${xxx.version}</version>
                <configuration>
                    <source>${java.version}</source>
                    <target>${java.version}</target>
                    <encoding>${project.encoding}</encoding>
                </configuration>
            </plugin>
            ...
        </plugins>
    </reporting>

    ...
</project>
```
