# jy-request是什么
* jy-request是一个uni-app网络缓存库

# jy-request特性
* 支持数据缓存

# 使用
- ## 安装
  ```bash
  npm i jy-request
  ```
- ## 初始化
  ```js
  import JyReq from '@/components/jy-image/libs/jy-request'
  export const req = new JyReq({
      host: 'host', //见本文档props列表
  })
  ```
- ## 请求并缓存
  ```js
  req.get('api').back(resp=>{}).exec()
  ```
- ## 传递数据和请求头
  ```js
  req.post('api').header({}).send({}).back(resp=>{}).exec()
  ```
- ## 额外的缓存  
  由于默认只对未传参的请求进行缓存，如果需要缓存带参请求则需要调用cache()方法或者通过cacheList属性进行设置
  ```js
  req.get('api').back(resp=>{}).cache().exec() 
  //也可以通过cacheList属性来实现带参请求的缓存
  req.opt({
      cacheList: ['api1', 'api2']
  })
  ```
- ## Promise方式
  ```js
  async fetch() {
      const {code, msg} = await req.post('api').send({}).cache().exec()
  }
  ```
- ## Method列表
  - 请求方式  
  `post('')` `get('')` `put('')` 等  
  - 请求数据  
  `send({})`
  - 请求头  
  `header({})`
  - 回调  
  `back(resp=>{})`
  - 指定缓存  
  `cache()`
  - 执行请求  
  `exec()`
  - 取消所有请求  
  `abort()`
  - 设置全局props  
  `opt({})`
  - 设置本次请求props并执行请求  
  `exec({})`  

- ## Props列表
  - `host:`  
  - `header:`  
  - `timeout:`  
  - `dataType:`  
  - `responseType:`  
  - `sslVerify:`  
  - `apiList: []`  
  设置额外缓存的api, 同cache()
  - `interceptor: (resp)=>{}`  
  拦截器
  - `offline: Boolean`  
  仅显示离线数据，测试缓存使用
  - `verbose: Boolean`  
  是否显示打印信息

