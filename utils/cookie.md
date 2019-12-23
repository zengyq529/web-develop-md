# cookie读写 



# cookie属性

name: cookie名称

value: cookie值

domain: 即可访问此cookie的域名(不同级有不同限制)

path: 可访问此cookie的页面路径

expires/Max-Age: cookie超时时间, 默认为Session

Size: cookie大小

http: 即httponly属性, true时只有http请求头会带有此信息, 而不能通过document.cookie来访问

secure: 设置是否只可通过https来传递此条cookie



## js-cookie

npm 地址： https://www.npmjs.com/package/js-cookie

```shell
npm install js-cookie --save
```

```js
import Cookies from 'js-cookie'

Cookies.set('name', 'value', { path: '',expires: 7 ,domain: '.domain.com' }); 
//expires : day
Cookies.get('name',{{ domain: 'domain.com' }}); // => 'value'
Cookies.remove('name', { path: '',domain: '.domain.com' });

```



## js cookie 读写

### ES6 写法

#### setCookie



#### getCookie



#### clearCookie





### 非ES6 写法

#### setCookie



#### getCookie



#### clearCookie





## 小程序 cookie 读写

#### setCookie



#### getCookie



#### clearCookie

## react-native cookie 读写



#### setCookie



#### getCookie



#### clearCookie