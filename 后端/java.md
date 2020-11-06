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