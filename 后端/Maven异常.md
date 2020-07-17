### 异常代码：Failed to deploy ...with status code 401
>翻译：

>说明：

 * 场景1： 
    ```
    ```   
    原因：    
    ```
        这是权限不够，无法发布包到私服。
    ```
    解决方案：
     ```
     	maven配置账号密码：
     		例：maven的setting.xml配置中添加以下代码：
     			<server>
     			  <id>154-nexus</id>
     			  <username>admin</username>
     			  <password>admin123</password>
     			</server>
     			
     			<server>
     			  <id>snapshots</id>
     			  <username>admin</username>
     			  <password>admin123</password>
     			</server>
     			<server>
     			  <id>release</id>
     			  <username>admin</username>
     			  <password>admin123</password>
     			</server>
     ```
>附： 
- - -
### 异常代码：Failed to execute goal org.apache.maven.plugins:maven-install-plugin:2.4:install (default-cli) on project core:  The packaging for this project did not assign a file to the build artifact -> [Help 1]
>翻译：

>说明：

 * 场景1： 
    ```
    ```   
    原因：    
    ```
        
    ```
    解决方案：
     ```
     	http://tieba.baidu.com/p/4810060893
        		点击Plugins里的install:install
        		打包点击Lifecycle里的install
     ```
>附： 
- - -
- - -
### maven添加插件不成功
>翻译：

>说明：

 * 场景1： 
    ```
    ```   
    原因：    
    ```
        
    ```
    解决方案：
     ```
     	https://blog.csdn.net/qq_41376740/article/details/81030611
     ```
>附： 
- - -
- - -
### maven依赖书写正确，但实际实际引入的却是另一个依赖
>翻译：

>说明：

 * 场景1： 
    ```
		项目引入的是zjj但实际引入的确是zdj，清缓存等操作均无效。
	    <dependency>
            <groupId>com.zjj.egov</groupId>
            <artifactId>doc-business</artifactId>
            <version>1.0.0-SNAPSHOT</version>
        </dependency>
		<dependency>
            <groupId>com.zdj.egov</groupId>
            <artifactId>doc-business</artifactId>
            <version>1.0.0-SNAPSHOT</version>
        </dependency>
		
    ```   
    原因：    
    ```
        因为一个request的依赖已经在其依赖包中引入了zdj，导致当前项目引入的zjj无法生效。
    ```
    解决方案：
     ```
     	屏蔽request。
		
		解决方案2：
			https://blog.csdn.net/Petershusheng/article/details/87885887?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase
     ```
>附： 
- - -
- - -
### Failed to execute goal on project zjgy-oa-hsf: Could not resolve dependencies for project com.rongji.egov:zjgy-oa-hsf:jar:0.0.1-SNAPSHOT: The following artifacts could not be resolved: com.alibaba.middleware:sdk:jar:999-not-exist-SNAPSHOT, com.taobao.pandora:taobao-hsf.sar:jar:dev-SNAPSHOT: Failure to find com.alibaba.middleware:sdk:jar:999-not-exist-SNAPSHOT in http://ip:端口/repository/public/ was cached in the local repository, resolution will not be reattempted until the update interval of 154-nexus has elapsed or updates are forced -> [Help 1]
>翻译：

>说明：

 * 场景1： 
    ```
		使用clean package打包失败
		
    ```   
    原因：    
    ```
        
    ```
    解决方案：
     ```		
		1.：确保（快照）包是否在私服存在
			
			附：
			1.上传SNAPSHOT类型的JAR文件到nexus中：
				https://blog.csdn.net/weixin_33873846/article/details/94046683?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-5.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-5.nonecase
				https://blog.csdn.net/zazzh007/article/details/101272511?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.nonecase
				
				附:
					mvn deploy:deploy-file -DgroupId=com.alibaba.middleware -DartifactId=sdk -Dversion=999-not-exist-SNAPSHOT -Dpackaging=jar -Dfile=D:\programming\versionControl\apache-maven-3.6.1-bin\repository\com\alibaba\middleware\sdk\999-not-exist-SNAPSHOT\sdk-999-not-exist-SNAPSHOT.jar -Durl=http://admin:admin123@ip:端口/repository/snapshots/ -DrepositoryId=snapshots
				
			2.快照包在nexus可是化界面中类似个文件夹，然后文件夹下面有快照包
			3.有包，确认下能否下载到本地库：
				https://blog.csdn.net/java_66666/article/details/90750107
		2.：错误中提示到：resolution will not be reattempted until the update interval of 154-nexus has elapsed or updates are forced
			那就强制更新打包方式：
				mvn clean install -U
			https://blog.csdn.net/u013066244/article/details/91986308
     ```
>附： 
- - -