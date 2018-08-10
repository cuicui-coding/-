# -
区分易混淆的知识点

### polyfill和shim区别
```
shim是利用现有的API实现新的API，例如JQ的$.ajax封装了W3C的xmlhttprequest和IE的xhr请求；
shim是一个库,它将一个新的API引入到一个旧的环境中,而且仅靠旧环境中已有的手段实现；

polyfill就是一种模仿未来API并为旧浏览器提供后备功能的“衬垫”
polyfill特指实现出的API是遵循标准的，例如在旧浏览器中运用仅有的手段实现新浏览器的标准API；
polyfill就是一个用在浏览器API上的shim.我们通常的做法是先检查当前浏览器是否支持某个API,如果不支持的话就加载对应的polyfill.然后新旧浏览器就都可以使用这个API了；

```
### 浏览器，v8引擎，JavaScript，ECMAScript到底是什么关系？
```
JavaScript由ECMAScript,dom,bom三部分组成，浏览器是运行脚本的一个环境。
问题一：说JavaScript不支持es6是说它没有实现es6规定的方法吗
问题二：es6到底是一门语言还是只是一个标准
问题三：浏览器不支持es6的某个方法，是因为javascript不支持es6吗
问题四：javascript是如何升级的，比如说他把es6的方法全部实现了，那浏览器是如何支持JavaScript的
问题五：v8是解析JavaScript的引擎，那JavaScript不支持es6，为什么chrome支持es6

1、javascript没有什么支不支持语法标准的说法。应该说javascript引擎是否支持es6比如chrome55的v8支持大部分es6语法。

2、ECMAScript6只是个标准指当前javascript引擎对原生js代码可用的语法及内置库。

3、浏览器不支持es6的某个方法，是因为javascript引擎还没有实现这个方法。

4、javascript标准升级靠浏览器更新，浏览器更新了js引擎也就更新了。

5、见1
浏览器组成可分两部分：Shell+内核。浏览器内核又可以分成两部分：渲染引擎和JS引擎。
```
