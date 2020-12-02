# 生命周期

### 1. 什么是生命周期？
项目有清理、编译、测试和部署等一系列构建过程，也可以称为项目的生命周期；Maven 对所有的构建过程进行抽象和统一，形成了 Maven 自己的一套生命周期。

Maven 的生命周期是抽象的概念，实际是通过插件来实现周期内每个阶段对应的功能。

### 2. Maven 的生命周期
Maven 有三套生命周期，相互独立，分别对应三类构建功能。
- clean 清理项目
- default 构建项目
- site 建立项目站点

**每套生命周期都包含一些阶段（phase）**，阶段之间都具有顺序依赖。

#### clean 生命周期
clean 生命周期表示清理项目的过程，包含这些阶段：
- pre-clean 执行一些清理前需要完成的工作。
- *clean*  清理上一次构建生成的文件。
- post-clean  执行一些清理后需要完成的工作。

#### default 
default 生命周期表示实际的项目构建过程。
- validate
- initialize
- generate-sources
- *process-sources* ：处理项目主资源文件。一般是对 src/main/resources 目录的内容进行变量替换等工作，复制到项目输出的主 classpath 目录中。
- generate-resources
- process-resources
- **compile** ：编译项目的主源码。一般是编译 src/main/java 目录下的 java 文件到项目输出的主 classpath 目录中。
- process-classes
- generate-test-sources
- *process-test-sources* ：处理项目测试资源文件。一般是对 src/test/resources 目录的内容进行变量替换等工作，复制到项目输出的测试 classpath 目录中。
- generate-test-resources
- process-test-resources
- *test-compile* ：编译项目的主源码。一般是编译 src/test/java 目录下的 java 文件到项目输出的测试 classpath 目录中。
- process-test-classes
- **test** ：使用单元测试框架运行测试，测试代码不会被打包或部署。
- prepare-package
- **package** ：把编译好的代码打包成可发布的格式，如 JAR 包。
- pre-integration-test
- integration-test
- post-integration-test
- verify
- **install** ：将包安装到本地 Maven 仓库，供本地项目使用。
- **deploy** ：将包复制到远程仓库，供其他人使用。

#### site 生命周期
site 生命周期表示建立和发布项目站点的过程。
- pre-site 执行一些生成项目站点前需要完成的工作。
- site 生成项目站点文档。
- post-site 执行一些生成项目站点后需要完成的工作。
- site-deploy 将生成的项目站点发布到服务器上。