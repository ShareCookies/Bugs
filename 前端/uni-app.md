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

### [JSHINT] 进程已崩溃(或闪屏退出)
>说明：
 * 场景1： 
    ```
	运行到浏览器提示：
    	### [JSHINT] 12:55:21.001 进程已崩溃
    	或直接闪屏退出
    ```
    原因1：    
    ```	
    原因：node运行异常造成的额。
	
    诊断方式：
    1.进入HBuilderX所在目录，进入plugins/node/, 点击下node程序，看下node能否正常运行
    (一闪而过就是不行)
    或2.点击菜单【帮助】【查看运行日志】，看下日志中，提示什么错误。
    
    ```
    解决方案：
     ```
    拷贝个可以的nodejs.exe替换掉这个文件。
     ```
>附： 

- - -

