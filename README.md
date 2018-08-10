# -
区分易混淆的知识点

### polyfill和shim区别
```
shim
一个shim是一个库，它将一系列新的、标准的API引入到一个旧的环境中，而且仅靠旧环境中已有的手段实现旧版兼容。
例如我们经常听到的es5-shim，它是在es3的引擎上实现了es5的特性，但用到的都是es3的技术，而且在Node.js上和在浏览器上有完全相同的表现，所以它是shim。

polyfill
polyfill是解决跨浏览器API兼容性问题的shim，相当于一段代码。
我们通常的做法是先检查当前浏览器是否支持某个API，如果不支持的话就加载对应的polyfill，然后新旧浏览器就都可以使用这个API了。


shim是利用现有的API实现新的API，例如JQ的$.ajax封装了W3C的xmlhttprequest和IE的xhr请求；
shim是一个库,它将一个新的API引入到一个旧的环境中,而且仅靠旧环境中已有的手段实现；

polyfill就是一种模仿未来API并为旧浏览器提供后备功能的“衬垫”
polyfill特指实现出的API是遵循标准的，例如在旧浏览器中运用仅有的手段实现新浏览器的标准API；
polyfill就是一个用在浏览器API上的shim.我们通常的做法是先检查当前浏览器是否支持某个API,如果不支持的话就加载对应的polyfill.然后新旧浏览器就都可以使用这个API了；

```
### babel-polyfill的作用
```
解释一：

Babel默认只转换新的JavaScript句法（syntax），而不转换新的API，比如Iterator、Generator、Set、Maps、Proxy、Reflect、Symbol、Promise等全局对象，以及一些定义在全局对象上的方法（比如Object.assign）都不会转码。

举例来说，ES6在Array对象上新增了Array.from方法。Babel就不会转码这个方法。如果想让这个方法运行，必须使用babel-polyfill，为当前环境提供一个垫片。



解释二：

提示：polyfill指的是“用于实现浏览器不支持原生功能的代码”，比如，现代浏览器应该支持fetch函数，对于不支持的浏览器，网页中引入对应fetch的polyfill后，这个polyfill就给全局的window对象上增加一个fetch函数，让这个网页中的JavaScript可以直接使用fetch函数了，就好像浏览器本来就支持fetch一样。在这个链接上 https://github.com/github/fetch 可以找到fetch polyfill的一个实现。
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
