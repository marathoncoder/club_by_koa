## club_by_koa

- bin/start：启动脚本
- config/：存放配置文件的目录，default.scheme.js 为 koa-scheme 所用
- lib/：存放一般代码文件的目录
- models/：存放模型文件的目录
- routes/：存放路由文件的目录
- theme/：存放主题模版文件的目录
- test/：存放测试文件的目录

---

- koa-bodyparser：请求体解析中间件，相当于 express 中的 body-parser
- koa-flash：相当于 connect-flash
- koa-generic-session：通用的 session 中间件，可结合 mongodb、redis等使用
- koa-generic-session-mongo：结合 koa-generic-session，将 session 存储到 mongodb 的中间件
- koa-static-cache：静态文件缓存中间件
- merge-descriptors：合并两个对象的工具模块
- mongoose：mongodb 驱动模块
- validator：参数验证工具模块

中间件的加载顺序十分重要，如上面的 errorhandler 中间件需要放到最上面，这样才能捕获下游抛出的错误。flash 中间件需要放到 session 中间件之后，因为 flash 功能是基于 session 实现的。routerCache 需要放到 router 前面，而 scheme 需要放到 routerCache 前面。 gzip 压缩中间件需要放到 routerCache 之后，这样 routerCache 缓存的就是 gzip 压缩后的内容了，大大减少了内存消耗量。
