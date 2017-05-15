# 配置Sonar客户端
## 配置插件及Profile，此配置可以放在Maven的settings，也可以放在具体的maven pom里
### 配置如下：
``` xml
<pluginGroups>
		<pluginGroup>org.sonarsource.scanner.maven</pluginGroup>
	</pluginGroups>
	<profiles>
		<profile>
            <id>sonar</id>
            <!-- Optional -->
            <activation>
               <activeByDefault>true</activeByDefault>
            </activation>
            <!-- Optional -->
            <properties>
			<sonar.host.url>
			    http://${sonar.server.ip}:${sonar.server.port}/sonar
            </sonar.host.url>
          </properties>
        </profile>
	</profiles>
```
## 配置完成后即可在maven或eclipse maven插件上使用命令来为自己的java project进行sonar代码检查了
### 命令如下： 
``` maven
	mvn verify sonar:sonar
```
