js的模块加载

     commonJS

            这里的CommonJS规范指的是CommonJS Modules/1.0规范。commonJS是一个比较偏向于服务端的规范，
         每个commonJS的模块就是一个js脚本文件。require第一次加载文件就会执行脚本并生成一个exports对象。
         以后在需要用到这个模块的时候可以直接在exports缓存取值。
            因为commonJS是同步加载模块，对于服务器来说加载模块的时间就是硬盘读取文件的时间，但是对于浏览器就不一样了，
         浏览器涉及到了网速代理等原因，如果时间过长浏览器就会出现”假死“的状态。所以在浏览器不适合使用commonJS规范
         
         
     AMD
            AMD是”Asynchronous Module Definition”的缩写，即”异步模块定义”。amd才用异步加载模块，
         模块的加载不影响dom构建，css渲染，然而，模块内部的加载时同步的加载完模块立即执行回调，
         AMD也采用require命令加载模块，但不同于commonJS，他要求两个参数：
           1、 require([module], callback)
          第一个参数是一个数组需要加载的模块，第二个参数是一个回调函数，加载完模块立即回调：
           2、exports.add = function(a, b){
                return a + b 
              }
              require(['math'],()=>{
                math.add(1,2)
              })
     
     
     CMD
        CMD推荐就近加载，但需要的是时候在加载，可以吧你依赖的模块写到任何位置：
        1、 define(factory)
            factory为函数的时候，表示是模块的构造方法。执行构造方法，可以得到模块向外提供的接口。factory默认传入三个参数：
        require、exoprts和module
        
     // CMD
     define(function(require, exports, module) {
       var a = require('./a');
       a.doSomething();
       var b = require('./b');
       b.doSomething();
     })
     // AMD
     define(['a', 'b'], function(a, b) {
       a.doSomething();
       b.doSomething();
     })
     
     AMD在使用前必须提前引入而CMD在使用的时候在引入
     
     






