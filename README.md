js的模块加载

     commonJS

            这里的CommonJS规范指的是CommonJS Modules/1.0规范。commonJS是一个比较偏向于服务端的规范，
         每个commonJS的模块就是一个js脚本文件。require第一次加载文件就会执行脚本并生成一个exports对象。
         以后在需要用到这个模块的时候可以直接在exports缓存取值。
            因为commonJS是同步加载模块，对于服务器来说加载模块的时间就是硬盘读取文件的时间，但是对于浏览器就不一样了，
         浏览器涉及到了网速代理等原因，如果时间过长浏览器就会出现”假死“的状态。所以在浏览器不适合使用commonJS规范

