# 附录 settings.xml

```xml
<settings>
  <localRepository>本地仓库</localRepository>

  <!--镜像仓库配置-->
  <mirrors>
    <mirror>
      <id>central-mirror</id>
      <!--需要克隆/代理的仓库 id，一般是远程仓库-->
      <mirrorOf>central</mirrorOf>
      <name>Central Mirror</name>
      <url>http://my.repository.com/repo/path</url>
    </mirror>
    ...
  </mirrors>
  
  <!--远程仓库认证配置-->
  <servers>
    <server>
      <!--远程仓库 id 必须和项目中 pom 文件配置的远程仓库 id 一致-->
      <id>remote-repo</id>
      <username>repouser</username>
      <password>repopwd</password>
    </server>
    ...
  </servers>
  
</settings>
```