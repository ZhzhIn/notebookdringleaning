###项目结构：  
![](.jacoco源码阅读_images/73a9e1e6.png)
 
模块内容拆分
参考：https://www.jacoco.org/jacoco/trunk/doc/api/index.html?overview-summary.html  

Bundle org.jacoco.core  
核心包实现了代码覆盖技术。它提供 API 和implementation，用于class文件检测（instrumentation), 收集runtime执行数据并分析覆盖率数据，分析覆盖数据。  
org.jacoco.core - jacoco源信息    
org.jacoco.core.analysis-覆盖率计算和分析  
org.jacoco.core.data-执行数据和会话信息的展示和持久化  
org.jacoco.core.instr-检测用于代码覆盖的 Java 类文件  
org.jacoco.core.runtime-运行控制和执行数据采集	 
org.jacoco.core.tools-使用jacoco核心api的工具集合	 

Bundle org.jacoco.report
提供创建不同格式的覆盖率报告的api和implementation 
org.jacoco.report	生成报告的公共接口和工具包(utilities)
org.jacoco.report.check	规则检查实现.
org.jacoco.report.csv	csv报告实现.
org.jacoco.report.html	html报告实现.
org.jacoco.report.xml	XML报告实现.

Bundle org.jacoco.agent
提供运行java代理jar包资源
org.jacoco.agent	提供运行java代理jar包资源

JaCoCo Runtime
com.vladium.emma.rt	兼容API for EMMA .
org.jacoco.agent.rt	用于从被测 JVM 中访问 JaCoCo 代理的 API.  