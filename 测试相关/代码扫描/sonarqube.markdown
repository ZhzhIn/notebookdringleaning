### sonarcanner
<https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/>
在conf下配置sonar-scanner.properties
```
# must be unique in a given SonarQube instance
sonar.projectKey=8a66a9a9bc94af9b877e31110e84c818e1de138e

# --- optional properties ---
#----- Default SonarQube server
sonar.host.url=http://sonarqube.ceshiren.com:9000
# defaults to project key
sonar.projectName=javaclient_cli_yinzzzzzzz
# defaults to 'not provided'
#sonar.projectVersion=1.0
sonar.sources=src/
# Path is relative to the sonar-project.properties file. Defaults to .
sonar.java.binaries=build/classes
 
# Encoding of the source code. Default is default system encoding
sonar.sourceEncoding=UTF-8
#sonar-scanner.bat -Dsonar.login=8a66a9a9bc94af9b877e31110e84c818e1de138e
```
进入项目路径执行扫描
sonar-scanner -Dsonar.projectKey=myproject -Dsonar.sources=src1