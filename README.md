# ProxyPool

## 安装

### 安装Python

至少Python3.5以上

### 安装Redis

安装好之后将Redis服务开启
pip install redis

### 配置代理池

```
cd proxypool
```

进入proxypool目录，修改settings.py文件

PASSWORD为Redis密码，如果为空，则设置为None

#### 安装依赖

```
pip3 install -r requirements.txt
```

#### 打开代理池和API

```
python3 scheduler.py
```

## 获取代理


利用requests获取方法如下

```python
import requests

PROXY_POOL_URL = 'http://localhost:5555/random'

def get_proxy():
    try:
        response = requests.get(PROXY_POOL_URL)
        if response.status_code == 200:
            return response.text
    except ConnectionError:
        return None
```
储存 db.py
获取 crawler.py getter.py
爬虫 utils.py
检测 tester.py
接口 api.py
调度 scheduler.py

examples/example.py是测试文件

## 食用方法
代理池运行后会在本机的5555端口开放接口
登录方式为：
    本机：
        localhost:5555
        127.0.0.1:5555
    同一局域网的异机：
        xxx.xxx.xxx.xxx:5555 //xxx.xxx.xxx.xxx为本机内网ip地址
目录分级:
    '/' 首页
    '/random' 获取代理接口
    '/count' 获取数据库剩余代理数量
