### 异常代码：git 无法push远程仓库 Note about fast-forwards 问题解决
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
     方式1：待测 https://blog.csdn.net/weixin_42596434/article/details/88759295
     方式2：丢弃重置到同一个commit，然后先拉，在重新提交，在推送
     ```
>附： 

- - -
### 异常代码：It looks like git-am is in progress. Cannot rebase.
>翻译：

>说明：

 * 场景1： 
    ```
    sourceTree放弃变基失败提示该异常
    ```
    原因：    
    ```
    
    ```
    解决方案：
     ```
    git pull 的时候出现这样的错误。
    
    It looks like git-am is in progress. Cannot rebase.
    用如下方法解决：rm -rf .git/rebase-apply
    在工程的根目录执行。
     ```
>附： 

- - -

# git 变基报错git-am is in progress

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
     https://blog.csdn.net/zhenyu5211314/article/details/78357139
        报错信息：
        It looks like git-am is in progress. Cannot rebase.
    
        解决办法：
        命令行执行 rm -rf .git/rebase-apply
        删除项目.git/rebase-apply 文件夹，.git文件夹默认为隐藏
     ```
>附： 

- - -

