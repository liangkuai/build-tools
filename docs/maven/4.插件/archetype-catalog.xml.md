# archetype-catalog.xml

### 1. 什么是 archetype-catalog.xml ？有什么用？
一个包含很多 Archetype 描述信息的文件。

在使用 maven-archetype-plugin 插件生成项目模版时，如果不指定所使用的 Archetype 坐标（直接运行 `mvn archetype:generate`），maven 会列出当前可用的 Archetype 列表，供用户选择；**这里显示的所有 Archetype 信息都是来自于 archetype-catalog.xml 文件**。


### 2. archetype-catalog.xml 文件在哪里？
- `internal` ：maven-archetype-plugin 内置
- `local` ：**~/.m2/repository/archetype-catalog.xml**
- `remote` ：maven 中央仓库下
- `file://...`
- `http://...`


### 3. 生成 archetype-catalog.xml
使用 maven-archetype-plugin 的目标 `archetype:crawl`。

果命令没有加其他参数，默认遍历 settings.xml 文件中的 localRepository，并在该仓库根目录下生成 archetype-catalog.xml。

```bash
$ mvn archetype:crawl
```

可选参数
- `-Drepository` 指定遍历的仓库
- `-Dcatalog` 指定要更新的 archetype-catalog.xml

```bash
$ mvn archetype:crawl \
    -Drepository=~/.m2/repository \
    -Dcatalog=/tmp/archetype-catalog.xml
```