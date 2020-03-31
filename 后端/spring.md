### 400

>说明：
 * 场景1： 
    ```
        请求响应为：    
        status: 400
        error: "Bad Request"
        exception: "org.springframework.web.bind.MissingServletRequestParameterException"
        message: "Required String parameter 'docId这是方法参数' is not present"
        path: "请求连接"	
    ```   
    原因1：    
    ```
        请求缺失参数
    ```
    解决方案：
     ```
        请求带上对应参数
     ```
 * 场景2：    
      ```
      ```
    原因2：    
     ```
     ```
    解决方案：
      ```
      ```   
>附： 
- - -
###  java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty


>说明：
 * 场景1： 
    ```
        https://blog.csdn.net/qq_33382113/article/details/78643373
    ```   
    原因1：    
    ```
        
    ```
    解决方案：
     ```
        
     ```
 * 场景2：    
      ```
      https://www.cnblogs.com/over140/archive/2013/04/10/3012077.html
      ```
    原因：    
     ```
     ```
    解决方案：
      ```
      ```   
 * 场景3：    
      ```
      用RestTemplete发起了https请求，报了这个异常。
      ```
    原因：    
     ```
     ```
    解决方案：
      ```
      使Spring RestTemplete支持Https安全请求：
      https://blog.csdn.net/weixin_33835103/article/details/86278376
      https://blog.csdn.net/justry_deng/article/details/82531306#commentBox
      ```         
>附： 
- - -
### 异常代码：No active profile set, falling back to default profiles: default
>翻译：

>说明：
 * 场景1： 
    ```
    以前debug启动的好好的，突然不行了
    ```   
    原因：    
    ```
    没找到原因。
    附：
        https://www.cnblogs.com/javawxid/p/10949511.html
        https://www.cnblogs.com/jpfss/p/10765636.html
    ```
    解决方案：
     ```
     清idea缓存，用dubug启动 又失败了。
     然后用rebel debug启动 哎成功了，在用debug启动 哎 也成功了。
     ```

>附： 
- - -
- - -
### 异常代码：NoSuchBeanDefinitionException: No qualifying bean of type [com.xxx.XxxMapper] found  
>翻译：
    bean未找到
>说明：
 * 场景1： 
    ```
    mapper类为找到
    ```   
    原因：    
    ```
    bean未找到。
    
    ```
    解决方案：
     ```
    注解定义在接口上，那么springIOC容器实际接管的是
    对应接口的具体实现类，或对应接口的代理类。
    
    mapper被接管的就是对应接口的代理类，那么很明显mapper对应的xml有问题，导致mapper代理类生成失败。
    xml文件要在resource下，且xml所在的包名（路径名）要和mapper类的包名一样。
    可参考思路：
        1.是所有的bean都没扫描到吗。
        2.确认对应的bean所在包别的bean有注入成功吗。
        如果是，那么bean所在的包是否扫到。
        
     ```

>附： 
- - -
### 异常代码：HikariPool-1 - Failed to validate connection ... Possibly consider using a shorter maxLifetime value.HikariPool-1 - Connection is not available, request timed out after *ms.
>翻译：
    连接验证失败，考虑使用一个更短的maxLifetime。连接无效，请求将在.ms后超时
>说明：
 * 场景1： 
    ```
		静默一段时间没有数据库操作就报该错误
    ```   
    原因：    
    ```
		Spring Boot 2 项目,使用 Spring Data JPA 管理数据库，默认使用 HikariCP 连接池经常出现了该警告。
		虽然程序从 HikariCP 连接池获取到了连接，但是连接不可用。
    ```
    解决方案：
     ```
		spring.datasource.hikari.connectionTimeout=60000
		spring.datasource.hikari.idleTimeout=60000
		# validationTimeout用于多久验证一次数据库连接池的连接是否有效（是否为null）的时间 (默认是5秒，最小不能小于250毫秒) https://segmentfault.com/a/1190000013081060
		spring.datasource.hikari.validationTimeout=3000
		spring.datasource.hikari.loginTimeout=5
		spring.datasource.hikari.maxLifetime=60000
		https://www.cnblogs.com/zhaojinxin/p/7753873.html
     ```

>附： 
- - -