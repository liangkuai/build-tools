# 构建

### 如何部署到远程仓库？
在项目 pom.xml 文件中添加配置

```xml
<distributionManagement>
    <repository>
        <id>releases</id>
        <name>Releases</name>
        <url>http://repo.com/content/repositories/releases</url>
    </repository>
    <snapshotRepository>
        <id>snapshots</id>
        <name>Snapshots</name>
        <url>http://repo.com/content/repositories/snapshots</url>
    </snapshotRepository>
</distributionManagement>
```

如果远程仓库需要认证，就需要在 `${user.home}/.m2/settings.xml` 中添加 `<server>` 认证配置。