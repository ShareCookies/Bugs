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