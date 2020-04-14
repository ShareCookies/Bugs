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
>附： 
- - -
### Webpack打包报"JavaScript heap out of memory"错误
>说明：
 * 场景1： 
    ```
    ```   
    原因1：    
    ```      
    ```
    解决方案：
     ```
         https://www.cnblogs.com/jianxuanbing/p/9331042.html
     ```
>附： 
- - -
### Computed property "XXX" was assigned to but it has no setter
>说明：
 * 场景1： 
    ```
		
    ```   
    原因1：    
    ```	
        v-model是vue中的双向绑定，但是在computed中只通过get获取参数值，没有set无法改变参数值
    ```
    解决方案：
     ```
        https://segmentfault.com/a/1190000018127192?utm_source=tag-newest
        1.在computed中添加get和set
        
        2.将v-model改成:value
     ```
>附： 
- - -