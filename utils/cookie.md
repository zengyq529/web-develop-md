# cookie读写 (提高效率 能copy的坚决不写)



# cookie属性

name: cookie名称

value: cookie值

domain: 即可访问此cookie的域名(不同级有不同限制)

path: 可访问此cookie的页面路径 (对应链接路径，如果设置路径则对应路径才可以访问到对应的cookie，默认设置 / 根路径)

expires/Max-Age: cookie超时时间, 默认为Session

Size: cookie大小

http: 即httponly属性, true时只有http请求头会带有此信息, 而不能通过document.cookie来访问 （服务端SetCookie设置）

secure: 设置是否只可通过https来传递此条cookie（服务端SetCookie设置）



## js-cookie

npm 地址： https://www.npmjs.com/package/js-cookie

<script src="https://cdn.jsdelivr.net/npm/js-cookie@2/src/js.cookie.min.js"></script>
```shell
npm add js-cookie --save  //执行需要放到使用save ， 打包依赖放 dev。
yarn add js-cookie --save
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

```js
/**
 *
 * @param name
 * @param value
 * @param time:day 传0 或者不传 则设置为session格式cookie，关闭浏览器消失。
 * @param path = '/a/b/'   /a/b/ 对应链接目录。如果设置path则只有链接目录对应才可以访问到cookie,默认为根路径（站点都可访问）
 * @param domain = 'a.com'
 */
function setCookie(name, value, time = 0,{path = '',domain = ''} = {}) {
    let timeStr = ''
    if (time) {
        let now = new Date();
        now.setTime(now.getTime() + time * 24 * 60 * 60 * 1000);
        timeStr = 'expires=' + now.toGMTString() + ';'
    }
    let domainStr =  'domain=' + (domain || document.domain.split('.').slice(-2).join('.')) + ';'; //设置一级域名
    let pathStr =  'path='+ (path || '/') +';'
    document.cookie = `${name}=${encodeURIComponent(value)};${pathStr}${timeStr}${domainStr}`
}

```

#### getCookie

```js
/**
 * 获取cookie
 * @param name
 * @return {string}
 */
function getCookie(name) {
    let reg=new RegExp("(^| )"+name+"=([^;]*)(;|$)");
    let match = document.cookie.match(reg);
    return match?decodeURIComponent(match[2]):'';
}
```

#### removeCookie

```js
//注释 如果设置cookie设置了 domain 和 path ，删除cookie需要删除对应的cookie 那么删除cookie也需要设置path ,domain
function removeCookie(name, {path = '',domain = ''} = {}) {
    setCookie(name,'',-1,{path,domain})
}
```



### 非ES6 写法

#### setCookie

```js
/**
 *
 * @param name
 * @param value
 * @param time:day 传0 或者不传 则设置为session格式cookie，关闭浏览器消失。
 * @param path = '/a/b/'   /a/b/ 对应链接目录。如果设置path则只有链接目录对应才可以访问到cookie,默认为根路径（站点都可访问）
 * @param domain = 'a.com'
 */
function setCookie(name, value, time, param) {
    let timeStr = ''
    let domain = param && param.domain ? param.domain : '';
    let path = param && param.path ? param.path : '';
    if (time) {
        let now = new Date();
        now.setTime(now.getTime() + time * 24 * 60 * 60 * 1000);
        timeStr = 'expires=' + now.toGMTString() + ';'
    }
    let domainStr = 'domain=' + (domain || document.domain.split('.').slice(-2).join('.')) + ';'; //设置一级域名
    let pathStr = 'path=' + (path || '/') + ';'
    document.cookie = name + '=' + encodeURIComponent(value) + ';' + pathStr +timeStr + domainStr;
}
```





#### removeCookie

```js
function removeCookie(name, param) {
    setCookie(name, '', -1, {path:param?param.path:'', domain:param?param.domain:''})
}
```





## 小程序 cookie 读写

#### setCookie

https://developers.weixin.qq.com/miniprogram/dev/api/storage/wx.setStorageSync.html

```js
//value: 需要存储的内容。只支持原生类型、Date、及能够通过`JSON.stringify`序列化的对象。
wx.setStorageSync('name',  value);
```

#### getCookie

```js
wx.getStorageSync('name');
```



#### clearCookie

```js
wx.setStorageSync('name','');
```



## react-native cookie 读写



### react-native-cookie

https://www.npmjs.com/package/react-native-cookie

```shell
# install library from npm
npm install react-native-cookie --save
# link native code
react-native link react-native-cookie

```

```js
import Cookie from 'react-native-cookie';

// set cookie 'foo=bar' for 'http://bing.com/'
Cookie.set('http://bing.com/', 'foo', 'bar').then(() => console.log('success'));

// set cookie 'foo=bar' for 'http://bing.com/' with options:
Cookie.set('http://bing.com/', 'foo', 'bar', {
    path: 'ditu',
    domain: 'cn.bing.com'
}).then(() => console.log('success'));

```



#### 
