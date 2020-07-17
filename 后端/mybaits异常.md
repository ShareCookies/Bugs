### 异常代码：The server time zone value 'ÖÐ¹ú±ê×¼Ê±¼ä' is unrecognized or represents more than one
>翻译：

>说明：

 * 场景1： 
    ```
    ```   
    原因：    
    ```
		出错的原因是mysql的时区值设置的不正确。
    ```
    解决方案：
     ```
		https://blog.csdn.net/hju22/article/details/88192989
		mysql默认的时区值system，即是美国失去，中国的时区要比美国晚8小时，需要采用+8:00的格式。
     ```
>附： 
- - -
- - -
### 异常代码：org.apache.ibatis.binding.BindingException: Parameter 'idList' not found. Available parameters are [collection, list]
>翻译：

>说明：

 * 场景1： 
    ```
    ```   
    原因：    
    ```
		Mybatis是按顺序传递参数的。
    ```
    解决方案：
     ```
		https://blog.csdn.net/qq_28379809/article/details/83342196
		方式1：
			xml中用list接收参数。
		方式2:
			加上@Param("")注解
     ```
>附： 
- - -
- - -
### 异常代码：org.apache.ibatis.ognl.NoSuchPropertyException
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
		https://blog.csdn.net/rocketeerLi/article/details/83349510
		我是对应属性缺失了get方法。
     ```
>附： 
- - -
- - -
### 异常代码：The content of element type "mapper" must match "(cache-ref|cache|resultMap*|parameterMap*|sql*| insert*|update*|delete*|select*)+"
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
		这个错误的意思是 你写的语句或者标签和mybatis的标准化配置不匹配。
		如果 检查之后还是没找到错误的话，重启一下ecplise,idea试试。
     ```
>附： 
- - -