### uni-app request:fail parameter `data`. Expected Object, String, ArrayBuffer, got Arr
>说明：
 * 场景1： 
    ```
		uni-app uni.request() post形式传array
    ```   
    原因1：    
    ```	
    ```
    解决方案：
     ```
		https://ask.dcloud.net.cn/question/76886 
        把data数组JSON.stringify转字符串，然后content-type设置为application/json 
     ```
>附： 
- - -