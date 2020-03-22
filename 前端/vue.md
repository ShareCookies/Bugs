### Property "visible" must be accessed with "$data.visible" because properties starting with "$" or "_" are not proxied in the Vue instance to prevent conflicts with Vue internals.
>说明：
 * 场景1： 
    ```
       vue框架，浏览器的console中报了这个错误。
    ```   
    原因1：    
    ```
       变量无法找到。
    ```
    解决方案：
     ```
         1.
         变量未在data中return，你就使用了它，所以报了这个错。
         2.
         变量定义了，但还是报错，那么可能this指向出错了。
         例：
         .forEach(()=>{visible
         	this.变量;
         	//this指向被改变成当前函数，所以无法找到vue下的属性
         });
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