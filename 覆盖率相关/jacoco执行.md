### 1.资料来源
- 官网下载：<https://www.jacoco.org/jacoco/trunk/doc/agent.html>
### 2.javaagent步骤
- 打包 忽略
- 启动服务并执行测试 
```
java -javaagent:jacocoagent.jar=includes=*,output=tcpserver,port=9100,address=127.0.0.1 -jar rest-service-0.0.1-SNAPSHOT.jar
```
- 生成报告 
```
java -jar jacococli.jar dump --address 127.0.0.1 --port 9100 --destfile ./jacoco.exec --reset
```
- 导出报告
```
java -jar jacococli.jar report ./jacoco.exec --classfiles C:/Users/yindo/IdeaProjects/gs-rest-service/complete/target/classes --sourcefiles  C:/Users/yindo/IdeaProjects/gs-rest-service/complete/src/main/java --encoding utf-8 --html jacoReport
```
