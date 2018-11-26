## Axios中的请求
### 介绍
> axios 是一个基于Promise 用于浏览器和 nodejs 的 HTTP 客户端    

特征如下：
- 从浏览器中创建 XMLHttpRequest
- 从 node.js 发出 http 请求
- 支持 Promise API
- 拦截请求和响应
- 转换请求和响应数据
- 取消请求
- 自动转换JSON数据
- 客户端支持防止 CSRF/XSRF

### 安装方法：
1. npm安装axios
```npm
npm install axios
```
2. 引入加载（./src/components/HelloWorld.vue）
```vue
import axios from 'axios'
```
3. 将axios全局挂载到Vue原型上
```vue
Vue.prototype.$http = axios
```

### Axios中的get请求
以cnode社区为例
```javascript
methods: {
  getData(){
    //params:指定参数。page和limit为官方的api
    this.$http.get('https://cnodejs.org/api/v1/topics', {
      params: {
        page: 1,
        limit: 10
      }
    })
      .then((res) => {
        this.items = res.data.data
        console.log(res)
      })
      .catch(function (err) {
        console.log(err)
      })
  }
}
```
#### 2种传递数据的形式
1. params传递:url后面接params对象。
    ```javascript
    getData(){
      //params:指定参数。page和limit为官方的api
      this.$http.get('https://cnodejs.org/api/v1/topics', {
        params: {
          page: 1,
          limit: 10
        }
      })
    }
    ```
2. url链接加参数
    ```javascript
    getData(){
      //params:指定参数。page和limit为官方的api
      this.$http.get('https://cnodejs.org/api/v1/topics?page=1&limit=10')
    }
    ```
### Axios中的post请求
#### post传递数据2种格式
1. form-data
2. x-www-form-urlencoded      
#### qs插件
##### 在axios中，post请求接收的参数必须是form-data，为解决这一问题可以使用qs插件的qs.stringify方法;
##### 安装方法：
```shell
npm install qs
```
##### **demo**
```javascript
postData(){
    //params:指定参数。page和limit为官方的api
    this.$http.post(url, qs.stringify({
        page: 1,
        limit: 10
    }))
      .then((res) => {
        this.items = res.data.data
        console.log(res)
      })
      .catch(function (err) {
        console.log(err)
      })
  }
```


