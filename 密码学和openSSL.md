### 密码学
#### 算法分类
* 对称加密（一把钥匙）
* 费对称加密（两把钥匙）
* Hash算法（没有钥匙）
### 对称加密常见算法
* DES
* RC6
### 非对称加密常见算法
* RSA
* DSA(数字签名较优)
* ECC(移动设备用)
### Hash算法
* MD5
* SHA
* HMAC-MD5
### 场景
```
key -> key -> key
aa(key) -> xxx -> aa(key)

public -> public -> public
key(private) -> xxx -> key(public)
aa(key) -> xxx -> aa(key)

第一次交换密钥使用非对称加密，双方通讯的内容是对称加密，原因是：对称加密的执行效率比非对称加密的要高。
业务场景比较严谨，比如https和支付宝，采用两次非对称加密，双方都有自己的一把钥匙，在通讯的时候都是用自己的数字指纹，确认双方都是对方发出的。
```
```
例子：邮件，下载。
对于大文件，比如5g文件直接进行非对称加密，效率低，一般采用hash算法和非对称加密结合的方式。

甲方，首先对于5G文件hash算法加密得到一个定长（45位）的字符串，再对定长字符串进行非对称的私钥签名。
乙方，会请求公钥对已经签名好的hash做一次验证，是否被篡改。
非篡改，在乙方的电脑上对这个5G文件进行hash,再进行对比，只要这两个hash完全一样，就说明这个文件未被篡改。


```
### openSSL常用场景是生成证书
CA是第三方比较权威的机构，对公钥进行加密（考虑到公钥传输不安全），需要生成三分证书（CA证书，server证书，client证书），步骤是：首先创建私钥，创建证书请求，自签署证书。

### 代码示例
```
const https = require('https');
const fs = require('fs');

const options = {
  key: fs.readFileSync('./server-key.pem')
  cert: fs.readFileSync('./server-cert.pem')
}

https.createServer(options, (req,res) => {
  res.writeHead(200)
  res.end('hello world\n')
}).listen(8000)

命令行输入node index.js，启8000服务，访问localhost:8000
```


