### ... is java.lang.NoClassDefFoundError: ...

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

### java.lang.IllegalArgumentException: Comparison method violates its general contract!  

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

    

