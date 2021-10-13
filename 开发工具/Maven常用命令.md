# 清理								

-	mvn clean							
	-	清理并删除target文件夹						
-	mvn clean install-U							
	-	强制检查更新						

# 编译主程序								

-	mvn compile							
	-	会生成target文件夹，里边是编译文件						

# 编译测试程序								

-	mvn test-compile							
	-	会生成test-target文件夹，里边是编译文件						
-	mvn compiler:testCompile 将测试类编译(包括copy资源文件)							

# 执行测试								

-	mvn test							
-	mvn surefire:test 运行测试用例							
-	mvn validate							
	-	验证工程是否正确，所有需要的资源是否可用						
-	mvn verify							
	-	运行任何检查，验证包是否有效且达到质量标准						

# 打包								

-	mvn package							
	-	classes						
	-	会生成maven-archiver文件夹，里边是pom.properties辅助性文件						
	-	会生成surefire-reports文件夹，里边是多个测试报告xxx.txt						
	-	xxx.jar，里边只有主程序						
-	mvn jar:jar							
	-	只打jar包						
-	mvn -Dtest package							
	-	如只打包不测试						
-	mvn source:jar							
	-	源码打包						
-	mvn source:jar-no-fork							
	-	源码打包						
-	mvn generate-sources							
	-	产生应用需要的任何额外的源代码，如xdoclet						

# 安装								

-	mvn intall							
	-	自己开发的Maven工程安装进自己仓库						
	-	将此jar包使用以下的命令安装到本地maven库中						
		-	mvn install:install-file -Dfile=my.jar -DgroupId=mygroup -DartifactId=myartifactId -Dversion=1					
	-	安装第三方Jar到本地库中						
		-	mvn install:install-file -DgroupId=com -DartifactId=client -Dversion=0.1.0 -Dpackaging=jar -Dfile=d:\第三方包路径client-0.1.0.jar -DdownloadSources=true -DdownloadJavadocs=true					

# 生成站点								

-	mvn site							

# 部署								

-	mvn deploy							
	-	发本地jar发布到remote						

# maven插件命令								

-	maven-release-plugin							
	-	mvn release:clean						
	-	清理release操作是遗留下来的文件						
-	eclipse							
	-	mvn eclipse:eclipse						
		-	生成eclipse项目					
	-	mvn eclipse:clean						
		-	清除eclipse的一些系统设置					
-	idea							
	-	mvn idea:idea						

# 代码生成								

-	创建Maven的普通Java项目							
	-	mvn archetype:create						
		-	-DgroupId=packageName					
		-	-DartifactId=projectName					
-	创建Maven的Web项目							
	-	mvn archetype:create						
		-	-DgroupId=packageName					
		-	-DartifactId=webappName					
		-	-DarchetypeArtifactId=maven-archetype-webapp					
-	反向生成 maven 项目的骨架							
	-	mvn archetype:generate						
-	提问辅助式生成maven项目							
	-	mvn archetype:generate				



# web项目相关命令

1. 启动tomcat：mvn tomcat:run
2. 启动jetty：mvn jetty:run
3. 运行打包部署：mvn tomcat:deploy
4. 撤销部署：mvn tomcat:undeploy
5. 启动web应用：mvn tomcat:start
6. 停止web应用：mvn tomcat:stop
7. 重新部署：mvn tomcat:redeploy
8. 部署展开的war文件：mvn war:exploded tomcat:exploded



# 显示更多信息								

-	获取命令帮助							
	-	mvn help						
-	显示版本信息							
	-	mvn -version/-v						
-	看项目(父或子)的完全的pom结构							
	-	mvn help:effective-pom						
-	查看当前项目已被解析的依赖							
	-	mvn dependency:list						
-	显示详细错误							
	-	mvn -e						
-	想要查看完整的依赖踪迹，包含那些因为冲突或者其它原因而被拒绝引入的构件							
	-	mvn install -X						
-	打印出已解决依赖的列表							
	-	mvn dependency:resolve						
-	打印整个依赖树							
	-	mvn dependency:tree						
-	使用 help 插件的  describe 目标来输出 Maven Help 插件的信息:							
	-	mvn help:describe -Dplugin=help						
-	使用Help 插件输出完整的带有参数的目标列 :							
	-	mvn help:describe -Dplugin=help -Dfull						
-	获取单个目标的信息,设置  mojo 参数和  plugin 参数。此命令列出了Compiler 插件的compile 目标的所有信息 :							
	-	mvn help:describe -Dplugin=compiler -Dmojo=compile -Dfull						
-	列出所有 Maven Exec 插件可用的目标:							
	-	mvn help:describe -Dplugin=exec -Dfull						
-	看这个“有效的 (effective)”POM，它暴露了 Maven的默认设置 :							
	-	mvn help:effective-pom						

# 常见命令后边的参数								

-	-D 传入属性参数							
-	-P 使用pom中指定的配置							
-	-e 显示maven运行出错的信息							
-	-o 离线执行命令,即不去远程仓库更新包							
-	-X 显示maven允许的debug信息							
-	-U 强制去远程参考更新snapshot包							
-	例如							
	-	mvn install -Dmaven.test.skip=true -Poracle						
-	跳过测试属性							
	-	给任何目标添加Pmaven.test.skip=true						





# 未分类								

-	mvn resources:resources 绑定在resource处理阶段, 用来将src/main/resources下或者任何指定其他目录下的文件copy到输出目录中							
-	mvn resources:testResources 将test下的resources目录或者任何指定其他目录copy到test输出目录下



# 技巧									

-	设置通过Maven创建的工程的JDK版本-一劳永逸								
	-	[1]打开settings.xml文件							
	-	[2]找到profiles标签							
	-	[3]加入如下配置							
		```xml	<profile>						
			<id>jdk-1.7</id>						
				<activation>						
				<activeByDefault>true</activeByDefault>						
			<jdk>1.7</jdk>						
			/activation>						
			<properties>						
				<maven.compiler.source>1.7</maven.compiler.source>						
				<maven.compiler.target>1.7</maven.compiler.target>		  	<maven.compiler.compilerVersion>1.7</maven.compiler.compilerVersion>						
			</properties> 
		</profile>	
```

# 使用 MAVEN注意									

-	避免莫名其妙的错误								
	-	Maven安装路径尽量不要有中文和空格							
	-	环境变量中配置M2_HOME							
	
-	SNAPSHOT快照								
	
	-	不稳定版，更新迭代的很快，这只是其中的某个瞬间							
	
-	RELEASE分离								
	
	-	已经分离出来的模块，开发完成了，比较完美的，问题都解决了，测试都通过了，比较稳定的版本，正式版							
	
- 部署后空指针异常可能是jar包冲突								

- mvn配置文件先加载~/.m/setting.xml再加载conf/setting.xml								

-	mvn compile与mvn install、mvn deploy的关系								
	-	mvn compile，编译类文件							
	-	mvn install，包含mvn compile，mvn package，然后上传到本地仓库							
	-	mvn deploy, 包含mvn install,然后，上传到私服							
	
-	Maven与构建过程相关命令，必须进入pom.xml所在的目录								
	
​	例如：编译、测试、打包。。							

