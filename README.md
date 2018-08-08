# -
区分易混淆的知识点

### polyfill是shim的一种
```
shim是利用现有的API实现新的API，例如JQ的$.ajax封装了W3C的xmlhttprequest和IE的xhr请求；
shim是一个库,它将一个新的API引入到一个旧的环境中,而且仅靠旧环境中已有的手段实现；

polyfill特指实现出的API是遵循标准的，例如在旧浏览器中运用仅有的手段实现新浏览器的标准API；
polyfill就是一个用在浏览器API上的shim.我们通常的做法是先检查当前浏览器是否支持某个API,如果不支持的话就加载对应的polyfill.然后新旧浏览器就都可以使用这个API了；
```
