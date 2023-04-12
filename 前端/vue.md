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
         nodeJs打包时内存溢出
         打开一个cmd窗口
         运行setx NODE_OPTIONS --max_old_space_size=4096
         重启电脑
         附:
         node --max-nex-space-size=1024   // 单位为KB
         node --max-old-space-size=2000  // 单位为MB
         可以通过任务管理器，看node.js内存达到你设置的值后，会不会崩，就能确定是否生效了
         https://www.cnblogs.com/jianxuanbing/p/9331042.html
         https://blog.csdn.net/genius_yym/article/details/80854729?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.nonecase
     ```
>附： 版本不一样可能不生效 14.17.1
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
		例：
			computed:{
			  test:{
				get:function () {
				  return this.$store.state.activeName
				},
				set:function () {
				}
			  }
			}
     ```
>附： 

- - -
- - -
### Webpack打包缓存问题

>说明：
 * 场景1： 
    ```
		各种问题，清了缓存就行
    ```
    原因1：    
    ```	
    	
    ```
    解决方案：
     ```
       修改build里webpack.prod.conf.js文件中的output为output: {
    path: config.build.assetsRoot,
    filename: utils.assetsPath(‘js/[name].[hash].js’),
    chunkFilename: utils.assetsPath(‘js/[id].[hash].js’)
	}
	附：
	https://www.cnblogs.com/heyushuo/p/8543889.html
	https://blog.csdn.net/sinat_17775997/article/details/61924901
	https://blog.csdn.net/qq_37337830/article/details/81507246?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.control
	 ```
>附： 
>
>ng指明清理缓存：
>
>        server {
>            listen       6050;
>            server_name  localhost;
>    
>            location / {
>                error_page 405 =200 /index.html;
>                root   /data/work/frontend/ex2;
>                index  index.html index.htm;
>                if ($request_filename ~* .*\.(?:htm|html)$)
>                {
>                    add_header Cache-Control "private, no-store, no-cache, must-revalidate, proxy-revalidate";
>                }
>            
>            }
>            ...
>        }

- - -
- - -
### element输入框等组件无法进行输入
>说明：
 * 场景1： 
    ```
		
    ```
    原因1：    
    ```	
        prop接收的对象(例form{}),并v-model到el-input上。
        然后对象引用变了，form指向别的，那么此时el-input就无法输入了。
    ```
    解决方案：
     ```
       
     ```
>附： 

- - -