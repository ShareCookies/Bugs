### 1. ... is java.lang.NoClassDefFoundError: ...

>说明：类未找到
 * 场景1： 
    ```
       使用Tika时提示：...Handler dispatch failed; nested exception is java.lang.NoClassDefFoundError: com/microsoft/schemas/office/visio/x2012/main/ConnectsType
    ```
    原因1：    
    ```
        因为tika用了新版，tika又用到了poi，maven项目中poi又被低版本poi覆盖了。
    ```
    解决方案：
     ```
        排除掉低版本poi
     ```
    
 * 附： 

    ​	类找不到异常通常就是依赖被低版本依赖覆盖导致的。
- - -

### 2. java.lang.IllegalArgumentException: Comparison method violates its general contract!  

>说明：比较方法违法通用规范
 * 场景1： 
    ```
       
    ```
    原因1：    
    ```
       集合的compare方法出现异常，要符合规范的实现compare方法，即考虑比较对象为为null情况。
       https://www.cnblogs.com/firstdream/p/7204067.html
    ```
    解决方案：
     ```
        if(o1 == null && o2 == null) {  
        	return 0;  
        }  
        if(o1 == null) {  
            return -1;  
        }  
        if(o2 == null) {  
            return 1;  
        }  
        也考虑下比较值
     ```
    
 * 附： 

- - -
### 3. ...java.io.InvalidClassException: ...SecurityContextImpl; local class incompatible: stream classdesc serialVersionUID = 510, local class serialVersionUID = 530

>说明：序列化与反序列化版本冲突
 * 场景1： 
    ```
     
    ```
    原因1：    
    ```
        序列化与反序列化版本冲突
    ```
    解决方案：
     ```
    1. 将相关的缓存redis清除即可解决
    	？因为这是security报的缓存冲突，security会把什么序列化信息存在redis然后在反序列化了
    2、查看版本冲突
    
        
     ```
    
 * 附： 

    ​	https://blog.csdn.net/m0_37352076/article/details/107580474
    
    ​	https://blog.csdn.net/YangX1aoLei/article/details/94885425
    
    ​	反序列化测试：https://blog.csdn.net/b1480521874/article/details/88841560?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_title~default-0.opensearchhbase&spm=1001.2101.3001.4242.1
- - -

- - -
### 4.  ？ NoClassDefFoundError
>翻译：类未找到

>说明：

 * 场景1： 
    ```
	maven分模块有依赖，但依赖了该模块的总模块引入不成功(不会自动引入分模块依赖)，为什么了？
    需要一个一个引入，才不会报类未找到.
    ？是因为这是第三方的包导致的不会自动引入吗，那如何判断第三方了，包名前缀是否相同吗
    ```
    原因：    
	```
			
	```
    解决方案：
     ```		
    思路：1. 包未引入 2. 包版本不对 3. 包版本冲突 4...
     ```
>附： 

- - -

- - -

### 5. 异常代码：文件流返回数据为空或长时间等待

>翻译：

>说明：

 * 场景1： 

   ```
   二进制传输响应流(文件流),请求头加上content-length，导致返回数据为空或长时间等待
   ```

   原因：    

   ```
   估计http的content-length与实际不一致导致了浏览器拒绝或一直等待文件的情况
   ```

   解决方案：

    ```
    	方式1. 正确设置content-length
    	方式2. 不要设置content-length，让其默认为-1
    ```

>附：
>
>Content-Length 作用：！！！
>
>https://blog.csdn.net/yy4545/article/details/107787463
>
>https://blog.csdn.net/stpeace/article/details/80217315?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-1&spm=1001.2101.3001.4242
>
>`http`的协议中`Content-Length`首部告诉浏览器报文中实体主体的大小。
>
>这个大小是包含了内容编码的：
>
>	比如对文件进行了`gzip`压缩，`Content-Length`就是压缩后的大小。
>
>除非使用了分块编码，否则`Content-Length`首部就是带有实体主体的报文必须使用的。
>
>使用`Content-Length`首部是为了能够检测出服务器崩溃而导致的报文截尾，并对共享持久连接的多个报文进行正确分段.

- - -