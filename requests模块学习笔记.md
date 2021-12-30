# Request模块的学习笔记
## res.text与res.content的不同
**r.text 根据r.encoding的值来解码，默认的值是'ISO-8859-1'**

> r.encoding = 'utf-8'
> 
> r.text

**r.content是二进制数据，可以通过decode()函数解码(默认utf-8)：**
> r.content.decode()

## Requests自带的JSON解码器
> r.json()

## 发送带参数的get请求
1. 直接在url字符串中加入参数

   > url = 'https://www.baidu.com/s?wd=python'
   >
   > requests.get(url)

2. 使用params参数带入

   > url = 'https://www.baidu.com/'
   >
   > data = {'wd':'python'}
   >
   > request.get(url,params=data)

## 使用cookies
1. 在headers参数中添加cookies字典
   
   > headers = {'cookie': 'asdfasdfasdfasdf'}
   >
   > requests.get(url,headers)

2. 利用cookies参数
   
   > cookies = {}
   >
   > requests.get(url,cookies=cookies)

## 使用代理
> proxies = {'http':'http://218.95.81.51:9000'}
> 
> requests = get(url,proxies=proxies)

## 使用verify参数忽略CA证书
> requests.get(url,verify=False)

## 使用session保持cookies
> ses = requests.sessions(url, headers)
> 
> res = ses.get(url,headers)
> 
> res = ses.post(url, data)