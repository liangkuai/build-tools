# maven-surefire-plugin

### 1. 跳过测试
命令行
- mvn -xxx -DskipTests
- mvn -xxx -Dmaven.test.skip=true


### 2. 指定要运行的测试用例
`mvn xxx -Dtest=xxx1Test,xxx2Test`