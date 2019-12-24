



## 使用说明：

chrome安装完成插件之后启用插件 

### 1，启用插件  

```sh
npm install -g whistle
```

安装插件地址：

（chrome插件商店）https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif

（github）https://github.com/FelisCatus/SwitchyOmega/releases

chrome下启用插件

chrome://extensions/

![1577177461692](C:\Users\yuqinzeng\AppData\Roaming\Typora\typora-user-images\1577177461692.png)

### 2，启动插件   w2 start

![1577178046686](C:\Users\yuqinzeng\AppData\Roaming\Typora\typora-user-images\1577178046686.png)



### 3，进入选项：

![1577178135601](C:\Users\yuqinzeng\AppData\Roaming\Typora\typora-user-images\1577178135601.png)



### 4，添加代理

![1577178739938](C:\Users\yuqinzeng\AppData\Roaming\Typora\typora-user-images\1577178739938.png)

![1577178764089](C:\Users\yuqinzeng\AppData\Roaming\Typora\typora-user-images\1577178764089.png)

### 5，配置代理

打开 配置

http://127.0.0.1:8899/

具体配置规则 ： http://wproxy.org/whistle/pattern.html

常见配置如下：

```
# 配置方案1
www.domain.com 127.0.0.1 

# 配置方案2 当你同时开了两个前端服务的时候就很好用啦
www.domain.com 127.0.0.1：81

#对于各种后端接口需要根据链接区分的情况  可以配置不同的链接路径对应不同的后端地址
http://www.domain.com/api1/  http://api.domain.com/api1/  
http://www.domain.com/api2/  http://{ip}/api1/
```



![1577179235417](C:\Users\yuqinzeng\AppData\Roaming\Typora\typora-user-images\1577179235417.png)



设置右上角的代理模式为 刚刚添加的代理 就可以进行前端测试了。

### 6切换查看请求日志

![1577179588717](C:\Users\yuqinzeng\AppData\Roaming\Typora\typora-user-images\1577179588717.png)

### 7设置正常访问其他网站

添加 auto switch

![1577179703994](C:\Users\yuqinzeng\AppData\Roaming\Typora\typora-user-images\1577179703994.png)

把需要代理的域名配置到上面 下面配置直接链接（注意代理生效优先级）

![1577179822777](C:\Users\yuqinzeng\AppData\Roaming\Typora\typora-user-images\1577179822777.png)



将代理模式设置为auto switch。

现在可以随便配置代理进行前后端联调啦 ！

